# 🚗 Autobot

중고차 통합검색 AI 챗봇 서비스, 오토봇의 모노레포입니다. 이 저장소는 프론트엔드와 백엔드 모두 포함하고 있습니다.

<br/>

## 📌 소개
Autobot은 중고차 구매를 고민하는 사용자들을 위한 AI 기반 챗봇 서비스입니다. AWS Bedrock의 강력한 AI 기능을 활용하여 사용자의 질문에 맞춤형 답변을 제공하고, 원하는 중고차를 쉽게 찾을 수 있도록 도와줍니다.

### 주요 기능 💫
- 🤖 자연스러운 대화를 통한 중고차 검색
- 🎯 차량 조건 기반 맞춤형 추천
- 💰 실시간 시세 정보 제공
- 📊 차량 상세 정보 및 비교 분석

<br/>

## 🛠 기술 스택
- **프론트엔드**: React, Vite
- **백엔드**: Java 17, Spring Boot 3.2
- **캐시 서버**: Redis 7.2
- **데이터베이스**: PostgreSQL 15
- **컨테이너화**: Docker
- **AI 엔진**: AWS Bedrock (Haiku 3)

<br/>

## 🚀 시작하기

### 사전 요구사항
- Docker 및 Docker Compose가 설치된 환경
- AWS 계정 및 접근 권한
- AWS Bedrock 사용 권한
<br/>

### 📥 설치 및 실행 방법

#### 1. 저장소 클론
```bash
git clone https://github.com/SWSchool-Straight/Autobot.git
cd Autobot
```
<br/>

#### 2. AWS Bedrock 리소스 설정
AWS Bedrock 서비스 설정을 위해 다음 단계를 따라주세요:
1. AWS Management Console에 로그인
2. Bedrock 서비스 접근 권한 확인
3. 제공된 PDF 문서를 참고하여 다음 리소스들을 생성:
   - Knowledge Base 생성
   - Guardrail 설정
   - 모델 선택 및 ARN 확인

**필요한 정보**:
- ⚡ AWS Access Key
- 🔑 AWS Secret Key
- 📋 Model ARN
- 📚 Knowledge Base ID
- 🛡 Guardrail ID
- 🔢 Guardrail Version

<br/>

#### 3. 환경 변수 설정
`.env` 파일에 다음 환경 변수들을 설정합니다:

```plaintext
APP_URL=your-app-url (EC2 인스턴스에서 실행한 경우: http://<퍼블릭 IP>)
DB_PW=your-db-password
AWS_ACCESS_KEY=your-access-key
AWS_SECRET_KEY=your-secret-key
AWS_MODEL_ARN=your-model-arn
AWS_KNOWLEDGEBASE_ID=your-kb-id
AWS_GUARDRAIL_ID=your-guardrail-id
AWS_GUARDRAIL_VERSION=your-guardrail-version
```

<br/>

#### 4. 서버 실행
```bash
docker-compose up -d
```

**실행 후 확인**:
- 프론트엔드: http://localhost
- 백엔드: http://localhost:8080
- Redis 서버: localhost:6379
- PostgreSQL 서버: localhost:5432
> EC2 인스턴스에서 실행한 경우: http://<퍼블릭 IP>

<br/>

## 🏗 아키텍처
서비스는 다음과 같은 컴포넌트로 구성되어 있습니다:
- 🌐 프론트엔드 애플리케이션 (포트: 80)
  - 사용자 인터페이스 제공
  - 백엔드 API와 통신
- 🌐 Spring Boot 애플리케이션 서버 (포트: 8080)
  - REST API 제공
  - AWS Bedrock 연동
  - 비즈니스 로직 처리
- ⚡ Redis 캐시 서버 (포트: 6379)
  - 세션 관리
  - 빠른 응답을 위한 캐싱
- 💾 PostgreSQL 데이터베이스 (포트: 5432)
  - 사용자 데이터 저장
  - 채팅 기록 관리
  - 차량 정보 저장

<br/>

## 📖 API 문서
상세한 API 명세는 다음 문서를 참고해주세요:
- [API 상세 문서](https://www.notion.so/API-92e4d70828a04da99a06b058a47471d3)

<br/>

## ⚖️ 라이선스
이 프로젝트는 MIT 라이선스 하에 배포됩니다.

<br/>

## 🔍 문제 해결
자주 발생하는 문제들과 해결 방법:

1. **Docker 실행 오류**
   - Docker 데몬이 실행 중인지 확인
   - 포트 충돌 여부 확인 (80, 8080, 6379, 5432)
   - 메모리 부족 시 Docker 리소스 할당 확인

2. **AWS 연결 문제**
   - AWS 인증 정보 재확인
   - 리전 설정 확인 (기본: us-east-1)
   - IAM 권한 확인
   - VPC 및 보안 그룹 설정 확인

3. **데이터베이스 연결 오류**
   - PostgreSQL 서비스 실행 상태 확인
   - 환경 변수 설정 확인
   - 데이터베이스 초기화 상태 확인
   - AWS 인증 정보 재확인


