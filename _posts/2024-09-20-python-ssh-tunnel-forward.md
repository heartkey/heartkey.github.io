---
layout: single
title: "Python: SSH Tunneling"
writer: CCBB
published: True
categories:
  - dev 
  - back-end
tags:
  - python ssh tunneling mssql db
toc: true
toc_label: "My Table of Contents"
toc_sticky: true
toc_icon: "cog"
# classes: wide

date: 2024-09-20 13:22:15
last_modified_at : 2024-09-20 14:34:44
excerpt: "SSH Tunneling 의 이해, 활용 예제 코드(DB 연결)"
header:
  # teaser: /assets/images/java-logo.png
  # overlay_image: /assets/images/unsplash-gallery-image-1.jpg
  # overlay_filter: 0.5 # same as adding an opacity of 0.5 to a black background
  # overlay_filter: linear-gradient(rgba(255, 0, 0, 0.5), rgba(0, 255, 255, 0.5))
  
  # overlay_color: "#333"
  # caption: "Photo credit: [**Unsplash**](https://unsplash.com)"
  # actions:
  #   - label: "More Info"
  #     url: "https://unsplash.com"
# date: 2024-07-19 13:22:15
# last_modified_at : 2024-07-11 14:34:44
---
---

<!-- # Python SSH Tunneling -->

SSH 터널링은 SSH(Secure Shell) 프로토콜을 사용하여 네트워크 연결을 암호화하여 보호하는 방법이다.  
이를 통해 로컬 또는 원격 네트워크의 특정 포트를 다른 호스트의 포트로 안전하게 포워딩할 수 있다.  
SSH 포트 포워딩에는 세 가지 유형이 있다: 로컬, 원격, 그리고 동적 포트 포워딩.

## 로컬 포트 포워딩 (Local Port Forwarding)
로컬 포트 포워딩은 로컬 시스템의 특정 포트를 원격 서버의 포트로 전달.  
예를 들어, 로컬 시스템의 localhost:8080 포트를 원격 서버의 example.com:80으로 전달할 수 있다.

```
ssh -L 8080:example.com:80 user@remote_host
```
이 명령어는 로컬 호스트의 8080 포트를 원격 호스트 remote_host를 통해 example.com:80으로 전달.   
이를 통해 로컬 브라우저에서 http://localhost:8080에 접속하면 example.com:80에 접속한 것과 동일하다.  

## 원격 포트 포워딩 (Remote Port Forwarding)
원격 포트 포워딩은 원격 서버의 특정 포트를 로컬 시스템의 포트로 전달.   
이를 통해 원격 서버의 클라이언트가 로컬 시스템의 서비스를 이용할 수 있다.

```
ssh -R 8080:localhost:80 user@remote_host
```
이 명령어는 원격 호스트 remote_host의 8080 포트를 로컬 호스트의 80 포트로 전달.   
원격 호스트에서 localhost:8080으로 접속하면 로컬 호스트의 80 포트로 연결된다.

## 동적 포트 포워딩 (Dynamic Port Forwarding)
동적 포트 포워딩은 SOCKS 프록시를 설정하여 클라이언트의 네트워크 트래픽을 포워딩한다.  
이를 통해 특정 포트에 대한 프록시를 설정하고 SSH 클라이언트를 사용하여 다른 네트워크 서비스에 액세스할 수 있다.

```
ssh -D 8080 user@remote_host
```
이 명령어는 로컬 호스트의 8080 포트를 SOCKS 프록시 서버로 설정.  
클라이언트 애플리케이션(예: 웹 브라우저)을 설정하여 이 SOCKS 프록시를 사용하도록 하면 모든 트래픽이 SSH 터널을 통해 전달된다.  

추가 옵션
-N: 원격 명령을 실행하지 않고 포트 포워딩만 수행할 때 사용한다.  
-f: 백그라운드에서 실행하기 위해 사용한다.  
```
ssh -N -L 8080:example.com:80 user@remote_host
```
SSH 포트 포워딩은 원격 자원에 대한 안전한 액세스를 제공하며, 방화벽을 우회하거나 제한된 네트워크에서 작업할 때 유용하다. 
이를 통해 데이터 전송의 보안을 강화하고, 네트워크를 더욱 유연하게 사용할 수 있다.


