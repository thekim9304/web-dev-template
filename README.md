# 🏠 Real Estate Info Platform Template

FastAPI + Next.js + PostgreSQL 기반의 부동산 정보 분석 플랫폼 템플릿입니다.  
지도에서 특정 부동산을 검색하거나 클릭하면 주변 입지 정보를 확인하는 기능 개발을 목표로 합니다.

Docker 기반으로 구성되어 있어 로컬 및 배포 환경 모두 빠르게 시작할 수 있습니다.

---

## 📦 기술 스택

- **Frontend**: Next.js (React 기반 SSR 프레임워크)
- **Backend**: FastAPI (Python 기반 비동기 API 서버)
- **Database**: PostgreSQL 14
- **DevOps**: Docker + Docker Compose

---

## 🐧 0단계: 깡통 리눅스에서 시작하기 (Ubuntu 기준)

### 0.1 Docker & Git 설치

```bash
sudo apt update
sudo apt install -y docker.io docker-compose git

# Docker 실행 및 권한 부여
sudo systemctl enable docker
sudo systemctl start docker
sudo usermod -aG docker $USER
```

> ❗ 권한 적용을 위해 **로그아웃 후 다시 로그인**해야 `docker` 명령어가 제대로 작동합니다.

---

### 0.2 템플릿 클론

```bash
git clone https://github.com/thekim9304/web-dev-template.git {project_dir_name}
cd {project_dir_name}
```

---

### 0.3 `.env` 파일 생성

```bash
cp .env.example .env
```

#### 또는 직접 생성

```env
POSTGRES_USER=postgres
POSTGRES_PASSWORD=postgres
POSTGRES_DB=realestate
POSTGRES_PORT=5432
POSTGRES_HOST=postgres
```

---

### 0.4 Docker로 전체 실행

```bash
docker-compose up --build
```

---

## ✅ 접속 확인

| 서비스 | 주소 |
|--------|------|
| 🟢 프론트엔드 (Next.js) | http://localhost:3000 |
| 🟢 백엔드 (FastAPI)    | http://localhost:8000/docs |
| 🐘 DB (PostgreSQL)     | localhost:5432 (컨테이너 내부 연결 전용) |

---

## 📁 프로젝트 구조

```
.
├── .env.example              # 환경 변수 예시
├── docker-compose.yml        # 전체 서비스 정의
├── README.md                 # 사용 가이드
│
├── fastapi/                  # FastAPI 백엔드
│   ├── Dockerfile
│   ├── requirements.txt
│   └── app/
│       ├── api/
│       ├── core/
│       ├── db/
│       └── main.py
│
├── nextjs/                   # Next.js 프론트엔드
│   ├── Dockerfile
│   ├── package.json
│   ├── package-lock.json
│   └── pages/
│       ├── index.js          # 기본 페이지
│       └── detail/
│           └── [id].js       # 상세 정보 라우팅 구조
│
└── postgres/
    └── init.sql              # DB 초기화 스크립트
```