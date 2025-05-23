from pathlib import Path

# Markdown content from previous response
markdown_content = """
# N8N 자동화 실습 커리큘럼 (초급–중급–고급)

## 1. 초급 과정 (N8N 입문 및 기초 활용)

| 회차 | 주제 | 세부 목표 | 중요 토픽 / 용어 | 참조 URL |
|------|------|-----------|-------------------|----------|
| 1강 | [N8N 설치 및 기본 구조](./01.Begineer/01.N8N설치및기본구조.md) | N8N을 로컬/클라우드에 설치하고 UI 및 워크플로우 구조 이해 | 워크플로우, 노드, 트리거, 실행 히스토리, 에디터 UI | [N8N 시작하기](https://docs.n8n.io/getting-started/) |
| 2강 | 슬랙 연동 및 메시지 전송 | Slack API 인증 후 메시지 전송 자동화 구성 | Slack Bot Token, OAuth2, 슬랙 노드, 텍스트 포맷 | [Slack 노드](https://docs.n8n.io/integrations/builtin/app-nodes/n8n-nodes-base.slack/) |
| 3강 | DB 연동 (MySQL/SQLite) | DB 연결 설정, SELECT/INSERT 쿼리 자동화 구성 | Credentials, SQL 쿼리, 데이터 매핑, 입력/출력 처리 | [MySQL 노드](https://docs.n8n.io/integrations/builtin/app-nodes/n8n-nodes-base.mysql/) |
| 4강 | Webhook 트리거 | 외부 요청으로 워크플로우 실행 및 데이터 처리 | Webhook, HTTP 요청, JSON 파싱, 응답 구성 | [Webhook 노드](https://docs.n8n.io/integrations/builtin/triggers/webhook/) |
| 5강 | 간단한 자동화 실습 | Slack + DB + Webhook 조합 실습으로 자동화 이해 | 데이터 흐름, 변수 참조, Switch, 실행 디버깅 | [기초 예제](https://docs.n8n.io/usage-examples/) |

## 2. 중급 과정 (실무 중심 워크숍)

| 회차 | 주제 | 세부 목표 | 중요 토픽 / 용어 | 참조 URL |
|------|------|-----------|-------------------|----------|
| 1강 | 서버 상태 모니터링 자동화 | HTTP 상태 확인 후 조건 분기로 Slack 알림 발송 | HTTP Request, 상태 코드, 조건 분기, Slack 알림 | [HTTP 노드](https://docs.n8n.io/nodes/n8n-nodes-base.httprequest/) |
| 2강 | 주기적 이메일 발송 배치 | Cron 트리거 + SMTP/Gmail로 메일 발송 자동화 | Cron, Gmail 인증, 첨부파일, 템플릿 | [Gmail 노드](https://docs.n8n.io/integrations/builtin/app-nodes/n8n-nodes-base.gmail/) |
| 3강 | 파일 처리 및 자동 보고 | CSV 수집 → 파싱 → DB 저장 → Slack 리포트 | CSV Reader, 파일 트리거, DB 삽입, 슬랙 포맷 | [CSV 노드](https://docs.n8n.io/integrations/community/nodes/n8n-nodes-community.csvfile/) |
| 4강 | 지라(JIRA) 연동 자동화 | JIRA 이슈 생성 및 상태 변경 자동화 | Jira API, 이슈 타입, 인증, REST 호출 | [JIRA 노드](https://docs.n8n.io/integrations/community/nodes/n8n-nodes-atlassian.jira/) |
| 5강 | 애자일 보고서 자동화 | 업무 상태 수집 → 리포트 자동 작성 및 공유 | 필터링, 반복 처리, 슬랙/이메일 포맷화 | [Agile 예제](https://docs.n8n.io/workflows/examples/agile-reporting/) |

## 3. 고급 과정 (AI 활용 및 시스템 자동화)

| 회차 | 주제 | 세부 목표 | 중요 토픽 / 용어 | 참조 URL |
|------|------|-----------|-------------------|----------|
| 1강 | GPT API 연동 자동응답 | OpenAI 연동 후 사용자 질문에 AI 응답 자동화 | GPT API, 프롬프트 설계, JSON 응답 처리 | [OpenAI 노드](https://docs.n8n.io/integrations/community/nodes/n8n-nodes-openai/) |
| 2강 | 슬랙 챗봇 구현 | 슬랙 입력에 대해 GPT 기반 챗봇 자동 응답 구성 | Slack Event, 대화 흐름, 입력 파싱, GPT 응답 | [Slack 챗봇 예제](https://n8n.io/workflows/1728-slack-gpt-chatbot) |
| 3강 | AI 기반 업무 판단 자동화 | GPT를 이용한 분기 판단 및 실행 흐름 구성 | 조건 분기, 컨텍스트 기반 AI 판단 | [AI 분기 예제](https://community.n8n.io/t/ai-decision-making-with-openai-node/16240) |
| 4강 | 시스템 로그 분석 및 알림 | 로그 감시 → 이상 탐지 → 슬랙/메일 경고 구성 | 로그 파싱, 텍스트 매칭, 알림 트리거 | [모니터링 예제](https://docs.n8n.io/usage-examples/system-monitoring/) |
| 5강 | IT 운영 전체 자동화 구성 | 통합 워크플로우로 전사적 업무 자동화 구현 | 오류 처리, 분기 흐름, 멀티 API 연동 | [엔터프라이즈 자동화](https://docs.n8n.io/usage-examples/enterprise-automation/) |

## n8n에서 제공하는 5가지 모듈

| 모듈 | 특징 | 대표 모듈 | 설명 |
|------|------|-----------|-------------------|
| Core | 기본 기능 제공 | HTTP Request, Function, Set | 워크플로우의 기본 구성 요소로, 데이터 처리와 변환을 담당 |
| Built-in | 내장 통합 기능 | Slack, Gmail, MySQL | 자주 사용되는 서비스와의 통합을 위한 기본 노드 제공 |
| Community | 커뮤니티 기여 | CSV, PDF, Excel | 사용자들이 개발한 추가 기능과 통합 모듈 |
| Enterprise | 기업용 기능 | LDAP, SAML, Audit Logs | 기업 환경에서 필요한 보안, 인증, 감사 기능 |
| Custom | 사용자 정의 | Custom Node, Custom Function | 사용자가 직접 개발하여 추가할 수 있는 커스텀 모듈 |

---

## n8n에서 제공하는 5가지 노드(모듈) 카테고리

| 카테고리      | 특징 및 설명                                                                 | 대표 노드(모듈) 예시                |
|---------------|-----------------------------------------------------------------------------|--------------------------------------|
| Triggers      | 자동화의 시작점이 되는 노드. 워크플로우를 시작하게 만드는 역할.              | Webhook Trigger, Cron Trigger, Email Trigger |
| Actions       | 외부 앱/서비스에서 실제 동작을 수행하는 노드.                               | Google Sheets, Airtable, Notion, Slack, Telegram, Gmail |
| Utility       | 데이터 변환, 필터, 조건문 등 워크플로우 내 데이터 가공 및 흐름 제어.         | IF, Switch, Merge, Set, SplitInBatches, Wait |
| Code          | 코드 실행, HTTP 요청, 웹훅 설정 등 고급 기능을 제공하는 노드.                | Function, Function Item, HTTP Request, Code, Execute Command |
| Advanced AI   | LLM, 검색, 메모리, 체인, 감정 분석 등 AI 기반의 고급 자동화 기능.            | OpenAI, Google Vertex AI, Pinecone, AI Memory, Sentiment Analysis |

### 각 카테고리별 설명 및 대표 노드

1. **Triggers (트리거)**
   - 워크플로우의 시작점이 되는 노드입니다.
   - 예시: Webhook Trigger(외부 요청), Cron Trigger(스케줄), Email Trigger(이메일 수신)

2. **Actions (액션)**
   - 외부 서비스와 연동하여 실제 동작(생성, 조회, 수정 등)을 수행합니다.
   - 예시: Google Sheets(시트에 데이터 추가), Airtable, Notion, Slack, Telegram, Gmail

3. **Utility (유틸리티)**
   - 데이터 변환, 조건 분기, 필터링 등 워크플로우 내 데이터 흐름을 제어합니다.
   - 예시: IF(조건문), Switch(분기), Merge(데이터 합치기), Set(값 설정), SplitInBatches(배치 분할), Wait(대기)

4. **Code (코드)**
   - JavaScript 코드 실행, HTTP 요청, 웹훅 등 고급 자동화 기능을 제공합니다.
   - 예시: Function(코드 실행), Function Item(아이템별 코드), HTTP Request(외부 API 호출), Code, Execute Command(명령어 실행)

5. **Advanced AI (고급 AI)**
   - LLM(대형 언어 모델), 검색, 메모리, 체인, 감정 분석 등 AI 기반의 고급 자동화 기능을 제공합니다.
   - 예시: OpenAI(GPT), Google Vertex AI, Pinecone(벡터DB), AI Memory, Sentiment Analysis(감정 분석)

---

