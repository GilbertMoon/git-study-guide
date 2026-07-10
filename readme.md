# Public Repository Fork, Clone, Pull Request 실습 가이드

## 실습 목표

교수자가 공개한 GitHub Public Repository를 자신의 계정으로 Fork한 뒤, 로컬 컴퓨터에 Clone하여 파일을 작성합니다.

작성한 파일을 자신의 GitHub 저장소에 Push하고, 교수자의 원본 저장소로 Pull Request를 생성합니다.

전체 작업 흐름은 다음과 같습니다.

```text
교수자 원본 저장소
        ↓ Fork
학생 GitHub 저장소
        ↓ Clone
학생 로컬 컴퓨터
        ↓ 파일 작성
Commit
        ↓
Push
        ↓
Pull Request
        ↓
교수자 확인 및 Merge
        ↓
Pull로 최신 내용 반영
```

---

# 1. 교수자 Public Repository 접속

교수자가 안내한 GitHub Repository 주소에 접속합니다.

예시:

```text
https://github.com/teacher-account/student-profile
```

저장소가 Public으로 설정되어 있으면 누구나 내용을 확인하고 Clone할 수 있습니다.

하지만 교수자의 원본 저장소에 직접 Push할 권한은 일반적으로 없습니다.

따라서 먼저 저장소를 자신의 GitHub 계정으로 Fork해야 합니다.

---

# 2. 원본 Repository Fork하기

원본 Repository 화면 오른쪽 위의 `Fork` 버튼을 클릭합니다.

```text
Fork
```

다음 화면에서 자신의 GitHub 계정을 선택합니다.

저장소 이름은 특별한 이유가 없다면 원본 이름을 그대로 사용합니다.

```text
student-profile
```

`Create fork` 버튼을 클릭합니다.

Fork가 완료되면 주소가 자신의 GitHub 계정으로 변경됩니다.

예시:

```text
원본 저장소
https://github.com/teacher-account/student-profile

Fork 저장소
https://github.com/student-account/student-profile
```

주소의 계정 이름이 자신의 GitHub 계정인지 반드시 확인합니다.

---

# 3. 자신의 Fork 저장소 Clone하기

자신의 Fork 저장소 화면에서 `Code` 버튼을 클릭합니다.

```text
Code
```

`HTTPS`가 선택되어 있는지 확인한 후 저장소 주소를 복사합니다.

예시:

```text
https://github.com/student-account/student-profile.git
```

주의할 점은 교수자의 원본 저장소가 아니라 자신의 Fork 저장소 주소를 복사해야 한다는 것입니다.

---

# 4. VS Code에서 Clone하기

VS Code를 실행합니다.

다음 단축키를 누릅니다.

```text
Ctrl + Shift + P
```

명령 팔레트에서 다음 항목을 검색합니다.

```text
Git: Clone
```

복사한 자신의 Fork 저장소 주소를 붙여 넣습니다.

```text
https://github.com/student-account/student-profile.git
```

저장할 폴더를 선택합니다.

Clone이 완료되면 다음 메시지가 나타날 수 있습니다.

```text
Open the cloned repository?
```

`Open`을 선택합니다.

---

# 5. 터미널에서 Clone하는 방법

VS Code의 Git Clone 기능 대신 터미널에서 직접 Clone할 수도 있습니다.

```bash
git clone https://github.com/student-account/student-profile.git
```

Clone이 완료되면 저장소 폴더로 이동합니다.

```bash
cd student-profile
```

현재 저장소가 자신의 Fork 저장소와 연결되어 있는지 확인합니다.

```bash
git remote -v
```

결과 예시는 다음과 같습니다.

```text
origin  https://github.com/student-account/student-profile.git (fetch)
origin  https://github.com/student-account/student-profile.git (push)
```

`origin` 주소에 자신의 GitHub 계정 이름이 표시되어야 합니다.

---

# 6. 작업 브랜치 만들기

팀 작업에서는 `main` 브랜치에서 직접 작업하기보다 별도의 브랜치를 만들어 작업하는 것이 좋습니다.

먼저 현재 브랜치를 확인합니다.

```bash
git branch
```

최신 내용을 가져옵니다.

```bash
git pull origin main
```

자신의 작업 브랜치를 생성합니다.

예시:

```bash
git switch -c profile/gildong
```

또는 다음과 같이 작성할 수 있습니다.

```bash
git switch -c add-profile-gildong
```

브랜치 이름에는 한글보다 영문 소문자와 하이픈 사용을 권장합니다.

---

# 7. 자기소개 HTML 파일 만들기

저장소에서 교수자가 지정한 폴더를 확인합니다.

예를 들어 다음 폴더에 파일을 작성한다고 가정합니다.

