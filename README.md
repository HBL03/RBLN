# Study of RBLN ATOM NPU on VIPLab

VIPLab에서 수행하는 Rebellions ATOM NPU 연구 과제를 정리하는 문서 사이트입니다.

## 🎯 프로젝트 개요

이 프로젝트는 Hugo 정적 사이트 생성기와 Hextra 테마를 사용하여 연구 내용을 체계적으로 문서화합니다.

### 주요 특징

- 📝 **마크다운 기반**: 간편한 문서 작성
- 🎨 **모던한 디자인**: Hextra 테마 사용
- 🌙 **다크모드**: 눈의 피로 감소
- 🔍 **전문 검색**: FlexSearch 통합
- 🇰🇷 **한국어 지원**: 완전한 한글 지원
- 📱 **반응형**: 모바일 친화적
- ⚡ **빠른 로딩**: 정적 사이트의 장점

## 🛠️ 기술 스택

- **정적 사이트 생성기**: [Hugo](https://gohugo.io/) v0.148.2 (Extended)
- **테마**: [Hextra](https://imfing.github.io/hextra/)
- **폰트**: 
  - 본문: Spoqa Han Sans Neo
  - 코드: D2Coding
- **배포**: GitHub Pages
- **CI/CD**: GitHub Actions

## 📦 설치 및 실행

### 필수 요구사항

- Hugo (extended version) v0.148.2+
- Go v1.22.7+
- Git

### 로컬 개발 환경 설정

```powershell
# 저장소 클론
git clone https://github.com/username/repository-name.git
cd repository-name

# Submodule 초기화 (Hextra 테마)
git submodule update --init --recursive

# 개발 서버 실행
hugo server --buildDrafts --disableFastRender
```

브라우저에서 `http://localhost:1313/` 접속

## 📚 문서

- [**SETUP.md**](SETUP.md): 프로젝트 구축 및 설정 가이드
- [**DEPLOY.md**](DEPLOY.md): GitHub Pages 배포 가이드

## 🚀 빠른 시작

### 새 문서 작성

```powershell
# docs 섹션에 새 페이지 추가
hugo new content/docs/새-문서.md
```

### 콘텐츠 작성

```markdown
---
title: 문서 제목
draft: false
weight: 1
---

# 내용 작성

마크다운 문법으로 작성...
```

### 로컬 미리보기

```powershell
hugo server --buildDrafts
```

### 배포

```powershell
git add .
git commit -m "Update content"
git push origin main
```

## 📂 프로젝트 구조

```
.
├── .github/workflows/   # GitHub Actions
├── assets/css/          # 커스텀 CSS
├── content/             # 마크다운 콘텐츠
│   ├── _index.md       # 홈
│   ├── about.md        # 소개
│   └── docs/           # 문서
├── layouts/             # 커스텀 레이아웃
├── static/fonts/        # 폰트 파일
├── themes/hextra/       # Hextra 테마
├── hugo.yaml           # Hugo 설정
├── SETUP.md            # 구축 가이드
└── DEPLOY.md           # 배포 가이드
```

## 🎨 커스터마이징

### 폰트 변경

`assets/css/custom.css` 파일에서 폰트를 수정할 수 있습니다.

### 메뉴 수정

`hugo.yaml` 파일의 `menu` 섹션에서 네비게이션을 수정할 수 있습니다.

### 테마 색상

Hextra 테마는 Tailwind CSS를 사용합니다. 커스텀 색상은 CSS 변수로 오버라이드할 수 있습니다.

## 🔧 개발

### 빌드

```powershell
hugo --gc --minify
```

결과물은 `public/` 디렉토리에 생성됩니다.

### 테마 업데이트

```powershell
git submodule update --remote themes/hextra
```

## 📊 배포 현황

사이트는 GitHub Actions를 통해 자동으로 배포됩니다.

- 배포 URL: `https://username.github.io/repository-name/`
- 브랜치: `main`
- 빌드 도구: Hugo v0.148.2

## 🤝 기여

연구팀 내부 프로젝트입니다. 문서 추가 및 수정 시 Pull Request를 생성해주세요.

## 📝 라이선스

이 프로젝트는 연구 목적으로 사용됩니다.

## 👥 팀

VIPLab - Rebellions ATOM NPU 연구팀

## 🔗 관련 링크

- [Rebellions](https://rebellions.ai/)
- [Hugo 문서](https://gohugo.io/documentation/)
- [Hextra 테마 문서](https://imfing.github.io/hextra/)

---

*Last Updated: 2025년 10월*
