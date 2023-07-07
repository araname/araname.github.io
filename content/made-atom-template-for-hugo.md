+++
date = 2019-10-10T20:45:28+09:00
lastmod = 2024-05-24T18:55:00+09:00
title = 'Atom Template for Hugo를 만들었습니다.'
category = ['정보', '휴고']
copyright = 'Copyright (c) 2019, 2024 Myeongjin.'
+++

내가 [Hugo](https://gohugo.io)에 기본 지원되는 RSS가 마음에 들지 않아서 Atom Template for Hugo를 만들었다.

## 설치하기
1. 다운로드의 사이트로 이동하여 `Clone or download`를 선택, Git을 사용해 그 주소에서 저장소를 복제하거나 `Download ZIP`을 선택하여 다운로드한다.
2. `/사이트/themes/`에 이를 붙여넣는다.

## 구성하기
1. `hugo.toml`에서 다음과 같이 테마를 설정한다.
`theme = ['atom-template-for-hugo', '설정할 테마']`
2. `hugo.toml`에서 다음과 같이 `output`를 설정한다. 기본값은 `['HTML', 'RSS']`이다.
```
[outputs]
home = ['HTML', 'Atom' , 'RSS']
section = ['HTML', 'Atom' , 'RSS']
taxonomyTerm = ['HTML', 'Atom' , 'RSS']
taxonomy = ['HTML', 'Atom' , 'RSS']
```
3. 테마에 따라 `/사이트/layouts/partials`에 `footer.html`을 복사한 다음 다음과 같이 수정한다. (테마에 따라 다름)
```
    {{- with .OutputFormats.Get "RSS" }}
      <a href="{{ .RelPermalink }}" type="application/rss+xml" target="_blank" title="RSS">
        RSS
      </a>
    {{- end }}
    {{- with .OutputFormats.Get "Atom" }}
      <a href="{{ .RelPermalink }}" type="application/atom+xml" target="_blank" title="Atom">
        Atom
      </a>
    {{- end }}
```

## 다운로드
* [GitHub에서 다운로드](https://github.com/araname/atom-template-for-hugo) (주)
* [GitLab에서 다운로드](https://gitlab.com/araname/atom-template-for-hugo) (미러)
