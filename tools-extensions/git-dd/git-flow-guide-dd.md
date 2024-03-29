# Git Flow

## [Git Flow 사용 가이드](https://danielkummer.github.io/git-flow-cheatsheet/index.ko\_KR.html)

## Init

{% hint style="info" %}
&#x20;git flow init을 하면 develop branch가 자동 생성된다.
{% endhint %}

```bash
git flow init   // git 버전관리 시작
git branch      // develop branch 생성된 것 확인
```

## git branch

{% hint style="info" %}
각 기능과 상황에 맞는 브런치에서 작업 후 main에 merge 해준다.
{% endhint %}

```bash
git branch               // 현재 branch 확인
git branch -r            // 원격에 있는 branch만 확인 
git branch -a            // 모든 branch 확인
git branch -D 브랜치명    // 브랜치명 삭제(main에서만 가능/영구삭제는 아님)
```

* main: 릴리즈 후 사용자에게 배포되는 안정화된 버전
* develop: 다음 릴리즈를 위해 개발중인 최신 버전
* feature: 특정 기능 개발을 위한 branch
* release: 배포 전 최종 점검을 위한 branch
* hotfix: 이미 배포된 버전에서 발생한 버그를 긴급하게 수정하는 branch

## git checkout

```bash
git checkout develop     // develop branch로 이동
git checkout -b 브랜치명  // 브랜치명을 생성함과 동시에 이동
git checkout -t origin/develop // 원격의 develop 브랜치 가져오기
```

## git flow feature

{% hint style="info" %}
특정 기능을 개발하기 위한 branch가 필요한 경우 feature을 이용한다.
{% endhint %}

```bash
git flow feature start 브랜치명   // feature branch 생성 후 자동 체크아웃
git flow feature finish 브랜치명  // 브랜치명 develop로 merge 및 삭제 후 자동 체크아웃 
git flow feature publish 브랜치명 // 원격 저장소에 게시하여 다른 개발자와 공동으로 협업 가능
git flow feature pull origin 브랜치명 //  원격 저장소에만 있는 branch 가져오기
```

## git flow release

{% hint style="info" %}
현재 develop branch를 사용자에게 배포 전 릴리즈 점검을 위해 간단한 버그를 수정하는 목적으로 사용된다.
{% endhint %}

```bash
git flow release start [버전명] > release branch 생성 후 자동 체크아웃
git flow release finish [버전명] > main, develop branch에 merge 후 자동으로 삭제
```

* main branch에 merge => 엔터만 치면 됨
* release 이름으로 태그를 등록 => 배포할 때 뜨게 할 태그 입력 후 엔터
* develop branch에 재병합 => 엔터만 치면 됨

## git merge

```bash
git merge 브랜치명    // 현재 헤더가 가리키는 브랜치와 다른 브랜치를 병합
```

## git push

{% hint style="info" %}
원격 저장소에 push하기 전까지는 release를 한 후에도 로컬 컴퓨터에만 변경사항이 저장되어 있다.
{% endhint %}

<pre class="language-bash"><code class="lang-bash"><strong>git push -u origin develop  // 원격 저장소에 develop branch가 없을 경우
</strong>git push origin main        // 원격 저장소 main branch에 push</code></pre>

## git tag

{% hint style="info" %}
release 단계에서 입력한 tag도 따로 push를 진행해야 원격 저장소에 저장된다.
{% endhint %}

```bash
git tag
git push --tags
```

## git stash

{% hint style="info" %}
하나의 파일을 두명이서 수정 후 그중 하나의 파일을 원격 저장소에 올렸을 경우, 내가 수정하던 파일을 옆으로 잠깐 치우고 변경된 파일을 다운받을 수 있다.
{% endhint %}

```bash
git stash                   // 수정한 작업 중 commit 안된 파일들만 잠시 스택으로 이동
git stash list              // 지금까지 저장된 stash 목록 확인
git stash apply stash 파일명 // 다시 working directory로 이동
git stash apply --index     // 선택한 stash 파일을 staged 상태로 복원
git stash drop 파일명        // apply를 해도 여전히 스택에 남아있음으로 제거해줘야함
```

## 협업 예시

### 다른 개발자 레포에서 협업하는 경우

{% hint style="info" %}
**관리 권한이 없는 경우**

1. 저장소를 fork 한 후 내 원격 저장소로 이동
2. 로컬 저장소에서 작업 후 최종 결과물은 내 원격 저장소의 develop branch에 push
3. 내 원격 저장소로 들어가 나의 develop branch를 병합해달라고 PR 요청
4. 프로젝트 관리자가 코드 확인 후 병합 또는 수정요청 진행
{% endhint %}

{% hint style="info" %}
**관리 권한이 있는 경우**

1. 관리자 원격 레포 주소가 등록되어 있지 않다면 추가
2. 관리자 원격 레포에 추가된 기능 fetch 및 merge
3. 관리자 레포의 develop branch로 push
{% endhint %}

```bash
git remote add upstream [관리자 원격 레포 url]
git fetch upstream develop
git merge FETCH_HEAD
git push upstream develop 
```

### 내가 관리자인 경우

{% hint style="info" %}
1. 원격 저장소 내 이슈 및 프로젝트를 확인 후 업무를 요청하고 PR온 작업물을 체크
2. PR온 작업물을 원격 저장소 develop branch에 push 한 후 충돌사항을 체크
3. release branch에서 최종 점검을 한 후 main과 develop branch에 최종 버전을 병합
{% endhint %}

```bash
// 로컬 저장소에 원격 저장소에서 변경된 부분을 가져와야 할 경우
$ git fetch origin develop
$ git merge FETCH_HEAD
```

### 기관 레포 생성할 경우

{% hint style="info" %}
1. 팀장은 팀원에게 Admin 권한을 부여한다.
2. 팀원은 레포 fork 후 기관 레포에 바로 push하여 대참사가 나는 것을 방지하기 위해 아래와 같이 upstream push 주소를 삭제한다.
{% endhint %}

```bash
git remote set-url upstream --push no_push
```

##
