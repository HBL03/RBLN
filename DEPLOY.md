# GitHub Pages 배포 가이드

## 📋 사전 준비

1. GitHub 계정
2. GitHub 저장소 생성 (public 또는 private)
3. 로컬 저장소와 원격 저장소 연결

## 🚀 초기 배포 설정

### 1단계: GitHub 저장소 생성

1. GitHub에서 새 저장소 생성
   - 저장소 이름: 원하는 이름 (예: `rbln-npu-docs`)
   - Public 또는 Private 선택
   - README, .gitignore, license 추가 안함 (이미 로컬에 있음)

### 2단계: 로컬 저장소와 연결

```powershell
# 원격 저장소 추가 (username과 repository-name을 실제 값으로 변경)
git remote add origin https://github.com/username/repository-name.git

# 현재 변경사항 커밋
git add .
git commit -m "Initial commit: Hugo + Hextra setup"

# main 브랜치로 푸시
git branch -M main
git push -u origin main
```

### 3단계: GitHub Pages 설정

1. GitHub 저장소 페이지로 이동
2. **Settings** 탭 클릭
3. 왼쪽 메뉴에서 **Pages** 선택
4. **Source** 섹션에서:
   - Source: `GitHub Actions` 선택

### 4단계: hugo.yaml 설정 업데이트

배포 전에 `hugo.yaml` 파일의 `baseURL`을 업데이트하세요:

```yaml
baseURL: https://username.github.io/repository-name/
```

**주의**: 
- Organization 페이지: `https://orgname.github.io/`
- User 페이지: `https://username.github.io/`
- Repository 페이지: `https://username.github.io/repository-name/`

## 🔄 배포 프로세스

### 자동 배포

main 브랜치에 푸시하면 자동으로 배포됩니다:

```powershell
# 변경사항 추가
git add .

# 커밋
git commit -m "Update content"

# 푸시 (자동 배포 트리거)
git push origin main
```

### 배포 상태 확인

1. GitHub 저장소의 **Actions** 탭 클릭
2. 실행 중인 워크플로우 확인
3. 완료되면 사이트 URL로 접속

### 수동 배포

GitHub Actions 페이지에서:

1. **Actions** 탭 클릭
2. **Deploy Hugo site to Pages** 워크플로우 선택
3. **Run workflow** 버튼 클릭
4. **Run workflow** 확인

## 📝 배포 워크플로우 설명

`.github/workflows/hugo.yml` 파일이 배포를 담당합니다:

### 워크플로우 단계

1. **Hugo 설치**: Hugo extended v0.148.2 설치
2. **Go 설치**: Go 1.22 설치
3. **저장소 체크아웃**: 코드와 submodule 다운로드
4. **Hugo 빌드**: 정적 파일 생성
5. **GitHub Pages 배포**: 빌드된 파일 배포

### 트리거 조건

- `main` 브랜치에 푸시할 때
- 수동으로 워크플로우 실행할 때

## 🔧 배포 문제 해결

### 1. 테마가 로드되지 않는 경우

워크플로우 파일에서 submodule 체크아웃 확인:

```yaml
- name: 저장소 체크아웃
  uses: actions/checkout@v4
  with:
    submodules: recursive  # 이 옵션이 있는지 확인
    fetch-depth: 0
```

### 2. 404 오류

**원인**: baseURL이 잘못 설정됨

**해결**:
```yaml
# hugo.yaml
baseURL: https://username.github.io/repository-name/
```

Repository 이름과 일치하는지 확인하세요.

### 3. CSS나 폰트가 로드되지 않음

**원인**: 상대 경로 문제

**해결**:
- `hugo.yaml`의 `baseURL`이 올바른지 확인
- 폰트 경로가 `/fonts/...`로 시작하는지 확인
- 빌드 후 `public/` 디렉토리에 파일이 있는지 확인

### 4. 빌드 실패

**GitHub Actions 로그 확인**:

1. **Actions** 탭으로 이동
2. 실패한 워크플로우 클릭
3. 빌드 로그 확인
4. 오류 메시지 확인

**일반적인 오류**:
- Hugo 버전 불일치
- 마크다운 문법 오류
- Front matter 오류

## 🔄 콘텐츠 업데이트 워크플로우

### 일반적인 작업 흐름

```powershell
# 1. 새 브랜치 생성 (선택사항)
git checkout -b feature/new-content

# 2. 콘텐츠 수정 또는 추가
hugo new content/docs/new-page.md
# 파일 편집...

# 3. 로컬에서 테스트
hugo server --buildDrafts

# 4. 변경사항 커밋
git add .
git commit -m "Add new documentation page"

# 5. 푸시 (배포)
git push origin main
# 또는 feature 브랜치를 푸시하고 Pull Request 생성
```

### Draft 콘텐츠

개발 중인 콘텐츠는 `draft: true`로 설정:

```yaml
---
title: 작성 중인 문서
draft: true
---
```

로컬에서만 확인하고 싶을 때:
```powershell
hugo server --buildDrafts
```

배포 시에는 draft 콘텐츠가 제외됩니다.

## 🌐 커스텀 도메인 설정 (선택사항)

### 1단계: 도메인 구매

원하는 도메인 등록기관에서 도메인 구매

### 2단계: DNS 설정

도메인 DNS 레코드에 다음 추가:

```
Type: CNAME
Name: www (또는 @)
Value: username.github.io
```

또는 A 레코드:

```
Type: A
Name: @
Value: 185.199.108.153
       185.199.109.153
       185.199.110.153
       185.199.111.153
```

### 3단계: GitHub Pages 설정

1. 저장소 **Settings** > **Pages**
2. **Custom domain**에 도메인 입력
3. **Save** 클릭
4. **Enforce HTTPS** 체크

### 4단계: Hugo 설정 업데이트

```yaml
# hugo.yaml
baseURL: https://yourdomain.com/
```

## 📊 배포 모니터링

### GitHub Actions

- 배포 성공/실패 알림
- 빌드 로그 확인
- 실행 시간 확인

### 사이트 확인

배포 후 다음을 확인하세요:

- [ ] 홈페이지 정상 로드
- [ ] 네비게이션 메뉴 작동
- [ ] 모든 페이지 접근 가능
- [ ] 폰트 정상 적용
- [ ] 이미지 정상 로드
- [ ] 다크모드 토글 작동
- [ ] 검색 기능 작동

## 🔐 보안 고려사항

### 민감한 정보

- API 키, 비밀번호 등을 커밋하지 마세요
- 필요시 `.gitignore`에 추가
- GitHub Secrets 사용 고려

### Private 저장소

- Private 저장소도 GitHub Pages로 배포 가능 (Pro 계정 필요)
- Public 저장소는 무료로 배포 가능

## 📞 문제 해결

배포 관련 문제가 발생하면:

1. GitHub Actions 로그 확인
2. 로컬에서 빌드 테스트 (`hugo --gc --minify`)
3. baseURL 설정 확인
4. Submodule 상태 확인 (`git submodule status`)
5. GitHub Pages 설정 확인

## 🔗 유용한 링크

- [GitHub Actions 문서](https://docs.github.com/en/actions)
- [GitHub Pages 문서](https://docs.github.com/en/pages)
- [Hugo 배포 가이드](https://gohugo.io/hosting-and-deployment/)

---

*마지막 업데이트: 2025년 10월*
