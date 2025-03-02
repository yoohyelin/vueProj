# Git 협업 기본 흐름

## ✅ 초기 프로젝트 설정
1️⃣ 한 명이 `main` 브랜치에서 초기 프로젝트 구조 설정  
2️⃣ **Spring Boot** 프로젝트 생성 → `backend/` 폴더에 푸쉬  
3️⃣ **Vue.js (Vite)** 프로젝트 생성 → `frontend/` 폴더에 푸쉬  
4️⃣ `.gitignore` 파일 설정 후 `main` 브랜치에 푸쉬  

## ✅ 각 개발자의 작업 흐름
5️⃣ `git checkout -b feature/브랜치명` (예: `feature/login-api`, `feature/user-ui`)  
6️⃣ 각자 기능 개발 후 **commit** & **push**  
7️⃣ **PR(Pull Request)** 생성 → 코드 리뷰 후 `develop` 브랜치에 머지  

## 🔹 Git 브랜치 전략
- **main** 브랜치: 배포(프로덕션)용, 안정적인 코드만 유지  
- **develop** 브랜치: 개발자들이 기능을 병합하는 브랜치, `main`에 바로 머지하지 않고 여기에서 통합  
- **feature/기능명** 브랜치: 각자 기능을 개발하는 브랜치, 완료 후 `develop` 브랜치에 병합  
- **hotfix/버그명** 브랜치: 긴급 수정이 필요할 때 사용하는 브랜치  

## 📌 일반적인 Git 작업 흐름

```bash
# 1️⃣ 초기 프로젝트 클론
git clone <repo-url>
cd <repo-folder>

# 2️⃣ 브랜치 생성
git checkout -b feature/login-api  # 로그인 API 개발 브랜치

# 3️⃣ 작업 후 커밋 & 푸쉬
git add .
git commit -m "로그인 API 구현"
git push origin feature/login-api

# 4️⃣ GitHub에서 PR 생성 후 코드 리뷰 & 머지
# 5️⃣ 머지된 후, 본인의 브랜치 최신화
git checkout develop
git pull origin develop
git branch -d feature/login-api  # 필요 시 브랜치 삭제
