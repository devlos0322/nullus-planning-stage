# Nullus 프로젝트 기획서

## 프로젝트 개요

### 프로젝트명
**Nullus** (라틴어: "없음" 또는 "무에서 시작"의 의미)

### 프로젝트 비전
플랫폼 엔지니어링을 중심으로 한 벤더 중립적 오픈소스 플랫폼 프레임워크를 구축하여, CNCF 커뮤니티의 중심 프로젝트로 성장시키고 지식 주권을 확립하는 것

### 핵심 가치
- **벤더 중립성**: 특정 벤더에 종속되지 않는 오픈소스 기반
- **확장성**: 모듈화된 구조로 지속적인 확장 가능
- **신뢰성**: 검증된 오픈소스 컴포넌트 활용
- **복원력**: 유기적이고 유연한 아키텍처 설계
- **개발 시간 단축**: 체감 가능한 가치 제공
- **운영 리소스 감소**: 자동화를 통한 효율성 향상

## 프로젝트 목표

1. **플랫폼 엔지니어링 표준화**
   - 개발 시간 단축 및 운영 리소스 감소에 초점
   - 체감 가능한 가치 중심의 접근

2. **글로벌 오픈소스 커뮤니티 구축**
   - CNCF 재단 어필 및 글로벌 개발자 참여 유도
   - 허깅페이스의 Transformers처럼 중심 코어 프로젝트로 성장

3. **지식 주권 확립**
   - 오픈소스 기여를 통한 전문성 축적
   - 기술적 명성 및 글로벌 노출
   - 장기적인 경제적 기회 창출

4. **실체화된 코드 제공**
   - 아이디어 수준이 아닌 실제 구현된 코드 제공
   - 누구나 가져다 쓸 수 있는 완성도 높은 솔루션

## 아키텍처 설계

### 5계층 아키텍처

#### 1. 표준 인터페이스 및 포털 (Backstage 기반 확장)
- **Backstage Portal**: Software Catalog / Scaffolder
- **AI Marketplace**: 재사용 가능한 모듈 레지스트리
- **JARVIS (CAIPE)**: Vibe Coding & NLP Interface

#### 2. 지능형 오케스트레이션 (Multi-Agent System & MCP)
- **Supervisor Agent**: Task Breakdown / LLM-as-Judge
- **Domain Agents**: IaC, K8s, Security, FinOps 전문 에이전트
- **MCP Servers**: Context Engineering / Data Glue

#### 3. 통합 보안 및 거버넌스 가드레일 (Policy as Code)
- **Sentinel / OPA / OpenBao**: Policy Enforcement & Secrets 관리
- **Falco / Checkov**: Runtime & Static Security Scan
- **OS Hardening Script**: FSS/국정원 보안 표준 준수

#### 4. 하이브리드 인프라 실행 계층 (CSP-Agnostic IaC)
- **Terraform / OpenTofu**: 표준화된 IaC 템플릿
- **KubeSpray / K-PaaS**: 독립적인 K8s 프로비저닝
- **Ansible Tower**: VM / Baremetal 설정
- **K8s API Manager**: 멀티 클러스터 중앙화
- **Cilium / Silly**: eBPF 기반 네트워킹

#### 5. 지식 레이어 및 최적화 (AIOps & Knowledge Graph)
- **Neo4j Knowledge Graph**: 온톨로지 및 장기 메모리
- **Prometheus / Grafana**: SLI/SLO 기반 관찰 가능성
- **DNN FinOps Engine**: 예측적 리소스 스케일링

### 추가 고려 사항

#### 데이터 옵스 레이어
- 데이터 성향별 처리 모듈화
  - 작은 데이터 대량 처리 (이커머스, 채팅)
  - 큰 데이터 처리 (연구소, 빅데이터)
  - 고빈도 트랜잭션 처리
  - 주기적 데이터 처리
- AI 기반 가상 데이터 생성 활용

#### ML 옵스 레이어
- GPU Ops: NVIDIA GPU Operator 기반 모니터링
- 데이터 레이어: 데이터셋 포맷 선택, 라벨링, 클렌징
- ML Ops: Apache Airflow 기반 파이프라인
- LLM Ops: LangChain 기반 프롬프트 관리

## 기술 스택 및 선택 기준

### 데이터베이스
- **PostgreSQL**: 메인 데이터베이스
  - 다양한 플러그인 지원 (벡터 DB 포함)
  - SQL 기반 쿼리로 학습 곡선 최소화
  - 오픈소스 생태계와의 호환성

### CNCF 프로젝트 우선 활용
- CNCF에서 검증된 프로젝트 우선 선택
- Sandbox → Incubating → Graduated 단계 고려
- 기술뿐만 아니라 시장 상황, 커뮤니티 활성도 종합 평가