```text
profiles
```

파일명은 다음 형식을 사용합니다.

```text
본인이름_학번뒷자리.html
```

예시:

```text
홍길동_123.html
```

Public Repository에는 전체 학번을 작성하지 않는 것이 좋습니다.

학번 뒷자리 3자리 또는 교수자가 지정한 식별번호를 사용합니다.

파일 내용 예시는 다음과 같습니다.

```html
<!DOCTYPE html>
<html lang="ko">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>홍길동 프로필</title>
</head>
<body>
    <h1>홍길동</h1>

    <p>안녕하세요. 컴퓨터공학을 전공하고 있는 홍길동입니다.</p>

    <h2>관심 분야</h2>
    <ul>
        <li>Python</li>
        <li>인공지능</li>
        <li>웹 개발</li>
    </ul>

    <h2>이번 수업의 목표</h2>
    <p>Git과 GitHub를 활용하여 팀 개발 과정을 익히는 것이 목표입니다.</p>
</body>
</html>
```

다음 개인정보는 작성하지 않습니다.

* 전체 학번
* 전화번호
* 개인 이메일 주소
* 집 주소
* 비밀번호
* API Key
* 주민등록번호
* 기타 민감한 개인정보

---

# 8. 작성한 파일 확인하기

VS Code에서 파일을 저장합니다.

```text
Ctrl + S
```

터미널에서 현재 변경 상태를 확인합니다.

```bash
git status
```

작성한 파일이 다음과 같이 표시되는지 확인합니다.

```text
Untracked files:
    profiles/홍길동_123.html
```

변경 내용을 확인할 때는 다음 명령어를 사용할 수 있습니다.

```bash
git diff
```

새로 생성한 파일은 `git add` 전에는 `git diff`에 내용이 표시되지 않을 수 있습니다.

---

# 9. 파일을 Staging Area에 추가하기

작성한 파일만 선택하여 추가합니다.

```bash
git add profiles/홍길동_123.html
```

모든 변경 파일을 한 번에 추가하려면 다음 명령어를 사용할 수 있습니다.

```bash
git add .
```

다시 상태를 확인합니다.

```bash
git status
```

파일이 다음 영역에 표시되면 정상입니다.

```text
Changes to be committed
```

---

# 10. Commit 만들기

Commit 메시지는 작업 내용을 알아볼 수 있도록 작성합니다.

```bash
git commit -m "홍길동 프로필 페이지 추가"
```

좋은 Commit 메시지 예시는 다음과 같습니다.

```text
홍길동 프로필 페이지 추가
학생 자기소개 HTML 작성
프로필 페이지 관심 분야 수정
```

다음과 같이 의미가 불분명한 메시지는 피하는 것이 좋습니다.

```text
수정
완료
최종
테스트
```

Commit이 완료되었는지 확인합니다.

```bash
git log --oneline
```

---

# 11. 자신의 Fork 저장소에 Push하기

현재 브랜치를 자신의 GitHub Fork 저장소에 Push합니다.

```bash
git push -u origin profile/gildong
```

브랜치 이름을 다르게 만들었다면 실제 브랜치 이름을 사용합니다.

예시:

```bash
git push -u origin add-profile-gildong
```

`-u` 옵션은 현재 로컬 브랜치와 원격 브랜치를 연결합니다.

처음 한 번 연결한 이후에는 다음 명령어만 사용할 수 있습니다.

```bash
git push
```

GitHub 로그인 창이 나타나면 브라우저에서 인증을 진행합니다.

---

# 12. GitHub에서 Push 결과 확인하기

자신의 Fork 저장소 페이지로 이동합니다.

```text
https://github.com/student-account/student-profile
```

상단의 브랜치 선택 메뉴에서 자신이 Push한 브랜치를 확인합니다.

예시:

```text
profile/gildong
```

작성한 HTML 파일이 정상적으로 올라갔는지 확인합니다.

---

# 13. Pull Request 생성하기

Push가 완료되면 GitHub 저장소 화면에 다음과 유사한 버튼이 나타날 수 있습니다.

```text
Compare & pull request
```

해당 버튼을 클릭합니다.

버튼이 보이지 않으면 다음 절차로 진행합니다.

1. 자신의 Fork 저장소에서 `Pull requests` 메뉴를 클릭합니다.
2. `New pull request`를 클릭합니다.
3. 원본 저장소와 자신의 브랜치를 선택합니다.

Pull Request 방향은 다음과 같아야 합니다.

```text
base repository
교수자의 원본 저장소

base branch
main

head repository
학생의 Fork 저장소

compare branch
profile/gildong
```

