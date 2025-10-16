# Hugo + Hextra 프로젝트 구축 가이드

## 📋 필수 요구사항

- **Hugo (extended version)**: v0.148.2 이상
- **Go**: v1.22.7 이상
- **Git**: 최신 버전

### 현재 시스템 확인

```powershell
go version
hugo version
git --version
```

## 🚀 프로젝트 구조

```
.
├── .github/
│   └── workflows/
│       └── hugo.yml          # GitHub Actions 워크플로우
├── assets/
│   └── css/
│       └── custom.css        # 커스텀 스타일 (폰트 설정)
├── content/
│   ├── _index.md            # 홈 페이지
│   ├── about.md             # 소개 페이지
│   └── docs/
│       └── _index.md        # 문서 메인 페이지
├── layouts/
│   └── partials/
│       └── custom-head.html  # 커스텀 헤드 (CSS 로드)
├── static/
│   └── fonts/
│       ├── d2coding/        # D2Coding 폰트
│       └── spoqa/           # SpoqaHanSansNeo 폰트
├── themes/
│   └── hextra/              # Hextra 테마 (Git submodule)
├── .gitignore
├── hugo.yaml                # Hugo 설정 파일
├── SETUP.md                 # 이 파일
└── DEPLOY.md                # 배포 가이드
```

## 📦 초기 설정 (이미 완료됨)

이 프로젝트는 이미 다음과 같이 구성되어 있습니다:

1. ✅ Hugo 사이트 초기화
2. ✅ Git 저장소 초기화
3. ✅ Hextra 테마 추가 (Git submodule)
4. ✅ 기본 설정 파일 작성 (hugo.yaml)
5. ✅ 커스텀 폰트 설정 (D2Coding, SpoqaHanSansNeo)
6. ✅ 기본 콘텐츠 페이지 생성
7. ✅ GitHub Actions 워크플로우 설정

## 🎨 커스텀 폰트

### 사용 중인 폰트

- **본문 폰트**: SpoqaHanSansNeo (Regular, Medium, Bold)
- **코드 폰트**: D2Coding

### 폰트 파일 위치

- `static/fonts/d2coding/`: D2Coding 폰트 파일
- `static/fonts/spoqa/`: SpoqaHanSansNeo 폰트 파일 (woff2 포맷)

### 폰트 적용 방식

1. `assets/css/custom.css`: 폰트 정의 및 스타일
2. `layouts/partials/custom-head.html`: CSS 로드

## 🔧 로컬 개발

### 개발 서버 실행

```powershell
hugo server --buildDrafts --disableFastRender
```

브라우저에서 `http://localhost:1313/` 접속

### 빌드 테스트

```powershell
hugo --gc --minify
```

빌드 결과는 `public/` 디렉토리에 생성됩니다.

## 📝 콘텐츠 작성

### 새 문서 페이지 추가

```powershell
# docs 섹션에 새 페이지 추가
hugo new content/docs/새-문서.md

# 다른 섹션에 페이지 추가
hugo new content/섹션명/페이지명.md
```

### Front Matter 설정

```yaml
---
title: 페이지 제목
draft: false
weight: 1  # 사이드바 순서 (docs 섹션에서)
---
```

## 🔄 테마 업데이트

Hextra 테마를 최신 버전으로 업데이트:

```powershell
git submodule update --remote themes/hextra
```

## ⚙️ 설정 수정

### hugo.yaml 주요 설정

- `baseURL`: GitHub Pages URL (배포 시 자동 설정됨)
- `title`: 사이트 제목
- `menu`: 네비게이션 메뉴 구성
- `params`: Hextra 테마 파라미터

### 사이트 제목 변경

`hugo.yaml` 파일에서:

```yaml
title: Study of RBLN ATOM NPU on VIPLab
```

## 🐛 트러블슈팅

### 테마가 로드되지 않는 경우

```powershell
# Submodule 초기화 및 업데이트
git submodule update --init --recursive
```

### 폰트가 적용되지 않는 경우

1. 브라우저 캐시 삭제
2. `assets/css/custom.css` 파일 경로 확인
3. Hugo 서버 재시작
4. 브라우저 개발자 도구에서 Network 탭 확인

### 빌드 오류

```powershell
# 캐시 삭제 후 재빌드
hugo --gc
```

## 📚 참고 링크

- [Hextra 공식 문서](https://imfing.github.io/hextra/)
- [Hugo 공식 문서](https://gohugo.io/documentation/)
- [GitHub Pages 문서](https://docs.github.com/en/pages)
- [D2Coding 폰트](https://github.com/naver/d2codingfont)
- [Spoqa Han Sans Neo](https://spoqa.github.io/spoqa-han-sans/)

## 📞 도움말

프로젝트 관련 문의사항이 있으면 이슈를 생성해주세요.
