---
layout: single
# layout: splash
# layout: post
# layout: home
# layout: collection
title: "[Gihub Blog] 마크다운(Markdown), kramdown 문법 사용"
writer: CCBB
categories: dev 
tags: github.io github blog markdown kramdown frontend jekyll
toc: true
toc_label: "My Table of Contents"
toc_sticky: true
toc_icon: "cog"
# classes: wide

excerpt: "kramdown은 표준 마크다운(Markdown)의 기능을 확장하여 다양한 기능을 제공합니다. 여기서는 kramdown에서만 지원되는 주요 문법 및 기능들을 정리하겠습니다"
# thumnail: /assets/images/nextjs-cover.jpg
header:
  teaser: /assets/images/markdown-logo.png
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

kramdown은 표준 마크다운(Markdown)의 기능을 확장하여 다양한 기능을 제공합니다. 여기서는 kramdown에서만 지원되는 주요 문법 및 기능들을 정리하겠습니다.

#### 1. 블록 요소 (Block Elements)
##### 1.1 표 (Tables)

kramdown은 표를 지원합니다.

```
| Header 1 | Header 2 |
|----------|----------|
| Cell 1   | Cell 2   |
| Cell 3   | Cell 4   |
```

##### 1.2 정의 목록 (Definition Lists)

용어와 정의를 나란히 배치할 수 있는 정의 목록을 지원합니다.

```
Term 1
:   Definition 1

Term 2
:   Definition 2a
:   Definition 2b
```

##### 1.3 각주 (Footnotes)

각주를 추가할 수 있습니다.

```
텍스트와 함께 각주를 사용할 수 있습니다[^1].

[^1]: 여기에 각주 내용이 들어갑니다.
```

##### 1.4 블록 수학 표현식 (Block Mathematical Expressions)

수학 블록을 지원합니다.

```
$$
E = mc^2
$$
```

##### 1.5 줄바꿈 (Line Breaks)

kramdown은 명시적인 줄바꿈을 허용합니다. 마지막 공백 2개 추가

```
이것은 한 줄입니다.
그리고 이것은 다음 줄입니다.
```

##### 1.6 블록 인용 (Block Quotes)

kramdown은 중첩된 블록 인용을 지원합니다.

```
> 이것은 첫 번째 인용입니다.
> 
> > 이것은 두 번째 인용입니다.
```

#### 2. 인라인 요소 (Inline Elements)
##### 2.1 하이라이트 (Highlighting)

텍스트 하이라이트 기능을 지원합니다.

```
이것은 ==하이라이트된 텍스트==입니다.
```

##### 2.2 인라인 수학 표현식 (Inline Mathematical Expressions)

인라인 수학 표현식을 지원합니다.

```
인라인 수학: $E = mc^2$
```

##### 2.3 자동 링크 (Automatic Links)

텍스트 내 URL이나 이메일 주소를 자동으로 링크로 변환합니다.

```
<http://example.com>
<mailto:example@example.com>
```

#### 3. HTML5 비호환 태그 (HTML5 Non-Conforming Tags)
HTML5 비호환 태그를 사용할 수 있습니다.

```
<mark>하이라이트된 텍스트</mark>
```

#### 4. 문서 구조 (Document Structure)
##### 4.1 Inline Attribute Lists (IAL)

요소에 속성을 추가할 수 있는 기능을 지원합니다.

```
# 제목 1 {#custom-id .custom-class}
```

##### 4.2 속성 목록 (Attribute Lists)

블록 요소에도 속성을 추가할 수 있습니다.

```
- 항목 1
- 항목 2
{: .custom-class #custom-id }
```

#### 5. 기타 기능
##### 5.1 구문 강조 (Syntax Highlighting)

코드 블록의 언어를 지정할 수 있어 구문 강조(syntax highlighting)가 가능합니다.

```
```ruby
def hello
  puts 'Hello, world!'
end
```

##### 5.2 텍스트 변형 (Text Transformation)

kramdown은 텍스트 변형 필터를 제공합니다.

```
{% raw %}
~This text will be transformed~
{% endraw %}
```

##### 5.3 HTML 엔티티 (HTML Entities)

HTML 엔티티를 지원합니다.

``` html
&copy; &amp; &lt; &gt;
```

##### 5.4 HTML 블록 (HTML Blocks)

HTML 블록을 지원합니다.

```
<div class="example">
  <p>HTML 블록 콘텐츠</p>
</div>
```

##### 5.5 링크 타이틀 (Link Titles)

링크에 타이틀 속성을 추가할 수 있습니다.

```
[Google](https://www.google.com "Google's Homepage")
```

##### 5.6 표준 하이퍼링크 (Standard Hyperlinks)

표준 하이퍼링크를 지원합니다.

```
[example link](http://example.com)
```

#### kramdown 설정 예제
아래는 kramdown의 다양한 설정을 포함한 _config.yml 예제입니다.

```
markdown: kramdown
kramdown:
  input: GFM
  auto_ids: true
  syntax_highlighter: rouge
  syntax_highlighter_opts:
    default_lang: "ruby"
    line_numbers: true
  entity_output: as_char
  toc_levels: 1..6
  smart_quotes: lsquo,rsquo,ldquo,rdquo
  footnote_nr: 1
  show_warnings: true
```  

* input: 사용할 마크다운 문법 (기본값: GFM).
* auto_ids: 자동으로 헤딩에 ID를 생성할지 여부.
* syntax_highlighter: 사용할 구문 강조 도구 (예: rouge).
* syntax_highlighter_opts: 구문 강조 도구의 옵션.
* entity_output: HTML 엔티티 출력 방식 (기본값: as_char).
* toc_levels: 목차 수준.
* smart_quotes: 스마트 인용 부호 설정.
* footnote_nr: 각주 번호 시작 값.
* show_warnings: 경고 메시지 표시 여부.

kramdown은 이러한 다양한 기능을 통해 마크다운 문서를 더욱 풍부하고 유연하게 작성할 수 있게 해줍니다. 표준 Markdown에서는 지원하지 않는 고급 기능들을 사용하여 더욱 복잡한 문서도 쉽게 작성할 수 있습니다.

#### 참고 사이트
* [kramdown](https://kramdown.gettalong.org)