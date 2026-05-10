
# 프로젝트명: R&D OS

**부제: OpenClaw와 Obsidian 기반의 지능형 문서관리 파이프라인 구축**

## 1. 프로젝트 목표 (Objectives)

- **지식의 자산화:** 흩어져 있는 양자 기술 논문과 트렌드를 체계적인 지식 그래프(Knowledge Graph)로 변환.
    
- **연구-개발 동기화:** 이론적 학습(Obsidian)이 즉시 실무 개발(GitHub)로 이어지는 심리스한 워크플로우 구축.
    
- **자율적 수행:** OpenClaw 에이전트가 단순 반복 업무(요약, 아카이빙, 환경 설정, 로그 기록)를 대행.
    
- **지속 가능한 관리:** 과거의 시행착오와 미래의 로드맵이 통합된 타임라인 저널 시스템 운영.
    

---

## 2. 사용성 워크플로우 (Usability Workflow)

### Step 1: Capture & Insight (수집 및 분석)

1. 사용자가 arXiv 논문 링크나 기술 아티클을 Obsidian의 Inbox 폴더에 넣습니다.
    
2. 라즈베리파이의 **OpenClaw** 데몬이 새 파일을 감지합니다.
    
3. 에이전트가 내용을 읽고 **[요약본 / 필요 기반 지식 / 관련 프로젝트]**를 추출하여 마크다운 노트를 생성합니다.
    

### Step 2: Planning (프로젝트 형성)

1. 사용자가 요약된 노트를 바탕으로 "이 알고리즘을 테스트하겠다"는 결정을 내리고 프로젝트 템플릿을 활성화합니다.
    
2. 에이전트가 해당 알고리즘 구현에 필요한 **Python(Qiskit/Cirq) 스켈레톤 코드**를 생성합니다.
    

### Step 3: Execution & Versioning (실행 및 형상관리)

1. **OpenClaw**가 GitHub에 비공개 레포지토리를 자동 생성하고 코드를 푸시합니다.
    
2. 사용자가 코딩을 진행하면, 에이전트가 주기적으로 **Commit Log를 분석**하여 Obsidian의 프로젝트 저널에 "오늘의 진척도"를 기록합니다.
    

### Step 4: Feedback & Archiving (회고 및 자산화)

1. 프로젝트 종료 시, 결과물과 배운 점을 에이전트가 정리하여 History 타임라인에 업데이트합니다.
    
2. 성공한 코드는 Code Snippets DB로, 실패한 경험은 Lessons Learned DB로 자동 분류됩니다.
    

---

## 3. 전략적 로드맵 및 마일스톤 (Roadmap)

|   |   |   |   |
|---|---|---|---|
|단계|목표|세부 마일스톤|기간|
|**Phase 1**|**Core Infra**|라즈베리파이-Obsidian-OpenClaw 환경 연동 및 기본 폴더 구조 확립|1-2주|
|**Phase 2**|**Knowledge Engine**|arXiv API 연동, LLM 기반 양자 논문 요약 및 지식 그래프(Dataview) 구축|3-4주|
|**Phase 3**|**Action Bridge**|GitHub API 연동, 프로젝트 템플릿 자동 생성 및 커밋 로그 동기화 기능 구현|5-7주|
|**Phase 4**|**Timeline UI**|통합 대시보드(Canvas/Dataview) 및 미래 로드맵 시각화 완성|8주~|

---

## 4. 개발 세부사항 (Technical Specifications)

### A. 인프라 (Infrastructure)

- **Host:** Raspberry Pi 4/5 (Docker 기반 OpenClaw 데몬 실행).
    
- **Storage:** Obsidian Vault (Local File System + Git 기반 원격 백업).
    
- **Agent framework:** OpenClaw (Custom Skills: arXiv Scraper, GitHub Manager, LaTeX Formatter).
    

### B. 주요 기술 스택

- **Language:** Python (Agent Logic), Markdown (Knowledge Base).
    
- **Visualization:** Obsidian Plugins (Dataview, Templater, Obsidian Git, Periodic Notes, Tasks).
    
- **Quantum Tools:** Qiskit, PennyLane (에이전트가 코드 스켈레톤 생성 시 참조할 라이브러리).
    

---

## 5. 예상 비용 분석 (Estimated Costs)

양자 기술 연구를 위한 개인 OS이므로 운영 비용을 최소화합니다.

|   |   |   |
|---|---|---|
|항목|비용 (월 기준)|비고|
|**Hardware**|0원 (기존 보유)|라즈베리파이 4/5|
|**Obsidian**|0원|개인용 무료 (Sync 필요 시 월 $8, 단 Git 플러그인으로 대체 가능)|
|**LLM API**|약 <br><br>```<br>10 10 <br>```<br><br>30|GPT-4o 또는 Claude 3.5 Sonnet 사용량에 따라 변동 (OpenClaw 연동)|
|**GitHub**|0원|Private Repository 무료 플랜|
|**클라우드 확장**|선택 (약 $5)|향후 외부 접근을 위한 Tailscale 또는 VPS 비용|
|**총계**|**약 1.5만 ~ 4만원**|고성능 AI 에이전트 고용 비용 수준|

---

## 6. 핵심 성과 지표 (KPI)

1. **지식 밀도:** 주간 생성되는 양자 기술 관련 연결 노트(Backlinks) 수.
    
2. **개발 속도:** 아이디어 발생 후 첫 GitHub 커밋까지 걸리는 시간(에이전트 자동화로 단축).
    
3. **관리 효율:** 별도의 정리 시간 없이 일주일간의 R&D 활동이 자동으로 타임라인에 요약되는지 여부.