정리하면 자신의 작업 브랜치 내용을 교수자의 원본 저장소 `main` 브랜치에 반영해 달라고 요청하는 것입니다.

---

# 14. Pull Request 내용 작성하기

Pull Request 제목은 작업 내용을 명확하게 작성합니다.

예시:

```text
홍길동 자기소개 프로필 추가
```

설명에는 다음 내용을 작성합니다.

```markdown
## 작업 내용

- 홍길동 자기소개 HTML 파일을 추가했습니다.
- 파일명: `profiles/홍길동_123.html`
- 전공, 관심 분야, 수업 목표를 작성했습니다.

## 확인 사항

- 전체 학번과 개인정보를 작성하지 않았습니다.
- HTML 파일이 정상적으로 열리는 것을 확인했습니다.
```

작성 후 `Create pull request` 버튼을 클릭합니다.

---

# 15. 교수자의 검토 기다리기

Pull Request가 생성되면 교수자가 다음 내용을 확인합니다.

* 파일명이 형식에 맞는지
* 지정된 폴더에 파일을 작성했는지
* HTML 문법에 문제가 없는지
* 개인정보가 포함되지 않았는지
* 다른 학생의 파일을 수정하지 않았는지
* Commit 메시지가 적절한지

수정이 필요한 경우 Pull Request 화면에 의견이 작성될 수 있습니다.

---

# 16. Pull Request 수정 요청 반영하기

교수자가 수정 요청을 남겼다면 새로운 Pull Request를 만들 필요가 없습니다.

기존 작업 브랜치에서 파일을 수정합니다.

```bash
git switch profile/gildong
```

파일을 수정한 뒤 상태를 확인합니다.

```bash
git status
git diff
```

수정 사항을 Commit합니다.

```bash
git add profiles/홍길동_123.html
git commit -m "프로필 페이지 수정 요청 반영"
```

다시 Push합니다.

```bash
git push
```

추가로 Push한 Commit은 기존 Pull Request에 자동으로 반영됩니다.

---

# 17. Pull Request Merge 확인하기

교수자가 Pull Request를 승인하고 병합하면 다음과 같은 상태가 표시됩니다.

```text
Merged
```

이제 학생의 프로필 파일이 교수자의 원본 Repository에 포함됩니다.

원본 저장소에서 파일이 정상적으로 추가되었는지 확인합니다.

---

# 18. 원본 저장소 최신 내용 가져오기

Pull Request가 병합된 이후에는 교수자의 원본 저장소에 다른 학생들의 파일도 계속 추가될 수 있습니다.

자신의 Fork 저장소와 로컬 저장소를 최신 상태로 맞추려면 원본 저장소를 `upstream`으로 등록하는 것이 좋습니다.

현재 원격 저장소를 확인합니다.

```bash
git remote -v
```

교수자의 원본 저장소를 `upstream`이라는 이름으로 추가합니다.

```bash
git remote add upstream https://github.com/teacher-account/student-profile.git
```

등록 결과를 확인합니다.

```bash
git remote -v
```

결과 예시는 다음과 같습니다.

```text
origin    https://github.com/student-account/student-profile.git
upstream  https://github.com/teacher-account/student-profile.git
```

여기서 각 이름의 의미는 다음과 같습니다.

```text
origin
학생 자신의 Fork 저장소

upstream
교수자의 원본 저장소
```

---

# 19. 교수자 원본 저장소 내용 Pull하기

먼저 `main` 브랜치로 이동합니다.

```bash
git switch main
```

교수자의 원본 저장소에서 최신 내용을 가져옵니다.

```bash
git pull upstream main
```

이제 로컬 `main` 브랜치에 교수자의 최신 내용이 반영됩니다.

자신의 Fork 저장소에도 반영하려면 다음 명령어를 실행합니다.

```bash
git push origin main
```

전체 흐름은 다음과 같습니다.

```bash
git switch main
git pull upstream main
git push origin main
```

---

# 20. 작업 브랜치 삭제하기

Pull Request가 병합된 이후에는 사용한 작업 브랜치를 삭제할 수 있습니다.

로컬 브랜치를 삭제합니다.

```bash
git branch -d profile/gildong
```

GitHub 원격 브랜치를 삭제합니다.

```bash
git push origin --delete profile/gildong
```

브랜치를 삭제하더라도 병합된 파일과 Commit 기록은 원본 저장소에 남아 있습니다.

---

# 21. 전체 실습 명령어 정리

## 처음 한 번만 수행하는 작업

```bash
git clone https://github.com/student-account/student-profile.git
cd student-profile

git remote add upstream https://github.com/teacher-account/student-profile.git
git remote -v
```

## 파일

## 프로필 페이지 작성용 프롬프트
자기소개 웹페이지를 HTML 파일 하나로 만들어 주세요.

