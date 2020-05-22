<a href="https://github.com/stevejkang/github-guideline"><img src="https://raw.githubusercontent.com/stevejkang/emoji-for-readme/master/emoji/triangular-ruler.png" align="right" width="90" height="90" /></a>

# github-guideline

  Personal github guideline about commit convention, git flow, issue/pull-request templates, etc.

 [![Last Commit](https://img.shields.io/github/last-commit/stevejkang/github-guideline.svg)](https://github.com/stevejkang/github-guideline/commits)

## 목차
  1. [Commit Convention](#1-commit-convention)
  2. Git Flow & Branch
  3. Pull Request
  4. Issue

## 1. Commit Convention

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

  > -m 옵션은 사용하지 않습니다.

#### 1.2.1. 언어

  누구나 봤을 때 이해할 수 있도록 영어로 작성하는 것을 권장합니다.

#### 1.2.2. 구성

  아래의 구성을 반드시 따라야 합니다.

  - 모든 줄은 문장으로 구성되며, 첫 문자는 대문자로, 첫 단어는 현재형 동사로, 마침표는 사용하지 않아야 합니다. 기타 기호 또는 특수문자(emoji 포함)는 필요한 경우를 제외하고는 사용을 권장하지 않습니다.
    - 예외사항
      - 메소드명 `getMessage()`
      - 파일명 `getMessage.js`
    - 예시
      - `Fix calculation in process.uptime()`

  - 세 줄 이상 작성해야 하고, 커밋의 두 번째 줄은 반드시 비워야 합니다. 세 번째 줄의 항목부터 상세 내용을 추가( `-`  + 내용)할 수 있습니다.
    - 예외사항
      - 오타 수정 `Fix typo`
    - 예시  
      ```
      Prevent multiple connection errors

      Catch error caused by network error
      - Use try catch expression
      ```

  - 이슈가 해결된 내용은 커밋 최하단에 `Fix #7`와 같은 용법으로 사용할 수 있습니다.

  - 커밋의 제목 또는 본문에 가장 먼저 나타나는 현재형 동사는 다음을 사용합니다.
    - **Fix** [기능수정]
      - `Fix A`: A 수정
      - `Fix A in B`: B의 A 수정
      - `Fix A which B/Fix A that B`: B인 A 수정
      - `Fix A to B/FIx A to be B`: B를 위해 A 수정 | B하기 위해 A 수정
      - `Fix A so that B`: A 수정해서 B (B 상태 강조)
      - `Fix A[issue|error|crash] where B`: B하는 A 수정
      - `Fix A when B`: B에 발생하는 A 수정
    - **Add** [코드추가/테스트추가/문서추가]
      - `Add A`: A 추가
      - `Add A for B`: B를 위한 A 추가
      - `Add A to B`: B에 A 추가
    - **Remove** [코드삭제]
      > 보통 (unnecessary|useless|unneeded|unused|duplicated) + A 형태  
      - `Remove A`: A 삭제
      - `Remove A from B`: B에서 A 삭제
    - **Use** [사용]
      - `Use A`: A 사용
      - `Use A for B`: B를 위한 A 사용
      - `Use A to B`: B에 A 사용 (to-부정사 B 가능)
      - `Use A in B`: B에 A 사용 (B 내부에서 A 사용)
      - `Use A instead of B`: B 대신에 A 사용
    - **Apply** [적용]
      - `Apply A`: A 적용
      - `Apply A to B`: B에 A 적용
    - **Refactor** [리팩토링(행위/기능/메소드)]
      - `Refactor A`: A 리팩토링
    - **Simplify** [단순화(행위/기능/메소드)]
      - `Simplify A`: A 단순화
    - **Update** [문서/리소스 버전 업]
      - `Update A`: A 최신화
      - `Update A to B`: A를 B로 최신화
      - `Update A for B`: B를 위한 A 업데이트
    - **Improve**/**Enhance** [향상/개선(테스트/커버리지/성능)]
      - `Improve A`: A 향상
    - **Make** [동작 변경]
      - `Make A B`: A를 B하게 하다(to-부정사 B) | A를 B로 만들다
    - **Implement** [Add 보다 큰 구현]
      - `Implement A`: A 구현
      - `Implement A to B`: B에 A 구현
    - **Correct** [문법/타입 등을 맞도록 수정]
      - `Correct A`: A를 맞게 하다
    - **Ensure**/**Make sure** [검증]
      - `Ensure A`: A를 확실하게 하다
    - **Prevent** [접근제한]
      - `Prevent A`: A를 막다
      - `Prevent A from B`: A를 B하지 못하게 막다.
    - **Avoid** [(조건등을) 피하다]
      - `Avoid A`: A를 피하다.
      - `Avoid A if B/Avoid A when B`: B일 때 A에 걸리지 않도록 하다.
    - **Move** [문서/코드 이동]
      - `Move A to B/Move A into B`:
    - **Rename** [(파일/메소드의) 이름 수정]
      - `Rename A to B`: A를 B로 이름을 바꾸다.
    - **Allow** [허용]
      - `Allow A to B`: A가 B할 수 있도록 허용
    - **Verify** [검증]
      - `Verify A`: A를 검증
    - **Set** [변수 등 설정]
      - `Set A to B`: A를 B로 설정
    - **Pass** [파라메터]
      - `Pass A to B`: A를 B로 넘기다
    - **Disable** [비활성화]
      - `Disable A`: A를 비활성화 하다

## Reference

  - [좋은 git commit 메시지를 위한 영어 사전](https://blog.ull.im/engineering/2019/03/10/logs-on-git.html)

## License

  MIT

## Author

  stevejkang <iam@juneyoung.io>