## Python SSH Tunneling 사용한 DB 연결

### 연결 테스트를 위한 네트워크 구성
A 서버의 인바운드는 22번 포트만 열려 있다 
B 서버의 인바운드는 mssql db 1433 포트가 열려있다
A 서버는 B서버로 1433 포트 접근 가능
C 서버는 A 서버로 SSH 22 포트만 접근 가능
C 서버는 B 서버로 접근 불가능
C 서버에서 python으로  A서버 호출해서 B서버의 데이터를 가져오려면? 

### 요약
이 시나리오에서는 C 서버에서 B 서버의 MSSQL 데이터베이스(1433 포트)에 접근하려고 하지만, A 서버만 22번 포트가 열려 있어 B 서버에 직접 접근할 수 없는 상황. 
따라서, A 서버를 중간 서버로 사용하여 SSH 터널을 통해 C 서버에서 B 서버의 데이터베이스에 접근.

### 해결 방법: SSH 터널링을 통한 포트 포워딩
C 서버에서 A 서버로 SSH 연결을 설정하여 B 서버의 MSSQL 데이터베이스 포트(1433)를 포워딩.
Python 코드로 데이터베이스에 연결하여 필요한 데이터를 추출.
1단계: SSH 터널링 설정
C 서버에서 SSH 터널링을 사용하여 A 서버를 통해 B 서버의 1433 포트에 접근 필요. 
이를 위해 Python의 paramiko 라이브러리를 사용.

먼저 paramiko와 sshtunnel 패키지를 설치.

```
pip install paramiko sshtunnel
```
2단계: Python 코드로 SSH 터널링 및 데이터베이스 연결
Python 코드를 작성하여 C 서버에서 A 서버로 SSH 터널을 만들고, 그 터널을 통해 B 서버의 MSSQL 데이터베이스에 접근.

```
from sshtunnel import SSHTunnelForwarder
import pyodbc  # Python ODBC for MSSQL

# SSH 터널 설정
with SSHTunnelForwarder(
        ('A 서버 IP 주소', 22),  # A 서버의 IP 주소와 SSH 포트
        ssh_username='A 서버의 SSH 사용자명',
        ssh_password='A 서버의 SSH 비밀번호',
        remote_bind_address=('B 서버 IP 주소', 1433),  # B 서버의 IP 주소와 MSSQL 포트
        local_bind_address=('127.0.0.1', 1433)  # 로컬에서 사용할 포트
) as tunnel:
    
    # MSSQL 데이터베이스 연결 설정
    conn_str = (
        "DRIVER={ODBC Driver 17 for SQL Server};"
        f"SERVER=127.0.0.1,{tunnel.local_bind_port};"
        "DATABASE=데이터베이스_이름;"
        "UID=DB_사용자명;"
        "PWD=DB_비밀번호;"
    )
    
    # 데이터베이스 연결
    conn = pyodbc.connect(conn_str)
    cursor = conn.cursor()

    # 데이터 가져오기 예시
    cursor.execute("SELECT * FROM YourTableName")
    rows = cursor.fetchall()
    
    for row in rows:
        print(row)
    
    # 연결 종료
    cursor.close()
    conn.close()
```

### 코드 설명
SSHTunnelForwarder: A 서버를 통해 B 서버로 SSH 터널을 생성.   
이때, remote_bind_address는 B 서버의 MSSQL 포트를 의미하며, local_bind_address는 로컬에서 사용할 포트이다.  
pyodbc를 사용한 MSSQL 데이터베이스 연결: 터널을 통해 로컬의 127.0.0.1:1433으로 접속하여 실제 B 서버의 데이터베이스에 접근한다.   
최초 데이터를 요청하는 C 서버에 ODBC 드라이버가 설치되어 있어야 함.  
쿼리 실행 및 데이터 가져오기: 데이터베이스에 연결하여 쿼리를 실행하고 데이터를 추출.  
이 방법을 통해, C 서버에서 안전하게 A 서버를 통해 B 서버의 데이터베이스에 접근하여 데이터를 가져올 수 있다.  