아래 조건을 모두 반영해 주세요.

## 기본 정보

* 이름: 홍길동
* 소속: 예) 컴퓨터공학과
* 관심 분야: 예) Python, 인공지능, 데이터 분석, 웹 개발
* 취미: 예) 독서, 음악 감상, 여행
* 한 줄 소개: 예) 새로운 기술을 배우고 직접 만들어 보는 것을 좋아합니다.
* 수업 참여 목표: 예) Git과 GitHub를 활용한 협업 과정을 익히고 싶습니다.

위 예시 내용은 자신의 정보에 맞게 수정해 주세요.

## 페이지 구성

하나의 자기소개 페이지 안에 다음 내용을 포함해 주세요.

1. 상단 프로필 영역

   * 이름
   * 소속
   * 한 줄 소개
   * 프로필 이미지 영역
   * 실제 사진이 없다면 Bootstrap Icons 또는 기본 프로필 아이콘 사용

2. 자기소개 영역

   * 자신에 대한 간단한 소개 문장
   * 3~5문장 정도로 작성

3. 관심 분야 영역

   * 관심 기술이나 분야를 카드 또는 배지 형태로 표시
   * 예: Python, AI, 데이터 분석, 웹 개발

4. 보유 기술 또는 학습 중인 기술

   * Bootstrap Progress Bar 또는 Badge를 활용
   * 기술 수준은 과장하지 않고 입문, 학습 중, 활용 가능 등으로 표현

5. 취미와 관심사

   * 취미 또는 평소 관심 있는 내용을 3개 이상 표시

6. 이번 수업의 목표

   * Git과 GitHub를 통해 배우고 싶은 내용
   * 팀 프로젝트에서 기대하는 점
   * 앞으로 만들어 보고 싶은 프로젝트

7. 연락처 또는 링크 영역

   * GitHub 주소를 입력할 수 있는 영역
   * 이메일은 선택사항
   * 실제 개인정보를 공개하고 싶지 않다면 예시 주소나 비공개 문구 사용

8. 하단 Footer

   * 이름
   * 제작 연도
   * 간단한 문구

## 디자인 조건

* Bootstrap 5 CDN을 사용해 주세요.
* Bootstrap Icons CDN도 사용해 주세요.
* 별도의 CSS 파일과 JavaScript 파일을 만들지 마세요.
* 필요한 CSS는 HTML 파일 내부의 `<style>` 태그에 작성해 주세요.
* 필요한 JavaScript는 HTML 파일 내부의 `<script>` 태그에 작성해 주세요.
* HTML 파일 하나만 실행해도 완성된 페이지가 나타나야 합니다.
* 반응형 웹으로 작성해 주세요.
* PC와 모바일 화면에서 모두 자연스럽게 보이도록 작성해 주세요.
* 전체 디자인은 깔끔하고 전문적인 포트폴리오 스타일로 만들어 주세요.
* 색상은 파란색 또는 남색 계열을 기본으로 사용해 주세요.
* 카드, 배지, 버튼, 아이콘을 적절히 사용해 주세요.
* 지나치게 많은 애니메이션은 사용하지 마세요.
* 메뉴를 클릭하면 해당 영역으로 부드럽게 이동하도록 구성해 주세요.

## 기술 조건

* HTML5 문서 형식을 사용해 주세요.
* `<html lang="ko">`를 사용해 주세요.
* 한글이 깨지지 않도록 UTF-8 설정을 포함해 주세요.
* 모바일 대응을 위한 viewport 설정을 포함해 주세요.
* Bootstrap CDN은 인터넷에서 바로 불러오는 방식으로 작성해 주세요.
* Bootstrap 외의 별도 프레임워크는 사용하지 마세요.
* 모든 코드는 하나의 HTML 코드 블록으로 제공해 주세요.
* 설명은 작성하지 말고 완성된 HTML 코드만 출력해 주세요.
* 코드 일부를 생략하지 마세요.
* `...`, `생략`, `이하 동일`과 같은 표현을 사용하지 마세요.

## 개인정보 주의사항

이 페이지는 Public GitHub Repository에 공개될 수 있습니다.

다음 정보는 포함하지 마세요.

* 전체 학번
* 전화번호
* 집 주소
* 주민등록번호
* 비밀번호
* API Key
* Access Token
* 데이터베이스 접속 정보
* 공개를 원하지 않는 개인 이메일

파일명은 다음 형식으로 저장할 예정입니다.

```text
본인이름_학번뒷자리.html
```

예시:

```text
홍길동_123.html
```

위 조건을 모두 만족하는 완성된 자기소개 페이지 HTML 코드를 작성해 주세요.

