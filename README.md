# 🎨 SKouter 프론트엔드 프로젝트

채용 정보 서비스를 위한 React 프론트엔드 웹 애플리케이션입니다.우와아!

---

## 📖 목차

1. [프로젝트 소개](#-프로젝트-소개)
2. [기술 스택](#-기술-스택)
3. [시작하기](#-시작하기)
4. [프로젝트 구조 이해하기](#-프로젝트-구조-이해하기)
5. [협업 가이드](#-협업-가이드)
6. [이슈와 브랜치 연결 방법](#-이슈와-브랜치-연결-방법)
7. [백엔드 API 연동](#-백엔드-api-연동)
8. [문제 해결](#-문제-해결)

---

## 🎯 프로젝트 소개

**SKouter**는 채용 공고를 크롤링하고 AI로 분석하여 사용자에게 최적의 공고를 추천하는 서비스입니다.

### 주요 기능
- ✅ 채용 공고 목록 및 상세 조회
- ✅ 검색 및 필터링 (키워드, 지역, 스킬)
- ✅ 회사별 공고 조회
- ✅ 로그인 / 회원가입
- ✅ AI 기반 공고 품질 점수 시각화
- ✅ 공고 비교 기능
- ✅ AI 채팅 챗봇

---

## 🛠 기술 스택

| 분류 | 기술 |
|------|------|
| **언어** | JavaScript / TypeScript |
| **프레임워크** | React 18 |
| **빌드 도구** | Vite / Create React App |
| **상태 관리** | Zustand / Redux Toolkit |
| **라우팅** | React Router v6 |
| **HTTP 클라이언트** | Axios |
| **스타일링** | Tailwind CSS / CSS Modules |
| **차트** | Recharts / Chart.js |
| **폼 처리** | React Hook Form |

---

## 🚀 시작하기

### 1️⃣ 사전 준비물

컴퓨터에 다음 프로그램이 설치되어 있어야 합니다:

- **Node.js 18+** ([다운로드](https://nodejs.org/))
- **npm 또는 yarn**
- **Git** ([다운로드](https://git-scm.com/))

> 💡 **확인 방법**: 터미널에서 `node -v` 입력 시 18 이상 버전이 나와야 합니다.

---

### 2️⃣ 프로젝트 클론

```bash
# 레포지토리 클론
git clone https://github.com/SKALA-SKouter/SKouter-frontend.git

# 프로젝트 폴더로 이동
cd SKouter-frontend
```

---

### 3️⃣ 의존성 설치

```bash
# npm 사용
npm install

# 또는 yarn 사용
yarn install
```

---

### 4️⃣ 환경 변수 설정

프로젝트 루트에 `.env` 파일 생성:

```env
# 백엔드 API URL
VITE_API_BASE_URL=http://localhost:8080

# AI 서버 URL (선택)
VITE_AI_API_URL=http://localhost:8000
```

---

### 5️⃣ 개발 서버 실행

```bash
# Vite 사용
npm run dev

# 또는 CRA 사용
npm start
```

브라우저에서 자동으로 열립니다:
- **로컬 주소**: http://localhost:5173 (Vite) 또는 http://localhost:3000 (CRA)

✅ 화면이 나오면 성공!

---

## 📁 프로젝트 구조 이해하기

### 전체 구조 (비유로 이해하기)

React 프로젝트는 **레고 블록**이라고 생각하면 쉽습니다:

```
레고 집 (React App)
├── 큰 블록 (Pages)        👉 완성된 페이지
├── 작은 블록 (Components)  👉 재사용 가능한 부품
├── 도구 (Hooks)           👉 특별한 기능
├── 설계도 (Types)         👉 데이터 구조
├── 물품 보관함 (Store)     👉 전역 상태
└── 연결선 (API)           👉 백엔드와 통신
```

---

### 폴더별 역할

#### 📂 `src/` (소스 코드 루트)

```
src/
├── components/          🧩 재사용 가능한 컴포넌트
│   ├── common/               공통 컴포넌트
│   │   ├── Button.tsx             버튼
│   │   ├── Input.tsx              입력 필드
│   │   ├── Card.tsx               카드
│   │   └── Loading.tsx            로딩 스피너
│   │
│   ├── layout/               레이아웃
│   │   ├── Header.tsx             헤더
│   │   ├── Footer.tsx             푸터
│   │   ├── Sidebar.tsx            사이드바
│   │   └── Layout.tsx             전체 레이아웃
│   │
│   └── job/                  채용공고 관련
│       ├── JobCard.tsx            공고 카드
│       ├── JobList.tsx            공고 목록
│       ├── JobFilter.tsx          필터
│       └── JobDetail.tsx          상세 정보
│
├── pages/               📄 페이지 (라우트)
│   ├── HomePage.tsx           메인 페이지
│   ├── JobListPage.tsx        공고 목록 페이지
│   ├── JobDetailPage.tsx      공고 상세 페이지
│   ├── CompanyPage.tsx        회사 페이지
│   ├── LoginPage.tsx          로그인 페이지
│   ├── ComparePage.tsx        공고 비교 페이지 (AI)
│   └── ChatbotPage.tsx        챗봇 페이지 (AI)
│
├── hooks/               🎣 커스텀 훅
│   ├── useAuth.ts             인증 관련
│   ├── useJobs.ts             채용공고 데이터
│   ├── useInfiniteScroll.ts   무한 스크롤
│   └── useDebounce.ts         디바운싱
│
├── store/               🗄️ 상태 관리
│   ├── authStore.ts           인증 상태
│   ├── jobStore.ts            공고 상태
│   └── uiStore.ts             UI 상태
│
├── api/                 📡 API 통신
│   ├── axios.ts               Axios 설정
│   ├── jobApi.ts              채용공고 API
│   ├── authApi.ts             인증 API
│   └── companyApi.ts          회사 API
│
├── types/               📝 TypeScript 타입
│   ├── job.ts                 채용공고 타입
│   ├── company.ts             회사 타입
│   ├── user.ts                사용자 타입
│   └── api.ts                 API 응답 타입
│
├── utils/               🛠️ 유틸리티 함수
│   ├── formatDate.ts          날짜 포맷팅
│   ├── validateForm.ts        폼 검증
│   └── localStorage.ts        로컬 스토리지 관리
│
├── styles/              🎨 스타일
│   ├── globals.css            전역 스타일
│   └── tailwind.css           Tailwind CSS
│
├── App.tsx              📱 앱 루트 컴포넌트
├── main.tsx             ▶️ 진입점 (Vite)
└── vite.config.ts       ⚙️ Vite 설정
```

---

### 데이터 흐름 (사용자 액션부터 화면 업데이트까지)

```
1. 사용자가 버튼 클릭 (예: "검색")
   ↓
2. Component가 이벤트 처리
   ↓
3. API 함수 호출 (axios)
   ↓
4. 백엔드 서버에 요청 (GET /api/jobs?keyword=...)
   ↓
5. 백엔드 응답 받기 (JSON 데이터)
   ↓
6. Store 업데이트 (상태 변경)
   ↓
7. Component 리렌더링 (화면 업데이트)
```

---

## 🤝 협업 가이드

### 작업 시작 전 (필수!)

#### 1️⃣ 최신 코드 받기
```bash
git pull origin main
```

#### 2️⃣ 새 브랜치 만들기
```bash
# 예: WBS 3.3.2 공고 목록 페이지 개발
git checkout -b feature/job-list-page
```

---

### 작업 순서 (역할별)

#### 👩‍💻 **프론트엔드 개발자 A** - UI 개발 담당

**작업 예시: 채용공고 목록 페이지 만들기**

1. **페이지 컴포넌트 작성** (`pages/JobListPage.tsx`)
```tsx
import { useJobs } from '@/hooks/useJobs';
import JobCard from '@/components/job/JobCard';

const JobListPage = () => {
  const { jobs, loading } = useJobs();

  if (loading) return <Loading />;

  return (
    <div className="container">
      <h1>채용 공고</h1>
      <div className="grid">
        {jobs.map((job) => (
          <JobCard key={job.id} job={job} />
        ))}
      </div>
    </div>
  );
};

export default JobListPage;
```

2. **라우트 추가** (`App.tsx`)
```tsx
import { BrowserRouter, Routes, Route } from 'react-router-dom';

function App() {
  return (
    <BrowserRouter>
      <Routes>
        <Route path="/" element={<HomePage />} />
        <Route path="/jobs" element={<JobListPage />} />
        <Route path="/jobs/:id" element={<JobDetailPage />} />
      </Routes>
    </BrowserRouter>
  );
}
```

3. **테스트**
```bash
npm run dev
# http://localhost:5173/jobs 접속하여 확인
```

---

## 🔗 이슈와 브랜치 연결 방법

### ✨ 핵심 개념

> **이슈는 "할 일 목록"이고, 브랜치는 "작업 공간"입니다!**

```
GitHub 이슈 (Issue)
  ↓ (작업 시작)
Git 브랜치 (Branch)
  ↓ (코드 작성)
커밋 (Commit)
  ↓ (완료)
Pull Request (PR)
  ↓ (리뷰 & 병합)
이슈 자동 종료
```

---

### 📝 전체 워크플로우

#### 1️⃣ GitHub에서 이슈 확인
https://github.com/SKALA-SKouter/SKouter-frontend/issues

예시: **Issue #10** - "WBS 3.3.2: 공고 목록/검색 페이지"

---

#### 2️⃣ 로컬에서 브랜치 생성 및 작업

```bash
# 최신 코드 받기
git pull origin main

# 이슈 번호를 포함한 브랜치 생성
git checkout -b feature/job-list-page-#10
# 또는
git checkout -b feature/10-job-list-page

# 코드 작성
# pages/JobListPage.tsx 생성
# components/JobCard.tsx 수정
# ...

# 커밋 (이슈 번호 포함!)
git add .
git commit -m "feat: 채용공고 목록 페이지 구현

- JobListPage 컴포넌트 생성
- useJobs 훅으로 데이터 관리
- 반응형 그리드 레이아웃 적용

Closes #10"
# 👆 "Closes #10"이 중요! 이렇게 쓰면 PR 병합 시 이슈가 자동으로 닫힙니다

# 푸시
git push origin feature/job-list-page-#10
```

---

#### 3️⃣ GitHub에서 Pull Request 생성

1. GitHub 레포지토리로 이동
2. **Compare & pull request** 버튼 클릭
3. PR 작성:

```markdown
## 관련 이슈
Closes #10

## 작업 내용
- 채용공고 목록 페이지 UI 구현
- 검색 기능 추가
- 페이징 처리

## 스크린샷
![목록 페이지](https://example.com/screenshot.png)

## 테스트 방법
1. `npm run dev` 실행
2. http://localhost:5173/jobs 접속
3. 공고 목록 확인
```

4. **Assignees**: 본인 선택
5. **Labels**: `ui`, `phase-2` 등 선택
6. **Linked issues**: #10 연결 (자동으로 될 수도 있음)

---

#### 4️⃣ 코드 리뷰 & 병합

- 팀원이 코드 리뷰
- 수정 사항 반영
- Approve 후 **Merge**
- 🎉 **이슈 #10이 자동으로 Close됨!**

---

### 🎯 커밋 메시지에서 이슈 자동 연결하기

#### 키워드 사용:

| 키워드 | 의미 | 예시 |
|--------|------|------|
| `Closes #이슈번호` | 이슈 닫기 | `Closes #10` |
| `Fixes #이슈번호` | 버그 수정 | `Fixes #15` |
| `Resolves #이슈번호` | 이슈 해결 | `Resolves #20` |
| `Ref #이슈번호` | 참고만 (안 닫힘) | `Ref #10` |

#### 여러 이슈 한번에:
```bash
git commit -m "feat: UI 개선

Closes #10
Closes #11
Fixes #12"
```

---

### 📌 이슈와 브랜치 네이밍 규칙

#### 브랜치 이름 형식:
```bash
타입/간단한-설명-#이슈번호

예시:
feature/job-list-#10
fix/search-bug-#15
style/button-ui-#20
```

#### 타입:
- `feature/`: 새 기능
- `fix/`: 버그 수정
- `style/`: UI/스타일
- `refactor/`: 리팩토링
- `docs/`: 문서

---

### 💡 실전 예시

#### 시나리오: Issue #10 "공고 목록 페이지 구현"

```bash
# 1. 브랜치 생성
git checkout -b feature/job-list-#10

# 2. 코드 작성
# (파일 생성 및 수정)

# 3. 1차 커밋
git commit -m "feat: JobListPage 컴포넌트 생성

Ref #10"

# 4. 2차 커밋
git commit -m "feat: 검색 기능 추가

Ref #10"

# 5. 최종 커밋 (완료!)
git commit -m "feat: 공고 목록 페이지 완성

- JobListPage 완성
- 검색, 필터, 페이징 모두 동작
- 반응형 확인 완료

Closes #10"
# 👆 마지막 커밋에만 Closes 사용!

# 6. 푸시
git push origin feature/job-list-#10

# 7. PR 생성 (GitHub 웹)
# 8. Merge → 이슈 #10 자동 닫힘!
```

---

### ⚠️ 주의사항

1. **이슈에 코드를 직접 넣지 않습니다!**
   - ❌ 이슈 댓글에 코드 복붙
   - ✅ 브랜치에서 작업 → PR로 리뷰

2. **이슈는 "계획"이고 PR은 "실행"입니다**
   - 이슈: "이걸 만들 거야"
   - PR: "이렇게 만들었어, 확인해줘"

3. **하나의 브랜치는 하나의 이슈에 집중**
   - ❌ 한 브랜치에서 여러 이슈 작업
   - ✅ 이슈별로 브랜치 분리

---

## 🔌 백엔드 API 연동

### Axios 설정

**`api/axios.ts`**
```tsx
import axios from 'axios';

const instance = axios.create({
  baseURL: import.meta.env.VITE_API_BASE_URL || 'http://localhost:8080',
  timeout: 10000,
  headers: {
    'Content-Type': 'application/json',
  },
});

// 요청 인터셉터 (토큰 추가)
instance.interceptors.request.use(
  (config) => {
    const token = localStorage.getItem('token');
    if (token) {
      config.headers.Authorization = `Bearer ${token}`;
    }
    return config;
  },
  (error) => Promise.reject(error)
);

// 응답 인터셉터 (에러 처리)
instance.interceptors.response.use(
  (response) => response,
  (error) => {
    if (error.response?.status === 401) {
      localStorage.removeItem('token');
      window.location.href = '/login';
    }
    return Promise.reject(error);
  }
);

export default instance;
```

---

## 🔧 문제 해결

### 1. npm install 실패

#### 증상: `ERESOLVE unable to resolve dependency tree`

**해결 방법**:
```bash
npm cache clean --force
rm -rf node_modules package-lock.json
npm install --legacy-peer-deps
```

---

### 2. CORS 에러

#### 증상: `Access to fetch has been blocked by CORS policy`

**해결 방법** (`vite.config.ts`):
```tsx
export default defineConfig({
  server: {
    proxy: {
      '/api': {
        target: 'http://localhost:8080',
        changeOrigin: true,
      },
    },
  },
});
```

---

## 📞 도움말

### 자주 묻는 질문

#### Q1. 컴포넌트는 어디에 만드나요?
**A**:
- 재사용 → `components/common/`
- 특정 기능 → `components/job/` 등
- 페이지 → `pages/`

#### Q2. 이슈와 브랜치 관계가 헷갈려요!
**A**:
```
이슈 = "할 일 메모"
브랜치 = "작업하는 책상"
커밋 = "진행 상황 저장"
PR = "완성품 검토 요청"
```

---

## 👥 팀원

- **PM**: 박현규
- **프론트엔드**: 고나연, 조성호
- **백엔드**: 신동건, 조석희

---

## 📌 관련 레포지토리

- 백엔드: https://github.com/SKALA-SKouter/SKouter-backend
- AI Agent: https://github.com/SKALA-SKouter/SKouter-AI-Agent

---

**마지막 업데이트**: 2025-11-20
