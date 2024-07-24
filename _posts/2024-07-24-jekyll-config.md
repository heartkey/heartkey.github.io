---
layout: single
# layout: splash
# layout: post
# layout: home
# layout: collection
title: "Jekyll config"
writer: CCBB
categories: dev
tags: frontend jekyll config blog
toc: true
toc_label: "My Table of Contents"
toc_sticky: true
toc_icon: "cog"
# classes: wide

excerpt: "Jekyll의 _config.yml 파일은 사이트 설정을 관리하는 파일입니다. 사이트의 기본 구성부터 플러그인 설정, 사이트 전역 변수까지 다양한 설정을 포함할 수 있습니다. _config.yml에서 설정 가능한 주요 항목들과 그 설명입니다."
header:
  teaser: /assets/images/jekyll-logo.png
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


### 기본 설정

#### Site Settings (사이트 설정)
* title: 사이트 제목
* description: 사이트 설명
* url: 사이트의 기본 URL
* baseurl: 사이트의 기본 경로 (예: /blog)
``` yaml
title: My Blog
description: A blog about Jekyll and Liquid
url: "https://myblog.github.io"
baseurl: ""
```

#### Build Settings (빌드 설정)
* source: 소스 파일이 위치한 디렉토리 (기본값: .)
* destination: 빌드된 파일이 위치한 디렉토리 (기본값: _site)
* plugins_dir: 플러그인 파일이 위치한 디렉토리 (기본값: _plugins)
* layouts_dir: 레이아웃 파일이 위치한 디렉토리 (기본값: _layouts)
``` yaml
source: .
destination: _site
plugins_dir: _plugins
layouts_dir: _layouts
```

#### Markdown 설정
* markdown: Markdown 변환기에 대한 설정 (예: kramdown, redcarpet)
```yaml
markdown: kramdown
```

#### Kramdown 설정 예시

``` yaml
kramdown:
  input: GFM
  auto_ids: true
  hard_wrap: false
```

#### Permalinks (영구 링크 설정)
* permalink: 게시물의 URL 구조를 정의
``` yaml
permalink: /:categories/:year/:month/:day/:title.html
```

#### Pagination (페이지 네비게이션 설정)
* paginate: 페이지당 표시할 게시물 수
* paginate_path: 페이지 네비게이션의 경로
``` yaml
paginate: 10
paginate_path: "/page:num/"
```

#### Collections (컬렉션 설정)
컬렉션을 정의하여 블로그 포스트 이외의 콘텐츠를 관리

```yaml
collections:
  my_collection:
    output: true
    permalink: /:collection/:name
```

#### Defaults (기본 값 설정)
특정 범위에 대한 기본 설정을 정의

```yaml
defaults:
  - scope:
      path: ""
      type: "posts"
    values:
      layout: "post"
      author: "John Doe"
```

#### Exclude / Include (제외 / 포함 설정)
빌드 시 포함하거나 제외할 파일 또는 디렉토리

```yaml
exclude:
  - README.md
  - Gemfile
include:
  - _pages
```

#### Plugins (플러그인 설정)
사용할 플러그인 목록

```yaml
plugins:
  - jekyll-feed
  - jekyll-seo-tag
```

#### Sass (Sass 설정)
Sass 파일을 처리하는 방법 설정

```yaml
sass:
  sass_dir: _sass
  style: compressed
```

#### Liquid (Liquid 설정)
Liquid 템플릿 엔진에 대한 설정

```yaml
liquid:
  error_mode: warn
```

#### URL (URL 설정)
URL 관련 설정
* url: 사이트의 기본 URL
* baseurl: 사이트의 기본 경로 (예: /blog)
```yaml
url: "https://myblog.github.io"
baseurl: "/blog"
```

#### Host (호스트 설정)
로컬 서버 호스트 및 포트 설정

```yaml
host: 127.0.0.1
port: 4000
```

#### Incremental (증분 빌드 설정)
증분 빌드 활성화 (변경된 파일만 빌드)

```yaml
incremental: true
```

#### Watch (파일 변경 감지 설정)
파일 변경 감지 활성화

```yaml
watch: true
```

#### Future (미래 게시물 설정)
미래 날짜의 게시물을 포함할지 여부 설정

```yaml
future: true
```

