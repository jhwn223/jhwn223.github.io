# Personal Data Science Site (Quarto)

해외 대학원 지원용 개인 사이트 뼈대입니다. About · Blog · Projects · CV 네 페이지로 구성되어 있어요.

## 폴더 구조

```
_quarto.yml          사이트 전체 설정 (이름, 메뉴, 링크, 테마)
index.qmd            About (첫 페이지)
blog.qmd             블로그 목록 (posts/ 안의 글이 자동으로 나열됨)
projects.qmd         프로젝트 목록 (projects/ 안의 페이지가 카드로 나열됨)
cv.qmd               이력서 페이지
posts/               블로그 글. 글 하나 = 폴더 하나 (index.qmd)
projects/            프로젝트 소개 페이지
files/               프로필 사진, CV PDF 등
.github/workflows/   GitHub에 push하면 자동 배포
```

## 1. 처음 설치 (한 번만)

1. Quarto 설치: https://quarto.org/docs/get-started/
2. Python 패키지 설치:
   ```bash
   python -m venv .venv
   source .venv/bin/activate        # Windows: .venv\Scripts\activate
   pip install -r requirements.txt
   ```
3. 미리보기:
   ```bash
   quarto preview
   ```
   브라우저가 열리고, 파일을 저장할 때마다 자동으로 새로고침됩니다.

## 2. 내 정보로 바꾸기

전체 검색으로 아래 값을 찾아 바꾸세요.

- `Your Name` → 영문 이름
- `YOUR-GITHUB-ID` → GitHub 아이디
- `YOUR-LINKEDIN-ID` → LinkedIn 주소
- `your.email@example.com` → 이메일
- `files/profile.png` → 본인 사진으로 교체
- `files/cv.pdf` → CV PDF 추가

## 3. GitHub Pages에 배포

1. GitHub에 `YOUR-GITHUB-ID.github.io` 이름으로 새 레포를 만들고 이 폴더를 push합니다.
2. 처음 한 번은 로컬에서 실행: `quarto publish gh-pages`
   (gh-pages 브랜치가 만들어집니다)
3. 레포 Settings → Pages → Source를 **Deploy from a branch**, 브랜치를 **gh-pages / (root)** 로 설정.
4. 이후에는 `main`에 push만 하면 GitHub Actions가 자동 배포합니다.

> ⚠️ 코드가 있는 글은 **로컬에서 `quarto render` 후** `_freeze/` 폴더까지 같이 커밋하세요.
> GitHub Actions는 코드를 다시 실행하지 않고 저장된 결과만 사용합니다.

## 4. 새 글 쓰기

1. `posts/2026-11-01-why-this-method/` 폴더를 복사해서 `posts/YYYY-MM-DD-제목/` 으로 이름 변경
2. `index.qmd`의 제목, 날짜, 카테고리 수정
3. 작성 중에는 `draft: true` → 완성되면 `false`
4. 대표 이미지를 쓰려면 폴더 안에 `thumbnail.png`를 넣으세요.

템플릿 글은 이 구조를 따릅니다:
**TL;DR → 질문 → 데이터 → 고려한 방법들 → 선택과 이유 → 결과 → 트레이드오프 → So what? → 회고**

## 5. 개인 도메인 (선택)

도메인을 산 뒤 레포 Settings → Pages → Custom domain에 입력하고,
`_quarto.yml`의 `site-url`도 같은 주소로 바꾸세요.
