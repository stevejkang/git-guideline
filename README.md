<a href="https://github.com/stevejkang/github-guideline"><img src="https://raw.githubusercontent.com/stevejkang/emoji-for-readme/master/emoji/triangular-ruler.png" align="right" width="90" height="90" /></a>

# github-guideline

  Personal github guideline about commit convention, git flow, issue/pull-request templates, etc.

  [![Last Commit](https://img.shields.io/github/last-commit/stevejkang/github-guideline.svg)](https://github.com/stevejkang/github-guideline/commits)
  [![Hits](https://hits.seeyoufarm.com/api/count/incr/badge.svg?url=https%3A%2F%2Fgithub.com%2Fstevejkang%2Fgithub-guideline)](https://github.com/stevejkang/github-guideline)

## Table of Contents
  1. [Commit Convention](#1-commit-convention)
  2. [Git Flow & Branch](#2-git-flow--branch)
  3. [Issue](#3-issue)
  4. [Pull Request](#4-pull-request)
  5. [Actions](#5-actions)
  6. [Wiki](#6-wiki)
  7. [Troubleshooting](#7-troubleshooting)
  8. [이제 뭘하면 되나요?](#8-so-what-should-i-do)

## 1. Commit Convention
> [상단으로 ⬆️](#github-guideline)  

### 1.1. 커밋의 정의

#### 1.1.1. 작성자

  커밋은 작업자가 직접 작업한 내용에 대해 커밋을 합니다.

#### 1.1.2. 단위

  커밋은 작업 하나의 단위가 되어야 합니다. 행동 하나의 단위가 되어서는 안됩니다.  
  예를 들어, `Case A`는 가능하지만 `Case B`는 커밋의 단위로 권장하지 않습니다.

  - `Case A`
    - CLI로 Vue.js 프로젝트를 설치한 경우
    - 오타를 고친 경우
    - 여러 개의 Dependency를 설치하여 프로젝트 기반을 만든 경우
    - 하나 이상의 Dependency를 설치하고 프로젝트 어딘가에 정의, 적용한 경우
  - `Case B`
    - Dependency를 설치한 경우

#### 1.1.3. 조건

  커밋은 임시로 저장 해두기 위한 장치로 사용해서는 안됩니다. 즉, 모든 커밋은 개발 당시에 완결된 코드만이 올라가야 합니다.

### 1.2. 커밋 메세지

  > 여러 줄의 커밋 메시지를 권장합니다. (`-m`으로 작성되는 single-line 커밋을 권장하지 않습니다.)

#### 1.2.1. 언어

  누구나 봤을 때 이해할 수 있도록 영어로 작성하는 것을 권장합니다.

  > 어디까지나 권장일 뿐, 강제 사항은 아니며, 사내에서 사용하는 경우나 필요에 따라서는 사용하기 편한 언어로 서술하는 게 전달이 명확한 경우도 있습니다.

#### 1.2.2. 구성

  아래의 구성을 반드시 따라야 합니다.

  - 기본 구성은 다음과 같습니다. 

    > `<?>`는 optional field를 의미합니다.  

    ```
    <Commit Title>
    
    <Commit Body>
    - <?Commit Detail>
    <Commit Footer>
    ```    

  - 모든 줄은 문장으로 구성되며, 첫 문자는 대문자로, 첫 단어는 현재형 동사로, 마침표는 사용하지 않아야 합니다. 기타 기호 또는 특수문자(emoji 포함)는 필요한 경우를 제외하고는 사용을 권장하지 않습니다.
    - 예외사항
      - 메소드명 `getMessage()`
      - 파일명 `getMessage.js`
    - 예시
      - `Fix calculation in process.uptime()`

  - 세 줄 이상 작성해야 하고, 커밋의 두 번째 줄은 반드시 비워야 합니다. 세 번째 줄의 항목부터 상세 내용을 추가( `-` + 내용)할 수 있습니다.
    - 예외사항
      - 오타 수정 `Fix typo`
    - 예시  
      ```
      Prevent multiple connection errors

      Catch error caused by network error
      - Use try catch expression
      ```

  - 이슈가 해결된 내용은 커밋 최하단에 `Fix #7`와 같은 용법으로 사용할 수 있습니다.
    > 또는 PR로 올라갈 커밋이 아니라면 간단히 메세지 뒤에 `(#7)`과 같이 reference 할 수 있습니다.

  - 커밋의 제목 또는 본문에 가장 먼저 나타나는 현재형 동사는 다음을 사용합니다.
    - **Fix** [기능수정]
      - `Fix A`: A 수정
      - `Fix A in B`: B의 A 수정
      - `Fix A which B/Fix A that B`: B인 A 수정
      - `Fix A to B/Fix A to be B`: B를 위해 A 수정 | B하기 위해 A 수정
      - `Fix A so that B`: A 수정해서 B (B 상태 강조)
      - `Fix A[issue|error|crash] where B`: B하는 A 수정
      - `Fix A when B`: B에 발생하는 A 수정
    - **Add** [추가(코드/테스트/문서)]
      - `Add A`: A 추가
      - `Add A for B`: B를 위한 A 추가
      - `Add A to B`: B에 A 추가
    - **Remove** [삭제(코드/문서)]
      > 보통 (unnecessary|useless|unneeded|unused|duplicated) + A 형태  
      - `Remove A`: A 삭제
      - `Remove A from B`: B에서 A 삭제
    - **Use** [사용]
      - `Use A`: A 사용
      - `Use A for B`: B를 위한 A 사용
      - `Use A to B`: B에 A 사용 (to-부정사 B 허용)
      - `Use A in B`: B에 A 사용 | B 내부에서 A 사용
      - `Use A instead of B`: B 대신에 A 사용
    - **Apply** [적용]
      - `Apply A`: A 적용
      - `Apply A to B`: B에 A 적용
    - **Refactor** [리팩토링(행위/기능/메소드)]
      - `Refactor A`: A 리팩토링
    - **Simplify** [단순화(행위/기능/메소드)]
      - `Simplify A`: A 단순화
    - **Update** [업데이트/버전 업(문서/리소스)]
      - `Update A`: A 최신화
      - `Update A to B`: A를 B로 최신화
      - `Update A for B`: B를 위한 A 업데이트
    - **Change** [변경]
      - `Change A`: A 변경
      - `Change A into B`: A를 B로 변경
    - **Improve**/**Enhance** [향상/개선(테스트/커버리지/성능)]
      - `Improve A`: A 향상
    - **Make** [동작 변경]
      - `Make A B`: A를 B하게 하다 (to-부정사 B 허용) | A를 B로 만들다
    - **Implement** [Add 보다 큰 구현]
      - `Implement A`: A 구현
      - `Implement A to B`: B에 A 구현
    - **Correct** [(문법/타입 등을) 맞도록 수정]
      - `Correct A`: A를 맞게 하다
    - **Ensure**/**Make sure** [검증]
      - `Ensure A`: A를 확실하게 하다
    - **Prevent** [접근제한]
      - `Prevent A`: A를 막다
      - `Prevent A from B`: A를 B하지 못하게 막다
    - **Avoid** [(조건 등을) 피하다]
      - `Avoid A`: A를 피하다.
      - `Avoid A if B/Avoid A when B`: B일 때 A에 걸리지 않도록 하다
    - **Move** [이동(코드/문서)]
      - `Move A to B/Move A into B`: A를 B로 이동하다
    - **Rename** [이름 수정(코드/문서/메소드)]
      - `Rename A to B`: A를 B로 이름을 바꾸다
    - **Allow** [허용]
      - `Allow A to B`: A가 B할 수 있도록 허용
    - **Verify** [검증]
      - `Verify A`: A를 검증
    - **Set** [설정(변수/값)]
      - `Set A to B`: A를 B로 설정
    - **Pass** [파라메터]
      - `Pass A to B`: A를 B로 넘기다
    - **Disable** [비활성화]
      - `Disable A`: A를 비활성화 하다
    - **Organize** [정리]
      - `Organize A`: A 정리

## 2. Git Flow & Branch
> [상단으로 ⬆️](#github-guideline)  

### 2.1. 개요

#### 2.1.1. 정의

  Git Flow는 버전 관리 시스템(Version Control System, VCS)의 한 종류인 git을 통해 효율적으로 프로젝트를 관리하고 배포하기 위한 전략이자 브랜칭 관리 전략(Branch Management Strategy) 입니다. 실제 프로덕트를 개발하고 지속적으로 배포하는 조직에서 권장되는 방법이지만, 실제로 개발 조직에 적용하는 방식은 각기 다를 수 있습니다.

  > 아래에서는 Best Practice를 담으려 노력하였으나, 조직과 프로젝트의 성격에 맞게 조정이 필요할 수 있습니다.

  이 섹션에서 말하는 Branch는 Git Flow의 브랜칭 관리 전략을 따르는 브랜치에 대한 설명입니다. 따라서 기본적인 `git branch` 명령어에 대한 설명을 포함하지 않습니다. 즉, 기본적으로 branch를 만들고, 이동하며, 삭제하는 등의 기초지식이 요구됩니다.

### 2.2. 방법
  
  > Vincent Driessen이 제한한 Git Flow는 다음 [PDF](https://nvie.com/files/Git-branching-model.pdf)로 한 눈에 확인할 수 있습니다.

#### 2.2.1. 브랜치 전략

  Git Flow에서는 용도/환경에 따라 브랜치를 구분합니다. 메인 브랜치는 master, develop 브랜치가 해당되며, 그 외에 보조 브랜치는 feature, release, hotfix, bugfix 브랜치 등이 해당됩니다.

  - **master**  
  프로젝트의 뿌리가 되는 브랜치로, 해당 브랜치의 HEAD는 production 환경에 배포되었거나, 곧 배포될 예정임(production-ready)을 의미합니다. 실제 서비스에서는 실 서버와 sync가 맞아야 합니다.  
  master 브랜치에 반영 혹은 병합된다는 것은 새 버전이 배포됨을 의미합니다. 보통  실제 서버로 빌드 & 배포하는 스크립트가 작동합니다.

  - **develop**  
  다음 배포를 위해 개발되고 있는 코드가 위치하는 브랜치. 실제 서비스에서는 개발 서버 혹은 테스트 서버와 sync가 맞아야 합니다.  
  develop 브랜치가 안정화되고, 배포 기능이 완성되면, master로 병합됩니다.
  
    <table>
      <thead>
          <tr>
              <th colspan=3>브랜치 상세</th>
          </tr>
      </thead>
      <tbody>
          <tr>
              <td rowspan=3>develop</td>
              <td>시작브랜치</td>
              <td>master</td>
          </tr>
          <tr>
              <td>병합브랜치(방향/순서)</td>
              <td>master</td>
          </tr>
          <tr>
              <td>네이밍 규칙</td>
              <td>develop</td>
          </tr>
      </tbody>
    </table>

  - **feature**  
  feature 브랜치는 개발하고자 하는 기능을 개발하는 주축이 되는 브랜치입니다. 만약 애자일 방법론을 채택한 조직이라면, 스프린트 기간 중 하나의 스토리 혹은 하나의 에픽이 이에 해당할 수 있습니다.  
  이 브랜치는 성공적으로 develop에 병합되거나 필요성이 없어진 경우 삭제하여 관리할 수 있습니다.
  
    > 네이밍 규칙에서 `feature-*`가 본래 권장되는 형식이나, SourceTree 등 GUI 환경에서 폴더구조로 표시된다는 이점 때문에 `feature/*`로 사용하기도 합니다.

    <table>
      <thead>
          <tr>
              <th colspan=3>브랜치 상세</th>
          </tr>
      </thead>
      <tbody>
          <tr>
              <td rowspan=3>feature</td>
              <td>시작브랜치</td>
              <td>develop</td>
          </tr>
          <tr>
              <td>병합브랜치(방향/순서)</td>
              <td>develop / master</td>
          </tr>
          <tr>
              <td>네이밍 규칙</td>
              <td>feature-* 또는 feature/*</td>
          </tr>
      </tbody>
    </table>

  - **work**  
  개인별 작업을 위한 브랜치. 이는 Git Flow에 해당하는 내용은 아니지만, optional하게 사용할 수 있는 브랜치로, feature에서 분기되어 기능 개발에 사용되며, 작업자별 원활한 작업을 위해 만드는 것을 권장합니다.
  
    > 일부 조직에서는 fork의 형태로 repository를 분리하는 방법을 채택하기도 합니다.
  
    <table>
      <thead>
          <tr>
              <th colspan=3>브랜치 상세</th>
          </tr>
      </thead>
      <tbody>
          <tr>
              <td rowspan=3>work</td>
              <td>시작브랜치</td>
              <td>feature</td>
          </tr>
          <tr>
              <td>병합브랜치(방향/순서)</td>
              <td>feature / develop / master</td>
          </tr>
          <tr>
              <td>네이밍 규칙</td>
              <td>ex) steve-* 또는 steve/*</td>
          </tr>
      </tbody>
    </table>

  여기까지 정리해보면 전체적인 브랜치 분기의 depth를 가장 위의 계층부터 나타내면 아래와 같습니다.

    master -> develop -> feature/* -> work/*
  
  develop 브랜치에서는 여러 개의 feature 브랜치가 분기될 수 있으며, 하나의 feature 브랜치에는 여러개의 work 브랜치가 분기될 수 있습니다.

  아래는 release, hotfix, bugfix 브랜치로, 각각의 상황에 따라 사용되는 보조 브랜치입니다.

  - **release**  
  최종 프로덕션으로 올릴 상태가 되었을 때, 이를 master로 반영하기 직전에 생성되는 브랜치. 보통의 경우, develop은 master보다 업데이트 주기가 짧기 때문에, develop에서 작업 중인 한 시점에서 release 브랜치를 생성하여, 최종적인 릴리즈 준비를 할 수 있습니다.  
  이렇게 진행할 경우, 처음 release가 분기되고 그 이후에 develop에 업데이트 되는 내용들은 다음 release 브랜치가 분기될 때 반영하게 되어, 현재 분기된 release 브랜치에 한해 정확한 범위 내에 업데이트를 진행할 수 있게 됩니다.  
  이 브랜치가 master로 반영될 때, 태그를 이용해 버저닝(versioning)을 진행하는 것을 권장하며, 반영 후에는 develop에도 동일한 내용을 병합합니다.
  
    <table>
      <thead>
          <tr>
              <th colspan=3>브랜치 상세</th>
          </tr>
      </thead>
      <tbody>
          <tr>
              <td rowspan=3>release</td>
              <td>시작브랜치</td>
              <td>develop</td>
          </tr>
          <tr>
              <td>병합브랜치(방향/순서)</td>
              <td>master / develop</td>
          </tr>
          <tr>
              <td>네이밍 규칙</td>
              <td>release-* 또는 release/*</td>
          </tr>
      </tbody>
    </table>

  - **hotfix**  
  미리 계획되지 못한 배포를 위한 브랜치. 실제 프로덕션에 장애를 일으킬 정도의 크리티컬(critical)한 이슈가 발생되어 긴급히 수정해야 할 때 사용합니다.  
  이전 release 브랜치가 master에 반영된 시점(태그로 버저닝된 시점)에서 hotfix 브랜치를 분기하여 이를 master, develop 순으로 반영을 진행합니다.

    <table>
      <thead>
          <tr>
              <th colspan=3>브랜치 상세</th>
          </tr>
      </thead>
      <tbody>
          <tr>
              <td rowspan=3>hotfix</td>
              <td>시작브랜치</td>
              <td>master</td>
          </tr>
          <tr>
              <td>병합브랜치(방향/순서)</td>
              <td>master / develop</td>
          </tr>
          <tr>
              <td>네이밍 규칙</td>
              <td>hotfix-* 또는 hotfix/*</td>
          </tr>
      </tbody>
    </table>

  - **bugfix**  
  기존에 리포팅된 이슈 혹은 버그를 해결하기 위해 생성되는 브랜치. 보통 fix 브랜치라고 불리기도 하며, 서비스에 중대한 영향을 끼치진 않지만, 기능으로 분류될 수 없고, 버그라 판단되는 경우, 이를 서비스에 반영하기 위해 생성합니다.  
  보통 develop에서 분기되어 이를 develop, master 순으로 병합되며, 표면적으로는 feature 브랜치와 동일합니다.

    <table>
      <thead>
          <tr>
              <th colspan=3>브랜치 상세</th>
          </tr>
      </thead>
      <tbody>
          <tr>
              <td rowspan=3>bugfix</td>
              <td>시작브랜치</td>
              <td>develop</td>
          </tr>
          <tr>
              <td>병합브랜치(방향/순서)</td>
              <td>develop / master</td>
          </tr>
          <tr>
              <td>네이밍 규칙</td>
              <td>bugfix-* 또는 bugfix/*</td>
          </tr>
      </tbody>
    </table> 

### 2.3. 적용

#### 2.3.1. 일반적인 플로우

  이 섹션에서 말하는 '일반적인' 플로우란 릴리즈 혹은 핫픽스와 같은 상황을 제외한 가장 보편적인(common) 상황을 다룹니다. 조직에 따라 work(개인 작업) 브랜치 대신에 fork하여 사용할 수 있고, merge 대신 rebase를 택할 수도 있습니다. ([2.4.1. merge와 rebase 무엇이 정답일까?](#241-merge와-rebase-무엇이-정답일까) 참고)

  아래에서 제시하는 병합 플로우는 rebase와 merge를 동시에 하는 방법입니다. rebase 후에 fast-forward merge를 사용하여 깔끔한 브랜칭 전략을 권장하고 있습니다. 이 방법은 뒤에 나오는 [2.3.2. 릴리즈 플로우](#232-릴리즈-플로우)와 [2.3.3. 핫픽스 플로우](#233-핫픽스-플로우)에서도 동일하게 사용합니다.

  > WIP general flow

#### 2.3.2. 릴리즈 플로우

  > WIP release flow

#### 2.3.3. 핫픽스 플로우

  > WIP hotfix flow

### 2.4. 고민해볼 내용

#### 2.4.1. merge와 rebase 무엇이 정답일까?

  merge와 rebase의 가장 큰 차이는 병합 혹은 작업 내용이 합쳐질 때 이에 대한 커밋이 남는지에 있습니다. merge 커밋은 흔히 말하는 merge 커밋을 남기지만, rebase는 말그대로 base를 바꾸는 작업이기에 커밋이 남지 않습니다.
  
  > 기본적으로 그렇다는 것이지, 항상 그러하다고 할 수 없습니다. 커밋으로 구분하기 보다는, 그 원리의 차이를 이해하는 것이 중요합니다. 아래 예시로 확인할 수 있습니다.

  **merge**  
  feature/order에서 분기한 steve/pg 브랜치가 있다고 가정합니다.  
  > [feature/order] git commit -m "a"  
  > [feature/order] git commit -m "b"  
  > [feature/order] git checkout -b steve/pg  
  > [steve/pg] git commit -m "x"  
  > [steve/pg] git commit -m "y"

                    (a)     (b)
    feature/order   * ----- *
                             \
    steve/pg                  ----- * ----- *
                                    (x)     (y)

  위 상태에서 작업 내용을 feature/order로 병합하려 할 때, 만약 다른 팀원이 feature/order 브랜치에 반영한 내용이 없고, 분기 이후로 진행된 커밋이 없다는 것이 origin으로부터 확인되면, fast-forward merge 혹은 non-fast-forward merge를 진행할 수 있습니다.
  
  - fast-forward merge를 하면 다음과 같습니다.
    > [steve/pg] git checkout feature/order  
    > [feature/order] git merge --ff-only steve/pg

    > 이 경우에는 상위 브랜치에 변경사항이 없으므로 뒤에서 나올 rebase와 동일하게 사용할 수 있습니다. (아래에서 나올 예시와 다른 점은 상위 브랜치에서 하위 브랜치로 rebase 한다는 점입니다.)
      
        (a)     (b)
        * ----- *
                 \                    steve/pg
                  ----- * ----- *     feature/order 
                        (x)     (y)

    > 작업이 완료된 steve/pg 브랜치를 삭제하여 히스토리를 깔끔하게 유지할 수 있습니다.

  - non-fast-forward를 하면 다음과 같습니다. (m은 merge commit)
    > [steve/pg] git checkout feature/order  
    > [feature/order] git merge --no-ff steve/pg
      
                        (a)     (b)                     (m)
        feature/order   * ----- *                       * -----
                                 \                     /
        steve/pg                  ----- * ----- * -----
                                        (x)     (y)

    > 작업이 완료된 steve/pg 브랜치를 삭제하면 분기된 브랜치의 형태와 그 커밋은 유지되고 브랜치만 삭제됩니다.

  하지만, feature/order에 변경사항이 있고 rebase 한 적도 없는 경우, 실질적인 머지 커밋으로만 병합이 가능합니다. 이 때는 non-fast-forward merge와 fast-forward merge 모두 동일하게 커밋이 남게 됩니다.

  > [steve/pg] git checkout feature/order  
  > [feature/order] git merge steve/pg
    
                      (a)     (b)                     (m)
      feature/order   * ----- *                       * -----
                               \                     /
      steve/pg                  ----- * ----- * -----
                                      (x)     (y)

  > 작업이 완료된 steve/pg 브랜치를 삭제하면 분기된 브랜치의 형태와 그 커밋은 유지되고 브랜치만 삭제됩니다.

  **rebase**  
  리베이스는 병합(merge)한다는 개념과는 거리가 있지만, 브랜치의 base를 옮겨 다른 브랜치의 내용을 반영한다는 점에서는 비슷합니다. 
  
  rebase 작업을 하면서 가장 주의해야 할 것은 rebase 후에 그 rebase를 적용받은 커밋들은 commit hash가 바뀌게 됩니다. 즉, 그렇게 바뀐 커밋이 이미 remote(github 등) branch에 올라갔던 커밋이라면 해당 내용을 (불가피하게) force-push(`--force`) 해야 할 것이고, 누군가와 동일한 브랜치에서 협업을 하고 있다면 푸시 후 `git reset --hard origin/<branch>` 등으로 다시 로컬에 반영이 필요할 것입니다.
  
  결론적으로 개인 브랜치에서는 리베이스를 자유롭게 해도 무방하지만, 다양한 협업과 커밋이 짧은 주기로 이루어진다면 협업에 많은 주의가 필요합니다. (항상 up-stream 설정을 해두고 로컬의 상태를 최신화할 필요가 있습니다.)

  rebase는 보통 하위 브랜치에서 상위 브랜치를 rebase한다고 표현하며, 현재 브랜치가 "하위 브랜치", 바라보는/병합 브랜치가 "상위 브랜치"가 됩니다. 상위 브랜치의 변경사항을 모두 반영하여, 그 상위 브랜치를 기반(base)으로 하여 현재 브랜치의 base 이후 모든 커밋을 최신화한다는 의미를 가지고 있습니다.

  예를 들어, 기존의 상태가 다음과 같다면,

                    (a)     (b)
    feature/order   * ----- *
                             \
    steve/pg                  ----- * ----- *
                                    (x)     (y)

  steve/pg에서 feature/order 기준으로 rebase할 수 있습니다.

  > [steve/pg] git rebase feature/order  
  > f/o가 feature/order, s/p가 steve/pg 브랜치.  

     (a)    (b)     (x)     (y)
    * ----- * ----- * ----- *
            (f/o)           (s/p)

  이때, steve/pg에서 커밋했던 (x), (y) 커밋이 영향을 받습니다. 이미 remote에 올라갔다면 force push로 업데이트해야 합니다.

  만약 rebase에서 conflict가 난 경우(매우 빈번히 일어납니다.), 각 파일에서 conflict를 해결하고 rebase를 진행하면 됩니다. rebase는 진행 방법이 현재 브랜치의 커밋을 하나하나 탐색하며, 적용하는 방법이므로, 한 번 rebase를 할 때 각 커밋별로 여러번 해결해야 하는 경우도 있습니다.

  > [steve/pg] git rebase feature/order  
  > [steve/pg] [CONFLICT 발생]  
  > [steve/pg] git add [confilcted file]  
  > [steve/pg] git rebase --continue

## 3. Issue
> [상단으로 ⬆️](#github-guideline)  

## 4. Pull Request
> [상단으로 ⬆️](#github-guideline)  

## 5. Actions
> [상단으로 ⬆️](#github-guideline)  

## 6. Wiki
> [상단으로 ⬆️](#github-guideline)  

## 7. Troubleshooting
> [상단으로 ⬆️](#github-guideline)  

## 8. So, What should I do?
> [상단으로 ⬆️](#github-guideline)  

## Reference

  - [좋은 git commit 메시지를 위한 영어 사전](https://blog.ull.im/engineering/2019/03/10/logs-on-git.html)
  - [GIT을 기반으로 한 프로젝트 개발프로세스](https://gist.github.com/ihoneymon/a28138ee5309c73e94f9)
  - [A successful Git branching model](https://nvie.com/posts/a-successful-git-branching-model/)
  - [Merge Branch - Backlog](https://backlog.com/git-tutorial/integrating-branches/git-merge/)
  - [Rebase Branch - Backlog](https://backlog.com/git-tutorial/integrating-branches/rebase-branch/)

## License

  MIT

## Author

  stevejkang <iam@juneyoung.io>
