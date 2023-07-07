---
title: "atom for hugo를 만들었습니다."
date: 2019-10-10T20:45:28+09:00
modified: 2019-10-12T15:10:00+09:00
subtitle: "내가 Git라는 버전 제어 체제를 이용하면서 얻는 이점과 여러 가지들"
tags: ["알림", "휴고"]
author: "Myeongjin"
copyright: "Copyright (c) 2019 Myeongjin."
footer: "저작권 2019 명진. [라이선스를 보세요](./license.html)."
---

내가 atom for hugo를 만들었다.

## 적용하기
1. 다운로드의 사이트로 이동하여 `Clone or download`를 선택, Git을 사용해 그 주소에서 저장소를 복제하거나 `Download ZIP`을 선택하여 다운로드한다.
2. `/사이트/themes/`에 이를 붙여넣는다.
3. `config.toml`에서 다음과 같이 테마를 설정한다.
`theme = ["atom-for-hugo", "설정할 테마"]`
4. `config.toml`에서 다음과 같이 `output`를 설정한다. 기본값은 `["HTML", "RSS"]`이다.
```
[outputs]
home = ["HTML", "RSS", "Atom"]
section = ["HTML", "RSS", "Atom"]
taxonomyTerm = ["HTML", "RSS", "Atom"]
taxonomy = ["HTML", "RSS", "Atom"]
```
5. 테마에 따라 `/사이트/layouts/partials`에 `footer.html`을 복사한 다음 다음과 같이 수정한다. (테마에 따라 다름)
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
* [GitHub에서 다운로드](https://github.com/araname/atom-for-hugo.git) (주)
* [GitLab에서 다운로드](https://github.com/araname/atom-for-hugo) (미러)
