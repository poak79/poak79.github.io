---
title: "GitHub Pages 블로그 동작 원리: Jekyll과 YAML Front Matter 정리"
author: poak79
date: 2026-02-16 11:33:00 +0800
categories: [Dev, Git]
tags: [github-pages, jekyll, yaml, front-matter, static-site, github-actions]
pin: true
math: true
mermaid: true
---

### YAML / YFM / Jekyll이란?

```yaml
---
title: '"GitHub Pages" 동작 원리'
date: 2026-02-19 10:00:00 +0900
categories: [Dev, Blog]
tags: [github-pages, jekyll, yaml]
---
```

각 게시물 마크다운 파일 맨 위를 보면 `---`로 시작하는 블록을 볼 수 있다. 

이를 **YAML Front Matter(YFM)** 라고 한다.

YAML은 구성 파일 작성에 자주 사용되는 데이터 직렬화 언어 중 하나이다.
YFM은 글의 **설정/메타데이터**를 담는 블록이며, 본문 내용이 아니라 **사이트 생성 규칙**에 영향을 준다.

따라서 Front Matter 블록이 본문에 그대로 출력되지는 않지만, 테마/레이아웃이 이를 기반으로 사이트의 카테고리, 태그 등에 자동 반영한다. 

Jekyll은 정적 사이트 생성기이다. 

보통 Markdown + YAML Front Matter로 작성된 글을 읽어, 최종적으로 정적 HTML 페이지를 생성한다.

### GitHub Pages 동작 원리

- **로컬에서 하는 일**

`_posts/` 에 게시물로 올릴 마크다운 파일을 추가한다. 

원한다면 `bundle exec jekyll serve` 로 로컬에서 미리보기가 가능하다. 


- **git push 후 GitHub에서 일어나는 일**

Pages가 Jekyll을 직접 빌드하거나, GitHub Actions가 빌드한 정적 파일 결과물을 Pages에 업로드한다.


- **결과**

빌드 산출물(HTML/CSS/JS)이 Pages에 올라가고, 브라우저는 그 정적 파일을 그대로 내려받아 렌더링한다.