### 멀티 아키텍처 지원
- **ARM64** (Apple Silicon, M 시리즈)
- **AMD64/x86_64**
- 로컬 개발 환경 우선 지원 후 클라우드 확장

## 개발 방향성

### 1. 오픈소스 조합 중심
- 기존 검증된 오픈소스 컴포넌트 조합
- 각 컴포넌트 간 인터페이스 표준화
- Loose Coupling 설계로 유연한 교체 가능

### 2. 코드 기반 자동화
- Infrastructure as Code (IaC) 완전 자동화
- Terraform/OpenTofu + Ansible + Shell Script
- 한 줄 명령어로 전체 설치 가능 (Kubeflow 스타일)
- 90% 이상 자동 설치로 사용자 부담 최소화

### 3. 로컬 우선, 클라우드 확장
- 초기: 로컬 환경 (VirtualBox, VMware Fusion) 지원
- 베이스 OS 이미지 최적화 (Ubuntu 24.04 기반)
- Kubernetes 최적화된 OS 이미지 제공
- HashiCorp Vagrant Cloud에 이미지 배포
- 향후: 클라우드 배포 버전 제공

### 4. 속도감 있는 개발
- 빠른 프로토타이핑 및 반복
- 작은 마일스톤으로 지속적인 결과물 산출
- 실패를 통한 학습 및 개선

### 5. API 중심 설계
- 모든 기능을 API로 제공
- 포털/UI는 API 기반으로 구축
- 컨텍스트 엔지니어링을 통한 AI 에이전트 연동

## 개발 언어 및 도구

### 언어 선택
- 초기: 각자 선호하는 언어 사용 (개인 취향 존중)
- 향후: 프로젝트 방향성에 맞춰 통일 검토
- WebAssembly 고려 (크로스 플랫폼 호환성)

### 버전 관리
- GitHub Organization 생성
- 프로젝트별 서브 프로젝트 구성
- 오픈소스 라이선스 결정 필요

## 역할 및 책임
## 마일스톤

### Phase 1: 기반 구축 (현재)
- [O] 프로젝트 네이밍 확정 (Nullus)
- [ ] GitHub Organization 생성
- [ ] 전체 아키텍처 설계 합의
- [ ] 역할 및 책임 분담
- [ ] 개발 언어 및 도구 결정

### Phase 2: 핵심 컴포넌트 개발
- [ ] OS 베이스 이미지 최적화 (ARM/AMD 지원)
- [ ] Kubernetes 기반 인프라 자동화
- [ ] Backstage 기반 포털 구축
- [ ] Multi-Agent System 기본 구조

### Phase 3: 통합 및 테스트
- [ ] 각 레이어 통합
- [ ] 로컬 환경 테스트
- [ ] 문서화

### Phase 4: 커뮤니티 확장
- [ ] CNCF 제출 준비
- [ ] 글로벌 개발자 초대
- [ ] 기업 파트너십 (삼성전자 등)

## 비용 및 리소스

### 초기 비용
- 퍼블릭 클라우드 테스트 비용: 클라우드브로 지원
- LLM API 키: 제공 예정
- 무료 클라우드 크레딧 활용

### 향후 비용
- 국책 과제 연계 검토
- 기업 파트너십을 통한 리소스 확보

## 다음 액션 아이템

1. **디스코드에서 설계 논의**
   - 전체 아키텍처 하이레벨 합의
   - 각 레이어별 담당자 지정
   - 기술 스택 최종 결정

2. **초안 완성 후 리뷰**
   - 파코 등 글로벌 전문가 리뷰 요청
   - 피드백 반영

3. **다음 미팅**
   - 일시: 2026년 1월 16일 (금) 오후 8시 30분
   - 목적: 설계 최종안 합의 및 역할 분담

## 참고 자료

- CNCF 프로젝트: https://landscape.cncf.io/
- 클라우드 네이티브 AI: CNCF Cloud Native AI 탭
- Backstage: https://backstage.io/
- Platform Engineering Gold Path (권재환, 아콘)

## 기대 효과

1. **개발자 경험 향상**
   - 복잡한 인프라 설정 자동화
   - 일관된 개발 환경 제공

2. **기업 도입 용이성**
   - 벤더 중립적 솔루션
   - 검증된 오픈소스 기반
   - 커스터마이징 가능

3. **커뮤니티 성장**
   - 글로벌 개발자 참여
   - 지식 공유 및 협업
   - 지속 가능한 생태계 구축

4. **기술 주권**
   - 국내 기술 역량 강화
   - 글로벌 시장 진출 기반 마련
