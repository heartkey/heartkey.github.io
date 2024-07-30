---
layout: single
# layout: splash
# layout: post
# layout: home
# layout: collection
title: "Java JDK 각 버전별 기능 및 지원 요약"
writer: CCBB
categories: dev
tags: java jdk LTS backend
toc: true
toc_label: "My Table of Contents"
toc_sticky: true
toc_icon: "cog"
# classes: wide

excerpt: "Java 각 버전은 새로운 기능, 성능 향상 및 보안 업데이트를 포함하고 있습니다."
header:
  teaser: /assets/images/java-logo.png
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


#### Java 버전 및 특징
##### Java SE 8 (2014년 3월 출시)

* 주요 특징:
  * 람다 표현식
  * 스트림 API
  * 새로운 날짜 및 시간 API (java.time 패키지)
  * Nashorn JavaScript 엔진
  * 메타스페이스(Metaspace)
* 지원 기간:
  * Oracle의 LTS(Long-Term Support) 버전으로, 일반적인 지원은 2019년 1월까지, 확장 지원은 2030년까지 제공됩니다.

##### Java SE 9 (2017년 9월 출시)

* 주요 특징:
  * 모듈 시스템 (Project Jigsaw)
  * JShell (REPL)
  * 새로운 HTTP 클라이언트 API (incubator)
  * 여러 성능 및 보안 개선
* 지원 기간:
  * Oracle의 비-LTS 버전으로, 일반적인 지원은 2018년 3월까지 제공되었습니다.

##### Java SE 10 (2018년 3월 출시)

* 주요 특징:
  * 지역 변수 유형 추론 (var 키워드)
  * 애플리케이션 클래스-데이터 공유 (AppCDS)
  * 여러 성능 및 보안 개선
* 지원 기간:
  * Oracle의 비-LTS 버전으로, 일반적인 지원은 2018년 9월까지 제공되었습니다.

##### Java SE 11 (2018년 9월 출시)

* 주요 특징:
  * 로컬-변수 구문 for 람다 매개변수
  * HTTP 클라이언트 API (표준화)
  * 여러 모듈화 기능 및 API 개선
* 지원 기간:
  * Oracle의 LTS 버전으로, 일반적인 지원은 2023년까지, 확장 지원은 2026년까지 제공됩니다.

##### Java SE 12 (2019년 3월 출시)

* 주요 특징:
  * 새로운 스위치 표현식 (프리뷰)
  * JVM 개선 (Shenandoah 가비지 컬렉터 등)
  * 여러 성능 및 보안 개선
* 지원 기간:
  * Oracle의 비-LTS 버전으로, 일반적인 지원은 2019년 9월까지 제공되었습니다.

##### Java SE 13 (2019년 9월 출시)

* 주요 특징:
  * 텍스트 블록 (프리뷰)
  * 스위치 표현식 (프리뷰)
  * 여러 성능 및 보안 개선
* 지원 기간:
  * Oracle의 비-LTS 버전으로, 일반적인 지원은 2020년 3월까지 제공되었습니다.

##### Java SE 14 (2020년 3월 출시)

* 주요 특징:
  * 스위치 표현식 (표준화)
  * 텍스트 블록 (프리뷰)
  * 새로운 패턴 매칭 (instanceof)
  * 여러 성능 및 보안 개선
* 지원 기간:
  * Oracle의 비-LTS 버전으로, 일반적인 지원은 2020년 9월까지 제공되었습니다.

##### Java SE 15 (2020년 9월 출시)

* 주요 특징:
  * 텍스트 블록 (표준화)
  * 숨겨진 클래스
  * 새로운 패턴 매칭 (프리뷰)
  * Sealed 클래스 (프리뷰)
  * 여러 성능 및 보안 개선
* 지원 기간:
  * Oracle의 비-LTS 버전으로, 일반적인 지원은 2021년 3월까지 제공되었습니다.