#### Timezone (시간대 설정)
사이트의 시간대 설정

```yaml
timezone: "America/New_York"
```

#### Plugins Directory (플러그인 디렉토리 설정)
플러그인 파일이 위치한 디렉토리 설정

```yaml
plugins_dir: _plugins
```

#### 기타 설정
Safe Mode (안전 모드)
사용자 정의 플러그인을 비활성화합니다.

```yaml
safe: true
```

#### Include (포함할 파일/디렉토리 목록)
빌드할 때 포함할 추가 파일/디렉토리 목록을 지정합니다.

```yaml
include:
  - .htaccess
```

#### Exclude (제외할 파일/디렉토리 목록)
빌드할 때 제외할 파일/디렉토리 목록을 지정합니다.

```yaml
exclude:
  - Gemfile
  - Gemfile.lock
```

#### Keep Files (유지할 파일 목록)
정적 사이트 빌드 중 유지할 파일 목록을 지정합니다.

```yaml
keep_files:
  - .git
  - .svn
```

#### Markdown (마크다운 처리기 설정)
사용할 마크다운 처리기를 설정합니다.

```yaml
markdown: kramdown
```

#### Encoding (인코딩 설정)
사이트의 기본 인코딩을 설정합니다.

```yaml
encoding: UTF-8
```

#### Include (포함할 파일 목록)
빌드할 때 포함할 파일 목록을 지정합니다.

```yaml
include:
  - .htaccess
```

#### Exclude (제외할 파일 목록)
빌드할 때 제외할 파일 목록을 지정합니다.

```yaml
exclude:
  - Gemfile
  - Gemfile.lock
```

#### Whitelisted Plugins (허용된 플러그인 목록)
특정 플러그인만 허용합니다.

```yaml
whitelist:
  - jekyll-paginate
  - jekyll-seo-tag
```

#### Markdown (마크다운 처리기 설정)
사용할 마크다운 처리기를 설정합니다.

```yaml
markdown: kramdown
```

#### Kramdown (Kramdown 설정)
Kramdown 마크다운 처리기에 대한 설정을 지정합니다.

```yaml
kramdown:
  input: GFM
  auto_ids: true
  syntax_highlighter: rouge
```

#### Gems (젬 설정)
사용할 젬 목록을 지정합니다.

```yaml
gems:
  - jekyll-paginate
  - jekyll-seo-tag
```

#### Permalinks (퍼머링크 설정)
게시물의 퍼머링크 형식을 지정합니다.

```yaml
permalink: /:categories/:year/:month/:day/:title/
```

#### Pagination (페이지네이션 설정)
페이지네이션 설정을 지정합니다.

```yaml
paginate: 10
paginate_path: "/page:num/"
```

#### 예제 _config.yml
```yaml
# Site settings
title: My Blog
description: A blog about Jekyll and Liquid
url: "https://myblog.github.io"
baseurl: ""

# Build settings
source: .
destination: _site
plugins_dir: _plugins
layouts_dir: _layouts

# Markdown settings
markdown: kramdown
kramdown:
  input: GFM
  auto_ids: true
  syntax_highlighter: rouge

# Permalinks
permalink: /:categories/:year/:month/:day/:title.html

# Pagination
paginate: 10
paginate_path: "/page:num/"

# Collections
collections:
  my_collection:
    output: true
    permalink: /:collection/:name

# Defaults
defaults:
  - scope:
      path: ""
      type: "posts"
    values:
      layout: "post"
      author: "John Doe"

# Exclude / Include
exclude:
  - README.md
  - Gemfile
include:
  - _pages

# Plugins
plugins:
  - jekyll-feed
  - jekyll-seo-tag

# Sass
sass:
  sass_dir: _sass
  style: compressed

# Liquid
liquid:
  error_mode: warn

# URL
url: "https://myblog.github.io"
baseurl: "/blog"

# Host
host: 127.0.0.1
port: 4000

# Incremental build
incremental: true

# Watch files
watch: true

# Future posts
future: true

# Timezone
timezone: "America/New_York"
```

이 예제는 Jekyll의 _config.yml 파일에서 설정 가능한 다양한 항목을 포함하고 있습니다. 필요에 따라 설정을 추가하거나 수정하여 사이트를 원하는 대로 구성할 수 있습니다.