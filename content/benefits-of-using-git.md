+++
date = 2019-10-04T00:00:00+09:00
lastmod = 2024-05-24T14:08:00+09:00
title = '내가 Git을 이용하면서 얻는 이점'
description = '내가 Git라는 버전 제어 체제를 이용하면서 얻는 이점과 여러 가지들'
category = ['정보', 'Git']
copyright = 'Copyright (c) 2019 Myeongjin.'
+++

이전에는 내가 [내가 휴고를 이용하면서 얻는 이점](/benefits-of-using-hugo)을 게시했었는데 이번에는 내가 [Git](https://git-scm.com)라는 버전 제어 체제를 이용하면서 얻는 이점을 알아본다.

## 버전 제어 기초
Git을 이용하면 저장소에서 자신의 작업한 버전이 여러 개일 때 커밋의 내역을 보고 현재의 잘못된 내용을 기존의 내용으로 찾아 고칠 수 있다. 이때 *커밋을 하여야* 자신이 리셋할 경우 스테이징이 사라지지 않는다.

### 브랜치
저장소에는 브랜치도 있어서

* 마스터에서 브랜치를 분기한 다음
* 그 브랜치에서 실험, 제안 기능을 작업하고 나서
* 그 브랜치에서 마스터로 그 작업을 병합할 수 있다. 또는 리베이스를 할 수도 있다.

나는 마스터의 작업을 복잡하게 하지 않고 다른 브랜치에서 작업하니까 편안해진다.

## 분산 버전 제어의 이점
버전 제어의 저장소가 서버에만 있는 경우 서버의 이용을 할 수 없다면 그 저장소에서 작업을 하고자 한다면 자신이 하고자 하는 작업을 서비스의 이용을 할 수 있을 때까지 기다려야 하므로 막막해질 것이고, 그 저장소의 작업이 서버에서 사라진다면 그 서버를 신뢰하기는 어려울 정도로 속상할 것이다. 누구라도 그럴 때가 있지 않을까.

하지만 Git을 이용할 경우 워킹 디렉토리를 갖지 않는 bare 저장소가 속해 있는 서버의 이용을 할 수 없을 때(예를 들어 서비스의 과부화 등으로 그것이 강제 종료되어 서비스의 이용이 불가능할 때(500 계열)나 서버 운영자의 실수로 저장소의 작업을 잃을 때, 자금이 부족하다는 등의 이유로 서버의 운영이 지속될 수 없을 때)나 저장소를 다른 서버로 복제/분기할 때 Git 저장소는 로컬에도 저장이 되어 있어서 로컬에서 자체적으로 작업을 하거나 다른 서버에 저장소를 푸쉬할 수 있다.

자신의 저장소의 백업이 쉬워지는 건 나는 두 말 할 필요가 없다고 본다. 자신이 저장소에서 로컬에서만 작업을 할 수도 있고.

## 내가 Git로 작업하는 환경 
나는 아라로그의 저장소를 제어하는 데에 있어서 윈도우와 Git, 그 중에서도 Git에 포함된 'Git Gui'를 사용한다. 이 앱에는 `Rebase`가 포함되지 않아 내가 쓰기에는 불편했다. 그래서 나는 다음과 같이 명령을 메뉴에 추가했다:

```
[guitool "Rebase onto..."]
    cmd = git rebase $REVISION
    revprompt = yes
[guitool "Rebase/Continue"]
    cmd = git rebase --continue
[guitool "Rebase/Skip"]
    cmd = git rebase --skip
[guitool "Rebase/Abort"]
    cmd = git rebase --abort
[guitool "Pull with Rebase"]
    cmd = git pull --rebase
```

출처는 <https://stackoverflow.com/questions/4830344/how-to-do-a-rebase-with-git-gui> 이다.

## 현재 내가 쓰는 gitconfig
현재 내가 쓰는 gitconfig는 다음과 같다:
```
[core]
	autocrlf = input
	eol = lf
	editor = \"C:\\Users\\username\\AppData\\Local\\Programs\\Microsoft VS Code\\Code.exe\" --wait
[user]
	email = example
	name = Full Name
[gui]
	encoding = utf-8
[guitool "Rebase onto..."]
    cmd = git rebase $REVISION
    revprompt = yes
[guitool "Rebase/Continue"]
    cmd = git rebase --continue
[guitool "Rebase/Skip"]
    cmd = git rebase --skip
[guitool "Rebase/Abort"]
    cmd = git rebase --abort
[guitool "Pull with Rebase"]
    cmd = git pull --rebase
```
