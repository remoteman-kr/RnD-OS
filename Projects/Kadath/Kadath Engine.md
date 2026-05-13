# 🤖 Project: Rust 기반 자율 진화형 에이전트 엔진 (Phase 1)

## 📋 대화 배경 및 프로젝트 개요

- **배경:** 기존에 Node.js 기반의 OpenClaw를 라즈베리 파이에서 운영하며 에이전트의 동작 원리(Context 주입, `parts` 래핑, Tool 호출)를 파악했습니다. 이제 이를 바탕으로 더 가볍고 빠르며 물리 세계(Robotics)와 직접 결합할 수 있는 나만의 엔진을 구축하고자 합니다.
    
- **비전:** 단순한 챗봇을 넘어, 데몬(Daemon) 형태로 상시 구동되며 스스로 데이터를 쌓고, 학습 계획을 세우며, 물리적 동작(로보틱스)까지 제어하는 **체화된 인공지능(Embodied AI)** 엔진을 만드는 것입니다.
    
- **기술 스택:**
    
    - **Core Engine:** Rust (고성능, 메모리 안전성, 데몬화 최적)
        
    - **Cognition (뇌):** Google Gemini API (대규모 컨텍스트 및 추론)
        
    - **Interface:** Telegram Bot API
        
    - **Network/Security:** Tailscale (내부망 통신 및 보안)
        
    - **Deployment:** Raspberry Pi (Linux systemd Daemon)
        
- **현재 최우선 목표:** 라즈베리 파이에서 러스트 기반 데몬을 띄우고, 테일스케일 망을 통해 텔레그램으로 제미나이와 첫 대화(Echo & Reply)에 성공하는 것.
    

---

## 🗺️ 로드맵 및 마일스톤 (Phase 1: 텔레그램 대화 성공)

아래 마일스톤을 복사하여 노션(Notion)이나 GitHub Issue, 또는 로컬 `TODO.md` 파일에 넣고 진행도를 체크해 보세요.

### Milestone 1: 샌드박스 인프라 구축 (환경 세팅)

- [ ] **Tailscale 네트워크 구성 완료**
    
    - 라즈베리 파이와 개발용 PC를 동일한 Tailnet에 연결
        
    - SSH를 통한 원격 접속 테스트 완료
        
- [ ] **Rust 프로젝트 초기화**
    
    - `cargo new agent_engine` 실행
        
    - 필수 의존성(Crates) 추가: `tokio` (비동기), `teloxide` (텔레그램), `reqwest` (HTTP), `serde_json` (JSON 파싱), `dotenv` (환경변수)
        
- [ ] **환경 변수 파일(`.env`) 세팅**
    
    - `TELEGRAM_BOT_TOKEN` 등록
        
    - `GEMINI_API_KEY` 등록
        

### Milestone 2: 텔레그램 리액티브 루프 (입출력 인터페이스)

- [ ] **Teloxide 봇 기본 뼈대 작성**
    
    - 봇 인스턴스 생성 및 비동기 핸들러(`Dispatcher`) 부착
        
- [ ] **Echo 테스트 성공**
    
    - 사용자가 텔레그램으로 보낸 메시지를 그대로 다시 반환하는 로직 구현
        
- [ ] **기본 커맨드 처리**
    
    - `/start`, `/ping` 등의 기본 상태 확인 명령어 동작 검증
        

### Milestone 3: 제미나이 '뇌' 이식 (AI 연동)

- [ ] **Gemini API 클라이언트 구현**
    
    - `reqwest`를 사용하여 Gemini REST API 호출 로직 작성
        
    - Request / Response JSON 스키마를 Rust `struct`로 정의 (`serde` 활용)
        
- [ ] **파이프라인 통합**
    
    - 텔레그램 메시지 수신 ➔ Gemini API 호출 ➔ 텔레그램으로 답변 전송 흐름 완성
        
- [ ] **에러 핸들링**
    
    - 네트워크 지연, API 한도 초과 등의 상황에서 데몬이 죽지 않고 텔레그램으로 에러 메시지를 보내도록 예외 처리
        

### Milestone 4: 데몬화 및 상시 대기 상태 전환 (운영 환경)

- [ ] **Systemd 서비스 파일 등록**
    
    - `/etc/systemd/system/agent-engine.service` 작성 및 등록
        
- [ ] **백그라운드 실행 및 자동 재시작 검증**
    
    - `sudo systemctl enable --now agent-engine` 실행
        
    - 라즈베리 파이 재부팅 후에도 텔레그램 봇이 자동으로 응답하는지 확인
        
- [ ] **로깅(Logging) 시스템 부착**
    
    - `tracing` 또는 `log` 크레이트를 사용해 데몬의 상태 로그를 로컬 파일에 기록하도록 설정
        

---

### 🚀 향후 확장 로드맵 (Preview)

- **Phase 2:** 간단한 메모리(상태) 유지 장치 추가 (Context 관리)
    
- **Phase 3:** 데몬 타이머(`tokio::time::interval`)를 활용한 능동형(Proactive) 모니터링
    
- **Phase 4:** 러스트 엔진의 기능을 Gemini `Tool`로 노출 (Function Calling)
    
- **Phase 5:** 로보틱스 모터 제어 및 헤드리스 가상 물리 환경(Bevy ECS 등) 통합