##### Java SE 16 (2021년 3월 출시)

* 주요 특징:
  * 패턴 매칭 for instanceof (표준화)
  * Records (표준화)
  * Sealed 클래스 (프리뷰)
  * 외부 메모리 접근 API (incubator)
  * 여러 성능 및 보안 개선
* 지원 기간:
  * Oracle의 비-LTS 버전으로, 일반적인 지원은 2021년 9월까지 제공되었습니다.

##### Java SE 17 (2021년 9월 출시)

* 주요 특징:
  * LTS 버전
  * 새로운 패턴 매칭 (표준화)
  * Sealed 클래스 (표준화)
  * 외부 메모리 접근 API (incubator)
  * 여러 성능 및 보안 개선
* 지원 기간:
  * Oracle의 LTS 버전으로, 일반적인 지원은 2026년까지, 확장 지원은 2029년까지 제공됩니다.

##### Java SE 18 (2022년 3월 출시)

* 주요 특징:
  * 단순 웹 서버
  * 코드 스니펫 in Javadoc
  * UTF-8 기본 문자셋
  * Vector API (Incubator)
  * 외부 함수 및 메모리 API (2nd Incubator)
* 지원 기간:
  * Oracle의 비-LTS 버전으로, 일반적인 지원은 2022년 9월까지 제공되었습니다.

##### Java SE 19 (2022년 9월 출시)

* 주요 특징:
  * Foreign Function & Memory API (Preview)
  * Pattern Matching for switch (3rd Preview)
  * Record Patterns (Preview)
  * Virtual Threads (Preview)
* 지원 기간:
  * Oracle의 비-LTS 버전으로, 일반적인 지원은 2023년 3월까지 제공되었습니다.

##### Java SE 20 (2023년 3월 출시)

* 주요 특징:
  * Scoped Values (Incubator)
  * Record Patterns (2nd Preview)
  * Pattern Matching for switch (4th Preview)
  * Foreign Function & Memory API (2nd Preview)
  * Virtual Threads (2nd Preview)
* 지원 기간:
  * Oracle의 비-LTS 버전으로, 일반적인 지원은 2023년 9월까지 제공됩니다.

##### Java SE 21 (2023년 9월 출시)

* 주요 특징:
  * LTS 버전
  * Pattern Matching for switch (Standard)
  * Record Patterns (Standard)
  * Virtual Threads (Standard)
  * Foreign Function & Memory API (Standard)
* 지원 기간:
  * Oracle의 LTS 버전으로, 일반적인 지원은 2026년까지, 확장 지원은 2029년까지 제공됩니다.



|버전	|출시일	|LTS 여부	|일반 지원 종료	|확장 지원 종료|
|----|-----|--------|------------|----------|
|Java SE 8	|2014년 3월	|LTS	|2019년 1월	|2030년 3월|
|Java SE 9	|2017년 9월	|비-LTS	|2018년 3월|	-|
|Java SE 10	|2018년 3월	|비-LTS	|2018년 9월|	-|
|Java SE 11	|2018년 9월	|LTS	|2023년 9월	|2026년 9월|
|Java SE 12	|2019년 3월	|비-LTS	|2019년 9월|	-|
|Java SE 13	|2019년 9월	|비-LTS	|2020년 3월|	-|
|Java SE 14	|2020년 3월	|비-LTS	|2020년 9월|	-|
|Java SE 15	|2020년 9월	|비-LTS	|2021년 3월|	-|
|Java SE 16	|2021년 3월	|비-LTS	|2021년 9월|	-|
|Java SE 17	|2021년 9월	|LTS	|2026년 9월	|2029년 9월|
|Java SE 18	|2022년 3월	|비-LTS	|2022년 9월|	-|
|Java SE 19	|2022년 9월	|비-LTS	|2023년 3월|	-|
|Java SE 20	|2023년 3월	|비-LTS	|2023년 9월|	-|
