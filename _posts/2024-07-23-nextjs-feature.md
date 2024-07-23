---
layout: single
# layout: splash
# layout: post
# layout: home
# layout: collection
title: "Next.js 14 : Feature"
writer: CCBB
categories:
  - dev 
tags:
  - nextjs
  - frontend
toc: true
toc_label: "My Table of Contents"
toc_sticky: true
toc_icon: "cog"
# classes: wide

excerpt: "Next.js 14은 최신 웹 애플리케이션 개발을 위한 다양한 기능을 제공하며, 개발자들이 효율적으로 작업할 수 있도록 도와줍니다."
header:
  teaser: /assets/images/unsplash-gallery-image-1.jpg
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


## Next.js Feature

## Next.js 14은 최신 웹 애플리케이션 개발을 위한 다양한 기능을 제공하며, 개발자들이 효율적으로 작업할 수 있도록 도와줍니다.

## Next.js 14의 주요 기능

### 1. React 18 지원 및 서버 컴포넌트
Next.js 14는 React 18의 새로운 기능들을 지원합니다. 특히 서버 컴포넌트를 활용한 스트리밍과 점진적 서버 렌더링(SSR)을 통해 성능을 최적화할 수 있습니다.

* 서버 컴포넌트: 서버에서 렌더링되며 클라이언트에 전달되는 컴포넌트로, 초기 로딩 성능을 향상시키고 클라이언트 측 JavaScript 번들을 줄일 수 있습니다.
### 2. 안정화된 앱 디렉터리(App Directory)
Next.js 14에서는 app/ 디렉토리가 안정화되어, 새로운 파일 기반 라우팅 시스템을 활용할 수 있습니다. 이는 pages/ 디렉토리와 별개로 동작하며, 더 유연하고 강력한 라우팅 옵션을 제공합니다.

### 3. 파일 기반 라우팅
Next.js 14에서는 파일 시스템을 기반으로 한 라우팅이 가능합니다. 이는 폴더 구조를 기반으로 자동으로 라우트를 생성합니다.

* 중첩 라우트: 중첩된 폴더 구조를 통해 중첩된 라우트를 쉽게 정의할 수 있습니다.
* 동적 라우트: 파일 이름에 대괄호를 사용하여 동적 라우트를 생성할 수 있습니다.

``` javascript

// app/posts/[id]/page.tsx
export default function PostPage({ params }) {
  return <div>Post ID: {params.id}</div>;
}
```

### 4. Improved Data Fetching (데이터 페칭 개선)
데이터 페칭을 위한 새로운 훅과 기능들이 도입되어, 클라이언트와 서버에서 데이터를 효율적으로 가져올 수 있습니다.

* use 훅: React의 새로운 훅을 사용하여 서버 컴포넌트와 함께 데이터를 가져올 수 있습니다.

``` javascript

// app/page.tsx
import { use } from 'react';

export default function HomePage() {
  const data = use(fetchData());

  return <div>Data: {data}</div>;
}

async function fetchData() {
  const res = await fetch('https://api.example.com/data');
  return res.json();
}
```

### 5. Middleware
Middleware를 사용하여 요청이 처리되기 전에 실행되는 코드를 작성할 수 있습니다. 이를 통해 인증, 로깅, 리다이렉션 등을 쉽게 구현할 수 있습니다.

``` javascript

// middleware.ts
import { NextResponse } from 'next/server';

export function middleware(request) {
  const response = NextResponse.next();
  // 요청 처리 로직 추가
  return response;
}
```

### 6. Optimized Images (이미지 최적화)
Next.js의 이미지 컴포넌트(next/image)가 더욱 향상되어, 다양한 이미지 최적화 기능을 제공합니다. 이는 이미지의 크기를 자동으로 조절하고, 적절한 포맷으로 변환하여 성능을 개선합니다.

``` javascript

import Image from 'next/image';

export default function HomePage() {
  return (
    <div>
      <Image src="/me.png" alt="Picture of me" width={500} height={500} />
    </div>
  );
}
```

### 7. 서버 액션(Server Actions)
Next.js 14에서는 서버 액션을 도입하여, 서버에서 직접 동작을 수행할 수 있는 함수를 정의할 수 있습니다. 이는 클라이언트와 서버 간의 데이터 흐름을 간소화합니다.

``` javascript

// app/actions/submitForm.ts
'use server';

export async function submitForm(data) {
  // 서버에서 폼 데이터 처리
  return { success: true };
}

// app/page.tsx
import { submitForm } from './actions/submitForm';

export default function HomePage() {
  async function handleSubmit(event) {
    event.preventDefault();
    const result = await submitForm(new FormData(event.target));
    console.log(result);
  }

  return (
    <form onSubmit={handleSubmit}>
      <input type="text" name="name" />
      <button type="submit">Submit</button>
    </form>
  );
}
```

### 8. TypeScript 지원 향상
Next.js 14는 TypeScript 지원이 더욱 향상되어, 개발자 경험을 개선하고 더 나은 타입 안전성을 제공합니다. 이는 자동 타입 생성, 타입 검사, 그리고 더 나은 개발자 도구 통합을 포함합니다.

### 9. API 라우트 개선
API 라우트가 더욱 강력해지고, 새로운 기능과 개선된 성능을 제공합니다. 이를 통해 서버리스 함수 및 API 엔드포인트를 쉽게 정의하고 관리할 수 있습니다.

``` javascript

// pages/api/hello.ts
import type { NextApiRequest, NextApiResponse } from 'next';

export default function handler(req: NextApiRequest, res: NextApiResponse) {
  res.status(200).json({ message: 'Hello, world!' });
}
```
### 10. 에지 컴퓨팅 지원
Next.js는 Vercel의 에지 네트워크와의 긴밀한 통합을 통해 에지 컴퓨팅을 지원합니다. 이를 통해 전 세계적으로 빠른 응답 시간을 제공할 수 있습니다.

이러한 기능들은 Next.js 14가 웹 애플리케이션 개발에 있어 강력하고 유연한 프레임워크로 자리 잡을 수 있도록 돕습니다. 각 기능을 적절히 활용하여 최적의 성능과 개발자 경험을 얻을 수 있습니다.


### 11. Next.js 13, 14 비교 요약

|기능|Next.js 13|Next.js 14|
|----|-----------|----------|
|App Directory|도입|안정화 및 개선|
|서버 컴포넌트|도입|안정화 및 성능 개선|
|React 18|지원|지원|
|데이터 페칭|use 훅 도입|데이터 페칭 훅 및 기능 개선|
|이미지 최적화|next/image 개선|최적화 기능 추가 및 성능 개선|
|Middleware|새로운 API 도입|성능 및 기능 개선|
|ES Modules|지원 시작|지속적인 개선|
|Server Actions|없음|도입 및 간소화|
|TypeScript|지원|지원 및 향상|
|API 라우트|기본 기능|성능 및 기능 개선|
|에지 컴퓨팅|제한적 지원|강화된 지원|
