**Volume 16 Multi Robot and Fleet Intelligence**

# 06. Distributed Intelligence

## 06.01 Distributed Intelligence Architecture Edge Fog Cloud

![](images/image1.png){width="7.268055555555556in" height="7.268055555555556in"}

로봇 플릿(Robot Fleet)의 분산 지능(Distributed Intelligence)은 지각(Perception), 추론(Reasoning), 학습(Learning), 의사결정(Decision-Making)을 하나의 플릿 서버(Fleet Server)에 집중시키지 않고 여러 컴퓨팅 계층(Computational Layer)에 분산 배치하는 아키텍처 접근 방식이다. 다중 로봇 지능(Multi-Robot Intelligence)의 구조에서 이 아키텍처는 로봇-클라우드 통합(Robot-Cloud Integration)과 연합 학습(Federated Learning), 지식 공유(Knowledge Sharing), 계층적 의사결정(Hierarchical Decision-Making), 다중 에이전트 학습(Multi-Agent Learning)과 같은 고급 메커니즘을 연결하는 기반 역할을 한다.

분산 지능의 기본적인 목표는 각 연산을 지연시간(Latency), 대역폭(Bandwidth), 신뢰성(Reliability), 개인정보 보호(Privacy), 연산 요구사항(Computational Requirements)에 가장 적합한 위치에서 실행하는 것이다. 로봇은 연결이 끊어진 상황에서도 안전하게 동작할 수 있는 충분한 지능을 유지해야 하며, 인접한 인프라는 여러 로봇을 조정하고 클라우드 시스템(Cloud System)은 대규모 데이터와 강력한 가속기 또는 여러 사이트에서 수집된 정보를 활용하는 연산을 수행할 수 있어야 한다.

엣지 계층(Edge Layer)은 주로 개별 로봇 또는 로봇에 직접 연결된 컨트롤러(Controller)에 위치하는 컴퓨팅으로 구성된다. 이 계층은 센서 처리(Sensor Processing), 위치추정(Localization), 장애물 감지(Obstacle Detection), 지역 경로계획(Local Planning), 모션 제어(Motion Control), 안전 모니터링(Safety Monitoring)과 같이 결정론적(Deterministic) 또는 준실시간(Near-Real-Time) 응답이 필요한 기능을 처리한다. 이러한 기능은 물리적 움직임과 직접 상호작용하므로 모든 결정을 원격 서버로 전송하면 허용하기 어려운 통신 의존성과 잠재적으로 위험한 지연시간이 발생할 수 있다.

엣지 지능(Edge Intelligence)은 또한 운용 자율성(Operational Autonomy)을 제공한다. 자율이동로봇(AMR)은 상위 계층과의 통신이 불안정해지더라도 계속해서 주행하고, 장애물을 회피하며, 안전 정지(Safe-Stop) 동작을 수행하고, 필수적인 임무 상태(Mission State)를 유지해야 한다. 따라서 엣지는 단순한 저지연 추론 장치(Low-Latency Inference Device)를 넘어 각 로봇이 원격 제어 단말이 아닌 독립적인 물리 에이전트(Physical Agent)로 기능하도록 보장하는 최소 자율 지능 경계(Minimum Autonomous Intelligence Boundary)를 의미한다.

포그 계층(Fog Layer)은 개별 로봇과 중앙집중형 클라우드 인프라(Centralized Cloud Infrastructure) 사이에 배치되는 컴퓨팅 자원을 의미한다. 포그 노드(Fog Node)는 공장 서버실, 창고 제어 캐비닛, 프라이빗 5G(Private 5G) 인프라, 산업용 엣지 서버(Industrial Edge Server), 사이트 수준 컴퓨팅 클러스터(Site-Level Computing Cluster) 등에 위치할 수 있다. 로봇과 물리적으로 가까운 위치에 있기 때문에 광역 네트워크(Wide-Area Network)를 거치지 않고 정보를 집계하고 조정 작업을 수행할 수 있다.

포그 지능(Fog Intelligence)은 하나의 로봇 범위를 넘어가면서도 비교적 빠른 응답이 필요한 의사결정에서 특히 유용하다. 대표적인 예로 지역 플릿 교통 조정(Local Fleet Traffic Coordination), 공유 지도 업데이트(Shared-Map Update), 구역 예약(Zone Reservation), 임무 재분배(Mission Redistribution), 혼잡 관리(Congestion Management), 협력 지각(Collaborative Perception), 인접 로봇 간 정보 동기화(Information Synchronization)가 있다. 따라서 포그 계층은 클라우드 중심 아키텍처보다 낮은 지연시간을 유지하면서 개별 엣지 에이전트를 조정된 지역 집단(Local Collective)으로 전환한다.

클라우드 계층(Cloud Layer)은 가장 광범위한 연산 및 정보 범위를 제공한다. 여러 로봇, 플릿, 시설, 지리적 지역으로부터 텔레메트리(Telemetry)를 통합하고 대규모 저장, 과거 데이터 분석(Historical Analysis), 모델 학습(Model Training), 시뮬레이션(Simulation), 플릿 최적화(Fleet Optimization), 글로벌 지식 관리(Global Knowledge Management)를 지원할 수 있다. 따라서 클라우드 지능(Cloud Intelligence)은 밀리초 수준의 반응시간보다 연산 규모와 정보의 범위가 중요한 작업에 적합하다.

이 세 계층은 고정된 하드웨어 범주로 해석해서는 안 된다. 엣지(Edge), 포그(Fog), 클라우드(Cloud)는 논리적인 책임 경계(Logical Responsibility Boundary)를 의미하며 실제 구현 방식은 배포 규모에 따라 달라질 수 있다. 강력한 온프레미스 GPU 서버(On-Premise GPU Server)는 하나의 시설에서 포그 기능을 수행하면서 동시에 클라우드 서비스와 상호작용할 수 있다. 마찬가지로 높은 AI 연산 능력을 가진 로봇은 일반적으로 사이트 수준 서버에 할당되는 일부 기능까지 자체적으로 실행할 수 있다.

유용한 아키텍처 원칙은 의사결정 시간 범위(Decision Horizon)에 따라 지능을 배치하는 것이다. 즉각적인 물리적 반응은 로봇 가까이에 위치해야 한다. 여러 로봇이나 특정 지역의 운영 영역과 관련된 결정은 주로 포그 수준에 배치된다. 플릿 전체의 이력, 사이트 간 지식(Cross-Site Knowledge), 대규모 모델(Large Model), 광범위한 최적화가 필요한 결정은 자연스럽게 클라우드 방향으로 이동한다. 이를 통해 공간적·시간적 추론 범위가 점차 확대되는 지능 계층 구조가 형성된다.

데이터는 계층 구조를 따라 위쪽으로 이동하면서 점차 추상화된 형태로 변환된다. 원시 카메라 영상, 라이다(LiDAR) 측정값, 모터 상태, 지역 관측 정보는 일반적으로 엣지에서 처리된다. 포그 계층은 객체 추적(Object Track), 의미론적 이벤트(Semantic Event), 로봇 상태, 지도 변화, 운용 요약 정보를 전달받을 수 있다. 클라우드는 모든 원시 센서 스트림을 지속적으로 수집하기보다는 압축된 텔레메트리, 학습된 표현(Learned Representation), 성능 통계, 사고 정보, 선별된 데이터셋을 전달받을 수 있다.

명령과 지식은 반대 방향으로 흐른다. 클라우드 시스템은 모델(Model), 정책(Policy), 지도(Map), 설정 파라미터(Configuration Parameter), 플릿 전체 목표(Fleet-Wide Objective)를 배포할 수 있다. 포그 시스템은 이러한 상위 목표를 사이트 수준의 조정 및 자원 의사결정으로 변환한다. 최종적으로 개별 로봇은 할당된 임무와 상황 정보를 궤적(Trajectory), 액추에이터 명령(Actuator Command), 물리적 행동(Physical Action)으로 변환한다. 따라서 지능은 단순한 클라이언트-서버(Client-Server) 구조가 아니라 양방향으로 순환한다.

통신 장애(Communication Failure)는 예외적인 사건이 아니라 정상적인 운용 조건의 하나로 취급해야 한다. 클라우드 연결이 사라지는 경우 포그 계층은 가능한 범위에서 핵심 사이트 운영을 유지해야 한다. 포그 계층까지 사용할 수 없게 되면 개별 로봇은 자체적으로 실행할 수 있는 지역 행동(Local Behavior)으로 점진적으로 성능을 저하시켜야 한다. 임무 지속, 제어된 정지(Controlled Stop), 지역 주행(Local Navigation), 텔레메트리 버퍼링(Telemetry Buffering), 이후 상태 조정(State Reconciliation)은 운용 회복탄력성(Operational Resilience)을 유지하기 위한 중요한 메커니즘이다.

일관성 요구사항(Consistency Requirement) 역시 계층마다 다르다. 모터 제어와 안전 상태는 엄격하게 통제된 지역 타이밍을 요구할 수 있지만 플릿 분석(Fleet Analytics)은 지연된 동기화를 허용할 수 있다. 공유 지도, 임무 소유권(Mission Ownership), 교통 예약(Traffic Reservation), 분산 작업 상태(Distributed Task State)는 오래된 정보가 충돌을 일으킬 수 있는 중간 범주에 속한다. 따라서 분산 지능에서는 어떤 데이터에 강한 일관성(Strong Consistency)이 필요하고 어떤 정보에 최종적 일관성(Eventual Consistency)을 적용할 수 있는지 명확하게 정의해야 한다.

이에 따라 지연시간 예산(Latency Budget)은 네트워크 자체가 아니라 기능별로 정의되어야 한다. 평균 지연시간이 매우 우수한 클라우드 연결이 존재하더라도 지터(Jitter), 통신 단절, 라우팅 변동성이 발생할 수 있기 때문에 충돌 회피(Collision Avoidance)를 원격에 배치하는 것은 적절하지 않다. 반대로 모든 최적화 알고리즘을 로봇에 탑재하면 제한된 엣지 자원을 낭비하게 된다. 아키텍처의 품질은 각 기능에서 허용 가능한 최대 지연시간과 장애 특성에 연산 위치를 얼마나 적절하게 대응시키는가에 달려 있다.

지능이 CPU, GPU, 메모리, 저장장치, 네트워크 대역폭, 전력과 경쟁하기 때문에 자원 관리(Resource Management) 역시 핵심적인 문제가 된다. 엣지 노드는 안전 핵심(Safety-Critical) 및 임무 핵심(Mission-Critical) 워크로드를 우선 처리하고, 포그 노드는 지역 가속기(Local Accelerator)를 활용하여 더 큰 추론 또는 최적화 작업을 동적으로 할당할 수 있다. 클라우드 인프라는 학습, 시뮬레이션, 과거 데이터 처리, 연산 집약적인 플릿 전체 분석을 위한 탄력적인 자원을 제공한다.

분산 지능은 협력 학습(Collaborative Learning)을 위한 자연스러운 기반도 제공한다. 로봇은 현장에서 경험을 수집하고, 사이트 인프라는 지식을 집계하거나 필터링하며, 클라우드 시스템은 분산된 운용 경험으로부터 더욱 광범위한 모델을 구축할 수 있다. 이러한 기반은 연합 학습(Federated Learning), 가십 기반 지식 교환(Gossip-Based Knowledge Exchange), 분산 의미 지도(Distributed Semantic Map), 계층적 의사결정(Hierarchical Decision-Making), 다중 에이전트 강화학습(Multi-Agent Reinforcement Learning)과 같은 기술로 확장될 수 있다.

보안 경계(Security Boundary)는 컴퓨팅 계층 구조를 따라 설계되어야 한다. 로봇은 감독 인프라(Supervisory Infrastructure)에서 수신한 명령을 인증해야 하고, 포그 노드는 참여 로봇의 신원을 검증해야 하며, 클라우드 서비스는 플릿 및 사이트의 신원(Identity)을 관리해야 한다. 불필요한 민감 원시 데이터는 엣지에 유지하고 특징(Feature), 이벤트(Event), 그래디언트(Gradient), 비식별화된 요약 정보(Sanitized Summary)만 상위 계층으로 전송할 수 있다. 따라서 명확한 신뢰 경계(Trust Boundary)를 설계한다면 분산 구조는 개인정보 보호 능력을 향상시킬 수 있다.

관측 가능성(Observability)은 모든 계층에 걸쳐 확보되어야 한다. 분산 지능에서 발생하는 장애는 하나의 구성요소만으로 설명하기 어려운 경우가 많기 때문이다. 운영자는 어떤 로봇이 관측 정보를 생성했는지, 어떤 포그 서비스가 이를 변환했는지, 어떤 정책이나 모델이 의사결정에 영향을 주었는지, 그리고 어떤 명령이 최종적으로 물리 시스템에 전달되었는지를 재구성할 수 있어야 한다. 공통 타임스탬프(Common Timestamp), 추적 식별자(Trace Identifier), 동기화 로그(Synchronized Log), 모델 버전(Model Version), 임무 식별자(Mission Identifier)는 계층 간 진단을 가능하게 한다.

확장성(Scalability)은 이러한 아키텍처를 도입하는 가장 강력한 이유 중 하나이다. 중앙집중형 컨트롤러(Centralized Controller)는 소규모 플릿에서는 효과적으로 동작할 수 있지만 로봇 수가 증가하면 통신, 연산 또는 가용성(Availability)의 병목이 될 수 있다. 계층적 분산(Hierarchical Distribution)을 적용하면 지역 그룹이 상당한 양의 정보를 자체적으로 처리하고 상위 계층은 집계된 상태(Aggregated State)를 중심으로 동작할 수 있으므로 대규모 다중 로봇 시스템으로 확장하기가 쉬워진다.

결과적으로 이러한 시스템은 네트워크로 연결된 세 개의 독립적인 컴퓨터로 이해해서는 안 된다. 이는 긴급성(Urgency), 지역성(Locality), 연산 비용(Computational Cost), 연결성(Connectivity), 운용 위험(Operational Risk)에 따라 책임이 이동하는 연속적인 지능 체계(Intelligence Continuum)이다. 엣지 지능은 즉각적인 물리적 자율성을 보호하고, 포그 지능은 지역 집단 행동(Local Collective Behavior)을 가능하게 하며, 클라우드 지능은 글로벌 학습(Global Learning), 최적화, 장기적인 지식 축적을 담당한다.

성숙한 구현에서는 각 상위 계층에 대한 안전한 의존성을 가능한 한 최소화하면서 동시에 상위 계층의 능력을 최대한 활용해야 한다. 개별 로봇은 독립적으로 안전한 상태를 유지하고, 지역 플릿은 외부 네트워크가 중단되어도 운영을 지속하며, 클라우드 서비스는 시스템의 기본적인 생존 가능성(Survivability)을 결정하는 것이 아니라 이를 향상시키는 역할을 담당해야 한다. 이러한 원칙은 회복탄력적인 분산 로봇 지능(Resilient Distributed Robotic Intelligence)을 단순히 기존 중앙집중형 소프트웨어를 여러 컴퓨터에 나누어 배치한 구조와 구분한다.

궁극적으로 엣지-포그-클라우드 아키텍처(Edge-Fog-Cloud Architecture)는 점점 더 지능화되는 로봇 플릿을 위한 연산 기반을 제공한다. 개별 로봇은 현장에서 즉각적으로 반응하고, 여러 로봇으로 구성된 그룹은 집단적으로 추론하며, 조직 전체는 축적된 경험으로부터 글로벌하게 학습할 수 있다. 지연시간, 일관성, 자율성, 보안, 자원 할당을 통합적으로 설계하면 분산 지능은 독립적인 자율 로봇의 집합을 확장 가능하고 회복탄력적인 플릿 수준 지능(Fleet-Wide Intelligence)으로 전환하는 핵심 메커니즘이 된다.

## 06.02 Federated Learning for Robot Fleet [w/Code]

![](images/image2.png){width="7.268055555555556in" height="7.268055555555556in"}

연합 학습(Federated Learning)은 모든 로봇이 원시 운용 데이터(Raw Operational Data)를 중앙집중형 학습 저장소(Centralized Training Repository)에 업로드하지 않고도 로봇 플릿(Robot Fleet)이 공유 인공지능 모델(Shared Artificial Intelligence Model)을 개선할 수 있도록 한다. 각 로봇 또는 지역 사이트(Local Site)는 운용 중 수집한 관측 데이터를 이용해 모델을 학습하며, 모델 파라미터(Model Parameter), 그래디언트(Gradient), 또는 압축된 업데이트(Compact Update)만 집계 서비스(Aggregation Service)와 교환한다. 이러한 접근 방식은 분산 지능(Distributed Intelligence)을 분산 실행(Distributed Execution)에서 분산 학습(Distributed Learning)으로 확장한다.

기존의 중앙집중형 학습 파이프라인(Centralized Learning Pipeline)에서는 로봇이 수집한 센서 기록(Sensor Recording), 궤적(Trajectory), 이벤트(Event), 레이블(Label)을 중앙 데이터센터(Central Data Center)로 전송하여 모델 학습을 수행한다. 이러한 아키텍처는 학습 관리를 단순화하지만 상당한 네트워크 트래픽, 저장공간 요구사항, 개인정보 보호 문제, 데이터 거버넌스(Data Governance)의 복잡성을 발생시킬 수 있다. 연합 학습은 플릿 전체의 협력을 유지하면서 학습 과정의 일부를 로봇 또는 지역 엣지 인프라(Local Edge Infrastructure)로 이동시킨다.

일반적인 연합 학습 주기(Federated Learning Cycle)는 글로벌 모델(Global Model)을 플릿 학습 서버(Fleet Learning Server)에서 선택된 참여 로봇으로 배포하면서 시작된다. 각 로봇은 로컬에 저장된 데이터셋(Local Dataset)을 이용하여 정해진 횟수만큼 모델을 학습하거나 미세조정(Fine-Tuning)한다. 이후 생성된 로컬 모델 업데이트(Local Model Update)는 집계 노드(Aggregation Node)로 전송되고, 집계 노드는 여러 참여자의 업데이트를 결합하여 다음 학습 라운드(Training Round)에 사용할 개선된 글로벌 모델을 생성한다.

일반적으로 페드애버리지(FedAvg)라고 부르는 연합 평균화(Federated Averaging)는 기본적인 집계 메커니즘(Aggregation Mechanism)을 나타낸다. 서버는 특정 로봇 하나의 모델을 선택하는 대신 여러 참여 모델의 파라미터를 결합하며, 일반적으로 각 로봇이 보유한 로컬 학습 데이터의 양에 따라 기여도를 가중한다. 이러한 로컬 학습(Local Training)과 글로벌 집계(Global Aggregation)를 반복하면 개별 데이터셋을 직접 중앙으로 수집하지 않고도 여러 로봇이 획득한 지식을 공통 모델(Common Model)에 반영할 수 있다.

로봇 플릿은 개별 로봇이 서로 다른 운용 조건을 반복적으로 경험하기 때문에 연합 학습에 특히 적합한 환경을 제공한다. 로봇마다 서로 다른 조명, 바닥 재질, 날씨, 장애물, 사람의 행동, 적재물(Payload), 장비 배치, 센서 특성을 관측할 수 있다. 로컬 학습은 이러한 경험을 포착하고, 집계 과정은 다양한 관측 경험을 보다 광범위한 플릿의 성능 향상에 활용할 수 있는 지식으로 변환하려고 한다.

그러나 로봇 데이터는 독립적이고 동일한 분포(Independent and Identically Distributed)를 따르는 경우가 드물다. 한 창고 로봇은 주로 좁은 통로를 관측하고, 다른 로봇은 하역장(Loading Dock) 주변에서 동작하며, 실외 로봇은 비, 그림자, 경사면, 식생 등을 경험할 수 있다. 이러한 비독립·비동일분포 데이터(Non-IID Data)는 로컬에서 최적화된 모델들이 서로 다른 방향으로 이동하여 글로벌 수렴(Global Convergence)을 느리게 하거나 불안정하게 만들 수 있기 때문에 플릿 연합 학습의 핵심적인 과제 중 하나이다.

플릿 이질성(Fleet Heterogeneity)은 하드웨어와 소프트웨어 수준에서도 존재한다. 로봇마다 서로 다른 프로세서, GPU 성능, 센서, 펌웨어 버전, 배터리 용량, 네트워크 연결을 사용할 수 있다. 따라서 연합 학습에서는 모든 로봇이 모든 학습 라운드에 동일하게 참여한다고 가정할 수 없다. 참여자 선택(Participant Selection)은 연산 자원의 가용성, 통신 품질, 충전 상태, 운용 작업 부하(Operational Workload), 모델 호환성(Model Compatibility), 로컬 데이터의 관련성을 고려해야 한다.

엣지-포그-클라우드 계층 구조(Edge-Fog-Cloud Hierarchy)는 연합 학습을 위한 실용적인 배포 구조를 제공한다. 개별 로봇은 엣지에서 경량 로컬 학습(Lightweight Local Training)을 수행하고, 사이트 수준의 포그 서버(Fog Server)는 인접한 로봇들의 업데이트를 집계할 수 있다. 이후 클라우드는 여러 시설 또는 지리적 지역의 지식을 다시 통합할 수 있다. 계층적 집계(Hierarchical Aggregation)는 광역 통신량을 줄이면서 훨씬 큰 플릿의 경험을 반영하는 모델을 구축할 수 있게 한다.

학습 워크로드(Training Workload)는 항상 로봇의 안전한 운용보다 낮은 우선순위를 가져야 한다. 위치추정(Localization), 지각(Perception), 경로계획(Planning), 제어(Control), 안전 프로세스(Safety Process)는 예측 가능한 연산 자원을 필요로 하지만 연합 학습은 일반적으로 지연하거나 중단할 수 있다. 따라서 로컬 학습은 충전 중, 대기 시간, 유지보수 시간대(Maintenance Window), 또는 GPU 사용률이 낮은 시간에 수행할 수 있다. 자원 인식 스케줄링(Resource-Aware Scheduling)은 학습 워크로드가 실시간 로봇 기능을 저하시키는 것을 방지한다.

모델 크기와 플릿 규모가 증가할수록 통신 효율성(Communication Efficiency)은 더욱 중요해진다. 수백 대의 로봇이 전체 신경망 파라미터(Neural Network Parameter)를 반복적으로 전송하면 상당한 대역폭을 소비할 수 있다. 그래디언트 압축(Gradient Compression), 파라미터 희소화(Parameter Sparsification), 양자화(Quantization), 선택적 계층 업데이트(Selective Layer Update), 통신 빈도 감소, 여러 에포크(Epoch)에 걸친 로컬 학습을 이용하면 네트워크 요구량을 줄일 수 있다. 아키텍처는 통신량 감소와 모델 정확도 및 수렴 속도 사이의 균형을 고려해야 한다.

비동기 연합 학습(Asynchronous Federated Learning)은 모든 로봇이 동시에 참여할 수 없는 경우 유용하다. 선택된 모든 로봇이 로컬 학습을 완료할 때까지 기다리는 대신 집계 서비스는 참여 로봇이 사용 가능한 시점마다 업데이트를 수신할 수 있다. 이는 실제 운용 플릿의 자원 활용도를 향상시키지만 일부 로봇이 이전 글로벌 모델을 기반으로 학습하면서 오래된 업데이트(Stale Update) 문제가 발생할 수 있다. 따라서 모델 버전 추적(Version Tracking)과 업데이트 노후도를 고려한 집계(Staleness-Aware Aggregation)가 중요한 요소가 된다.

로봇은 학습 라운드 중에 연결이 끊어지거나, 운용에서 제외되거나, 배터리가 부족해지거나, 더 높은 우선순위의 임무를 수행할 수 있으므로 장애 허용성(Failure Tolerance)이 필수적이다. 일부 참여자가 업데이트를 반환하지 않더라도 글로벌 학습 과정은 계속 진행되어야 한다. 참여 임계값(Participation Threshold), 마감시간(Deadline), 재시도 정책(Retry Policy), 체크포인팅(Checkpointing), 부분 집계(Partial Aggregation)는 개별 로봇의 장애가 플릿 전체 학습을 차단하지 않도록 하며 실제 운용 연합 학습 시스템과 이상적인 실험실 환경을 구분하는 요소가 된다.

연합 학습은 데이터 지역성(Data Locality)을 향상시키지만 개인정보 보호(Privacy)를 자동으로 보장하는 것은 아니다. 특히 민감한 관측 정보가 포함된 경우 모델 업데이트를 통해 로컬 학습 데이터의 일부 정보가 노출될 가능성이 있다. 보안 집계(Secure Aggregation)는 중앙 서버가 개별 로봇의 업데이트를 직접 확인하지 못하도록 할 수 있으며, 차등 개인정보 보호(Differential Privacy)는 제어된 노이즈(Controlled Noise)를 추가하여 정보 유출을 줄일 수 있다. 이러한 기술은 추가적인 연산 비용과 정확도 사이의 절충관계(Trade-Off)를 발생시키므로 응용 분야별로 평가해야 한다.

손상된 참여자가 악의적이거나 조작된 업데이트를 제출할 수 있기 때문에 보안(Security) 역시 중요하다. 모델 포이즈닝(Model Poisoning), 백도어 삽입(Backdoor Insertion), 손상된 그래디언트(Corrupted Gradient), 신원 위조(Identity Spoofing)는 공유 플릿 모델에 영향을 줄 수 있다. 로봇 인증(Robot Authentication), 서명된 업데이트(Signed Update), 보안 통신(Secure Communication), 이상 탐지(Anomaly Detection), 업데이트 검증(Update Validation), 강건한 집계(Robust Aggregation), 참여자 평판 메커니즘(Participant Reputation Mechanism)을 통해 이러한 위험을 줄일 수 있다. 따라서 학습 인프라는 플릿 보안 경계(Fleet Security Boundary)의 일부로 취급해야 한다.

모든 로컬 업데이트가 자동으로 글로벌 모델에 영향을 주도록 해서는 안 된다. 손상된 카메라, 잘못 보정된 라이다(LiDAR), 비정상적인 소프트웨어 설정, 손상된 데이터셋을 사용하는 로봇은 통계적으로는 유효하지만 운용 측면에서는 해로운 업데이트를 생성할 수 있다. 품질 게이트(Quality Gate)는 로컬 데이터셋의 특성, 검증 지표(Validation Metric), 업데이트 크기(Update Magnitude), 센서 상태(Sensor Health), 소프트웨어 구성을 평가한 후 해당 업데이트가 집계에 참여할 수 있는지 결정할 수 있다.

모델 개인화(Model Personalization)는 하나의 글로벌 모델이 모든 로봇에 최적의 성능을 제공할 수 없는 상황을 해결한다. 플릿은 광범위하게 활용할 수 있는 지식을 포함한 공통 백본(Common Backbone)을 유지하면서 특정 계층, 파라미터, 보정 구성요소(Calibration Component)를 각 로봇의 환경에 맞게 유지할 수 있다. 이러한 접근 방식은 로봇들이 기본적인 작업을 공유하지만 운용 환경, 하드웨어 구성 또는 임무 프로파일(Mission Profile)이 상당히 다른 경우 유용하다.

연합 학습은 다양한 플릿 지능(Fleet Intelligence) 기능을 지원할 수 있다. 지각 모델(Perception Model)은 분산된 환경 관측으로부터 개선될 수 있고, 이상 탐지기(Anomaly Detector)는 여러 장비에서 수집된 패턴을 학습할 수 있으며, 배터리 모델(Battery Model)은 서로 다른 듀티 사이클(Duty Cycle)을 반영할 수 있다. 또한 주행 관련 모델은 다양한 운용 조건으로부터 이점을 얻을 수 있다. 가장 적합한 대상은 플릿 경험을 통해 성능을 개선하면서 의미 있는 로컬 학습과 통제된 검증이 가능한 기능이다.

검증(Validation)은 집계(Aggregation)와 분리되어야 한다. 연합 최적화 목표(Federated Optimization Objective)가 향상되었다는 이유만으로 업데이트된 글로벌 모델을 자동으로 배포해서는 안 된다. 후보 모델(Candidate Model)은 대표적인 검증 데이터셋, 시뮬레이션 시나리오, 회귀 테스트(Regression Test), 안전 제약조건(Safety Constraint), 필요에 따라 섀도 모드 운용(Shadow-Mode Operation)을 통해 평가되어야 한다. 사전에 정의된 승인 기준(Acceptance Criteria)을 충족한 모델만 실제 운용 플릿에 단계적으로 배포되어야 한다.

따라서 모델 생명주기 관리(Model Lifecycle Management)는 연합 학습과 밀접하게 연결된다. 모든 글로벌 및 로컬 모델은 식별 가능한 버전, 학습 설정(Training Configuration), 참여 로봇 집합, 집계 이력(Aggregation History), 검증 결과, 배포 상태(Deployment Status)를 가져야 한다. 배포 이후 성능이 저하되는 경우 운영자는 어떤 학습 라운드에서 변화가 발생했는지 확인하고 통제된 롤백(Controlled Rollback)을 통해 이전에 검증된 모델로 복원할 수 있어야 한다.

완전한 학습 루프(Learning Loop)는 단순한 로컬 학습과 파라미터 평균화를 넘어선다. 운용 중인 로봇이 경험을 생성하고, 로컬 시스템은 적절한 학습 데이터를 선별하며, 엣지 노드는 업데이트를 계산한다. 포그 또는 클라우드 인프라는 분산된 지식을 집계하고, 검증 시스템은 후보 모델을 평가하며, 배포 서비스(Deployment Service)는 승인된 지능을 다시 플릿에 전달한다. 이후 새로운 운용 경험이 다음 주기를 시작하면서 지속적인 플릿 학습 과정(Continuous Fleet Learning Process)이 형성된다.

대규모 환경에서 연합 학습은 플릿을 중앙에서 개발된 모델을 단순히 사용하는 로봇들의 집합에서 분산형 지식 생산 시스템(Distributed Knowledge-Producing System)으로 변화시킨다. 각각의 로봇은 자율적인 물리 에이전트(Autonomous Physical Agent)이면서 동시에 집단 지능(Collective Intelligence)에 기여하는 구성원이 된다. 아키텍처의 목표는 단순히 학습을 분산시키는 것이 아니라 지역 경험(Local Experience), 글로벌 지식(Global Knowledge), 운용 회복탄력성(Operational Resilience), 개인정보 보호, 보안, 통제된 배포를 지속 가능한 학습 시스템(Sustainable Learning System)으로 통합하는 것이다.

적절하게 설계된 연합 학습은 원시 운용 데이터를 주로 데이터가 생성된 위치 가까이에 유지하면서 플릿 지능을 지속적으로 향상시킬 수 있도록 한다. 엣지 로봇(Edge Robot)은 지역 경험을 제공하고, 포그 인프라(Fog Infrastructure)는 사이트 수준의 학습을 조정하며, 클라우드 시스템(Cloud System)은 조직 전체의 지식을 통합한다. 이를 통해 학습 자체가 전체 다중 로봇 시스템(Multi-Robot System)의 분산 능력(Distributed Capability)이 되는 지속적으로 발전하는 로봇 플릿을 위한 확장 가능한 기반을 구축할 수 있다.

## 06.03 Gossip Protocol Based Fleet Knowledge Sharing [w/Code]

![](images/image3.png){width="7.268055555555556in" height="7.268055555555556in"}

대규모 로봇 플릿(Robot Fleet)에서는 유용한 지식(Knowledge)이 하나의 중앙 서버(Central Server)에서 생성되는 것이 아니라 여러 위치에서 지속적으로 생성된다. 각 로봇은 장애물, 교통 상황, 환경 변화, 위치추정 불확실성(Localization Uncertainty), 임무 결과, 장비 상태 및 기타 운용 이벤트(Operational Event)를 관측한다. 가십 프로토콜 기반 지식 공유(Gossip Protocol-Based Knowledge Sharing)는 모든 로봇이 중앙 조정기(Central Coordinator)와 직접 통신하지 않고도 이러한 지역적으로 생성된 정보를 플릿 전체에 점진적으로 전파할 수 있는 분산형 메커니즘(Decentralized Mechanism)을 제공한다.

가십 프로토콜(Gossip Protocol)은 반복적인 피어 투 피어 교환(Peer-to-Peer Exchange)을 통해 정보가 확산되는 방식에서 착안한 것이다. 각 통신 기회마다 로봇은 하나 이상의 인접 피어(Neighboring Peer)를 선택하여 현재 보유한 지식의 일부를 교환한다. 이후 해당 피어들은 다른 로봇들과 다시 통신하면서 여러 라운드에 걸쳐 정보가 네트워크 전체로 확산된다. 이 과정은 중앙에서 스케줄링되지 않는 확률적(Probabilistic) 방식이지만 충분한 반복 교환을 통해 정보를 플릿의 상당 부분에 전달할 수 있다.

이러한 접근 방식은 중앙집중형 발행-구독(Centralized Publish-Subscribe) 또는 데이터베이스 동기화(Database Synchronization) 아키텍처와 근본적으로 다르다. 중앙집중형 시스템에서는 로봇이 정보를 권위 있는 서비스(Authoritative Service)에 전송하고 해당 서비스가 이를 저장하고 다시 배포한다. 가십 기반 시스템에서는 지식이 참여자 사이에서 직접 이동할 수 있으므로 단일 통신 경로나 중앙 서비스에 대한 의존성을 줄일 수 있다. 이러한 구조는 인프라 연결이 간헐적으로 끊어지는 상황에서도 로봇이 협력을 지속해야 하는 분산 지능(Distributed Intelligence)에 자연스럽게 적합하다.

플릿 지식(Fleet Knowledge)은 다양한 형태의 정보를 포함할 수 있다. 로봇은 최근 감지된 장애물, 차단된 통로, 지도 변화, 의미론적 랜드마크(Semantic Landmark), 혼잡도 추정치, 충전소 가용성, 위치추정 신뢰도(Localization Confidence), 임무 상태, 고장 관측 정보 또는 학습된 운용 통계를 교환할 수 있다. 카메라나 라이다(LiDAR)의 원시 데이터를 불필요하게 복제하면 통신 및 저장 자원을 빠르게 소모하므로 가십은 일반적으로 연속적인 원시 센서 스트림보다 압축된 지식 표현(Compact Knowledge Representation)을 배포해야 한다.

따라서 지식 항목(Knowledge Item)에는 구조화된 메타데이터(Structured Metadata)가 필요하다. 공유 관측 정보에는 원본 로봇(Origin Robot), 생성 시간, 공간 위치, 지식 유형, 신뢰도, 버전, 만료 시간(Expiration Time), 고유 식별자(Unique Identifier) 등이 포함될 수 있다. 이러한 메타데이터를 통해 수신 로봇은 해당 정보가 새로운 것인지, 중복된 것인지, 오래된 것인지, 충돌하는 것인지 또는 현재 임무와 관련이 없는지를 판단할 수 있다. 명확한 출처 정보(Provenance)와 시간 정보가 없으면 분산형 지식 전파 과정에서 오래된 관측 정보가 잘못된 플릿 전체 정보로 변할 수 있다.

단순한 가십 주기(Gossip Cycle)는 피어 탐색(Peer Discovery), 피어 선택(Peer Selection), 지식 비교(Knowledge Comparison), 교환(Exchange), 로컬 상태 업데이트(Local State Update)로 구성된다. 로봇은 먼저 사용 가능한 플릿 통신 네트워크를 통해 접근 가능한 피어를 식별한다. 이후 피어의 일부를 선택하고 서로 보유한 지식 가운데 어떤 부분이 다른지 판단한다. 누락되었거나 더 새로운 항목을 교환하고 검증하여 수신 로봇의 로컬 지식 저장소(Local Knowledge Store)에 통합한 후 다음 가십 주기를 시작한다.

푸시(Push), 풀(Pull), 푸시-풀(Push-Pull)은 일반적인 교환 방식이다. 푸시 가십(Push Gossip)에서는 로봇이 선택한 지식을 다른 로봇에 능동적으로 전송한다. 풀 가십(Pull Gossip)에서는 로봇이 현재 보유하지 않은 정보를 요청한다. 푸시-풀 방식은 하나의 상호작용에서 두 동작을 결합하며 각 통신 세션에서 양방향의 지식 차이를 해결할 수 있기 때문에 수렴(Convergence)을 가속할 수 있다. 적절한 방식은 대역폭, 지식 크기, 네트워크 토폴로지(Network Topology), 업데이트 빈도에 따라 결정된다.

무작위 피어 선택(Random Peer Selection)은 단순성과 회복탄력성(Resilience)을 제공하지만 로봇 플릿에서는 토폴로지 인식 선택(Topology-Aware Selection)을 활용할 수 있다. 로봇은 인접 피어, 주변 구역에서 운용되는 로봇, 동일한 임무 그룹의 구성원 또는 서로 다른 지식 버전을 가진 피어를 우선적으로 선택할 수 있다. 통신 품질, 네트워크 비용, 물리적 거리, 임무 관련성, 이전 교환 이력도 피어 선택에 영향을 줄 수 있다. 이를 통해 순수한 무작위 가십을 운용 상황을 인식하는 지식 전파 메커니즘으로 발전시킬 수 있다.

가십의 주요 장점은 자연스러운 확장성(Scalability)이다. 모든 로봇이 모든 업데이트를 다른 모든 로봇에 직접 전달하려고 하면 플릿 규모가 증가함에 따라 통신 복잡도가 빠르게 증가한다. 가십은 각 로봇이 상대적으로 적은 수의 피어와만 정보를 교환하도록 제한하면서도 반복적인 상호작용을 통해 정보가 전체 네트워크로 확산될 수 있도록 한다. 따라서 수백 또는 수천 개의 에이전트(Agent)로 구성된 플릿에서도 완전 연결형 통신 토폴로지(Fully Connected Communication Topology)를 구축하지 않고 지식을 배포할 수 있다.

가십 프로토콜은 본질적으로 장애 허용성(Fault Tolerance)도 높다. 특정 로봇의 연결이 일시적으로 끊어져도 여러 개의 전파 경로가 존재하기 때문에 정보가 다른 참여자에게 전달되는 과정이 반드시 중단되는 것은 아니다. 연결이 끊겼던 로봇이 다시 네트워크에 참여하면 이후의 교환을 통해 누락된 지식을 동기화할 수 있다. 모든 참여자가 지속적으로 연결될 필요가 없기 때문에 실외 플릿, 다중 건물 운용, 일시적인 네트워크 분할(Network Partition), 모바일 애드혹 환경(Mobile Ad Hoc Environment)에 적합하다.

그러나 이러한 회복탄력성에는 중요한 절충관계(Trade-Off)가 존재한다. 가십은 일반적으로 즉각적인 일관성(Immediate Consistency)이 아니라 최종적 일관성(Eventual Consistency)을 제공한다. 정보가 전파되는 동안 두 로봇이 서로 다른 버전의 플릿 지식을 보유할 수 있다. 이러한 특성은 많은 관측 정보나 통계 요약에서는 허용될 수 있지만 일부 안전 핵심 의사결정(Safety-Critical Decision)에는 적합하지 않다. 비상 정지(Emergency Stop), 배타적 자원 소유권(Exclusive Resource Ownership), 즉각적인 충돌 회피(Immediate Collision Avoidance)는 확률적 가십 전파에만 의존해서는 안 된다.

따라서 지식 최신성(Knowledge Freshness)을 명시적으로 관리해야 한다. 유효시간(Time-to-Live)은 운용 관련성이 사라진 관측 정보를 제거할 수 있으며, 타임스탬프(Timestamp)와 시퀀스 번호(Sequence Number)는 최신 정보와 오래된 복사본을 구분하는 데 사용된다. 일시적인 장애물 관측은 몇 초 또는 몇 분 동안만 유효할 수 있지만 지속적인 의미론적 랜드마크는 훨씬 오랫동안 유효할 수 있다. 따라서 만료 정책(Expiration Policy)은 각 지식 범주의 의미와 예상 수명에 따라 결정해야 한다.

동일한 정보가 여러 전파 경로를 통해 도착할 수 있기 때문에 중복 억제(Duplicate Suppression) 역시 중요하다. 고유 지식 식별자, 버전 벡터(Version Vector), 시퀀스 카운터(Sequence Counter), 해시(Hash), 압축된 멤버십 요약(Compact Membership Summary)을 사용하면 로봇이 이미 보유한 정보를 식별할 수 있다. 중복 탐지가 없으면 가십 트래픽이 변경되지 않은 지식의 반복적인 재전송으로 채워져 분산형 아키텍처가 제공하는 확장성의 장점이 감소할 수 있다.

실제 로봇 플릿에서는 지식 충돌(Conflicting Knowledge)을 피할 수 없다. 두 로봇이 서로 다른 시간이나 서로 다른 센서를 사용하여 동일한 통로, 객체, 지도 영역 또는 충전소를 관측하면 서로 다른 상태를 보고할 수 있다. 충돌 해결(Conflict Resolution)에서는 타임스탬프, 신뢰도, 센서 신뢰성(Sensor Reliability), 관측 빈도, 출처 평판(Source Reputation), 공간적 근접성(Spatial Proximity)을 고려할 수 있다. 일부 충돌은 하나의 관측 정보를 즉시 전역의 권위 있는 정보로 결정하기보다 여러 가설(Multiple Hypotheses)로 유지하는 것이 적절할 수 있다.

지식의 증가 속도가 사용 가능한 통신 용량보다 빨라지면 대역폭 최적화(Bandwidth Optimization)가 중요해진다. 로봇은 전체 지식 항목을 전송하기 전에 로컬 지식의 요약 정보를 교환하여 피어가 누락되거나 변경된 정보만 식별하도록 할 수 있다. 배칭(Batching), 압축(Compression), 우선순위 큐(Priority Queue), 델타 업데이트(Delta Update), 확률적 필터(Probabilistic Filter), 적응형 가십 주기(Adaptive Gossip Interval)를 이용하면 네트워크 트래픽을 추가로 줄일 수 있다. 가치가 높은 운용 지식은 빠르게 전파하고 우선순위가 낮은 과거 정보는 천천히 확산시킬 수 있다.

엣지-포그-클라우드 아키텍처(Edge-Fog-Cloud Architecture)는 가십 통신을 대체하는 것이 아니라 보완할 수 있다. 로봇들은 지역 운용 영역에서 직접 가십을 수행하고, 포그 노드(Fog Node)는 그룹 사이의 지식을 집계하거나 중계하는 고성능 피어(High-Capacity Peer)로 참여할 수 있다. 클라우드 서비스(Cloud Service)는 플릿 지식의 요약 정보를 주기적으로 받아 장기 분석을 수행하고 전역적으로 관련된 정보를 다시 각 사이트에 배포할 수 있다. 이를 통해 분산형 전파와 계층형 인프라를 결합한 하이브리드 아키텍처(Hybrid Architecture)를 구축할 수 있다.

네트워크 분할(Network Partition)은 이러한 설계의 가치를 잘 보여준다. 두 로봇 그룹 사이의 연결이 일시적으로 끊어졌지만 각 그룹 내부에서는 계속 운용할 수 있다고 가정할 수 있다. 각 그룹은 중앙 서버에 접근할 수 없다는 이유로 동작을 중단하는 대신 내부적으로 지식을 계속 교환할 수 있다. 연결이 복구되면 브리지 노드(Bridge Node) 또는 복귀한 로봇이 그동안 축적된 차이를 전파하여 전체 플릿을 다시 시작하지 않고도 분리되어 있던 지식 상태가 점진적으로 수렴하도록 할 수 있다.

분산형 전파는 잠재적인 정보 출처의 수를 증가시키기 때문에 보안(Security)이 필수적이다. 침해된 로봇(Compromised Robot)은 거짓 장애물, 조작된 고장 정보, 손상된 지도 업데이트 또는 잘못된 운용 통계를 플릿에 주입할 수 있으며 이러한 정보가 전체 플릿으로 확산될 수 있다. 따라서 로봇 신원(Robot Identity), 메시지 인증(Message Authentication), 디지털 서명(Digital Signature), 권한 부여 규칙(Authorization Rule), 무결성 검사(Integrity Check), 신뢰 정책(Trust Policy)을 통해 수신된 지식을 수락, 거부, 격리(Quarantine) 또는 낮은 신뢰도로 처리할지를 결정해야 한다.

지식 검증(Knowledge Validation)에는 물리적 및 의미론적 타당성(Physical and Semantic Plausibility)도 활용해야 한다. 하나의 로봇이 영구적인 벽이 사라졌다고 보고했지만 주변 로봇들이 반복적으로 해당 벽을 관측한다면 플릿은 이러한 비정상적인 주장을 사실로 간주하여 무조건 전파해서는 안 된다. 교차 관측 검증(Cross-Observation Verification), 신뢰도 누적(Confidence Accumulation), 출처 다양성(Source Diversity), 시간적 일관성(Temporal Consistency), 로컬 센서 확인을 활용하면 실제 환경 변화와 센서 오류 또는 악의적인 정보를 구분하는 데 도움이 된다.

지식이 플릿 전체에 어떻게 전파되는지를 이해하기 위해 관측 가능성(Observability)이 필요하다. 운영자는 특정 지식 항목이 어디에서 생성되었는지, 어떤 피어가 이를 전달했는지, 전파에 얼마나 많은 시간이 필요했는지, 현재 어떤 버전이 존재하는지, 일부 플릿 영역이 아직 동기화되지 않았는지를 파악할 수 있어야 한다. 전파 지연시간(Dissemination Latency), 수렴 비율(Convergence Ratio), 중복 트래픽(Duplicate Traffic), 피어 가용성(Peer Availability), 메시지 손실(Message Loss), 지식 수명(Knowledge Age)과 같은 지표를 사용하면 가십 동작을 측정 가능한 시스템 특성으로 관리할 수 있다.

가십 파라미터(Gossip Parameter)는 운용 조건에 따라 동적으로 조정할 수 있다. 안정적인 운용 중에는 로봇이 상대적으로 낮은 빈도로 정보를 교환할 수 있다. 중요한 지도 변화, 고장 패턴 또는 환경 위험이 발생하면 전파 속도를 일시적으로 증가시킬 수 있다. 마찬가지로 네트워크가 혼잡할 경우 팬아웃(Fan-Out)을 줄이거나 중요한 지식만 우선적으로 전달할 수 있다. 이러한 적응형 동작(Adaptive Behavior)을 통해 통신 비용을 플릿 이벤트의 실제 정보 가치와 긴급성에 맞출 수 있다.

가십 기반 지식 공유는 더욱 발전된 집단 지능(Collective Intelligence)을 위한 기반도 제공한다. 분산 의미 지도(Distributed Semantic Map), 분산형 이상 지식(Decentralized Anomaly Knowledge), 협력 학습 통계(Collaborative Learning Statistics), 로봇 능력 정보(Robot Capability Information), 로컬 정책 경험(Local Policy Experience)을 동일한 개념적 메커니즘을 통해 전파할 수 있다. 연합 학습(Federated Learning)과 결합하면 로봇은 중앙집중형 지능에 전적으로 의존하지 않으면서 운용 지식과 학습 관련 메타데이터를 함께 교환할 수 있다.

핵심 설계 원칙은 모든 플릿 지식이 하나의 권위 있는 경로(Authoritative Path)를 필요로 하는 것은 아니라는 점이다. 광범위한 전파가 필요하지만 일시적인 불일치를 허용할 수 있는 정보는 반복적인 지역 상호작용을 통해 효과적으로 확산될 수 있다. 반면 중요한 명령과 강한 일관성(Strong Consistency)이 필요한 자원 의사결정은 전용 조정 메커니즘(Dedicated Coordination Mechanism)을 유지하고, 가십은 분산 상황 인식(Decentralized Awareness)과 지식 확산(Knowledge Diffusion)을 담당하도록 할 수 있다. 이러한 정보 유형의 분리는 결정론적 보장(Deterministic Guarantee)이 필요한 영역에 확률적 통신을 잘못 사용하는 것을 방지한다.

적절하게 설계된 가십 프로토콜은 로봇 플릿이 분산형 지식 네트워크(Distributed Knowledge Network)로 동작할 수 있도록 한다. 각 로봇은 관측 정보를 제공하고, 피어로부터 정보를 수신하며, 정보의 관련성과 신뢰성을 평가하고, 유용한 지식을 다른 참여자에게 전달한다. 수많은 소규모 지역 교환을 통해 정보는 결국 많은 로봇에게 전달될 수 있으며, 모든 상호작용이 중앙 서버를 통과하지 않고도 플릿 전체 상황 인식(Fleet-Wide Situational Awareness)을 형성할 수 있다.

결과적으로 이러한 아키텍처는 통제된 일시적 불일치(Controlled Temporary Inconsistency)를 아키텍처적 절충관계로 받아들이면서 확장성, 회복탄력성, 자율성(Autonomy)을 향상시킨다. 메타데이터 관리(Metadata Management), 중복 억제, 충돌 해결, 보안, 적응형 통신, 엣지-포그-클라우드 통합과 결합된 가십 기반 공유는 개별 로봇이 획득한 지역 경험을 분산된 플릿 지식(Distributed Fleet Knowledge)으로 전환하며, 점점 더 분산화되는 다중 로봇 지능(Multi-Robot Intelligence)을 위한 중요한 통신 기반을 제공한다.

## 06.04 Distributed Map and Semantic Knowledge Sharing [w/Code]

![](images/image4.png){width="7.268055555555556in" height="7.268055555555556in"}

분산 지도 및 의미 지식 공유(Distributed Map and Semantic Knowledge Sharing)는 모든 로봇이 전체 작업 공간을 독립적으로 관측하지 않고도 여러 로봇이 공통된 운용 환경 표현(Common Representation)을 구축하고 갱신하며 활용할 수 있도록 한다. 각 로봇은 지역적으로 획득한 기하학적(Geometric), 위상학적(Topological), 의미론적(Semantic) 정보를 분산 지식 시스템(Distributed Knowledge System)에 제공하며, 이를 통해 개별 관측 정보를 점진적으로 풍부해지는 집단적 공간 이해(Collective Understanding of Space)로 발전시킬 수 있다.

일반적인 자율 로봇(Autonomous Robot)은 자체 센서에서 수집한 정보를 사용하여 위치추정(Localization)과 주행(Navigation)을 위한 지도를 유지한다. 그러나 다중 로봇 플릿(Multi-Robot Fleet)에서 이러한 방식은 탐색 작업을 중복시키고 각 로봇이 직접 방문한 영역으로 상황 인식(Situational Awareness)을 제한한다. 분산 매핑(Distributed Mapping)을 사용하면 한 로봇이 획득한 관측 정보를 다른 로봇도 활용할 수 있으므로 중복 탐색을 줄이면서 전체 플릿의 실질적인 지각 범위(Effective Perception Range)를 확장할 수 있다.

공유 표현(Shared Representation)은 서로 보완적인 여러 지도 계층(Map Layer)을 포함할 수 있다. 기하 지도(Geometric Map)는 점유 격자(Occupancy Grid), 포인트 클라우드(Point Cloud), 메시(Mesh) 또는 기타 공간 표현을 사용하여 물리적 구조를 나타낸다. 위상 지도(Topological Map)는 의미 있는 위치 사이의 연결 관계를 표현하며, 의미 지도(Semantic Map)는 공간 영역과 객체에 복도, 충전소, 문, 작업대, 제한 구역, 팔레트, 차량 또는 임시 장애물과 같은 개념을 연결한다.

의미 지식(Semantic Knowledge)은 환경 요소가 무엇을 의미하고 로봇이 해당 요소와 어떻게 상호작용해야 하는지를 표현함으로써 매핑을 단순한 기하학적 표현 이상으로 확장한다. 특정 영역이 물리적으로 통행 가능하다는 사실과 그 영역이 보행자 구역, 위험 지역, 하역장 또는 일방통행 구역이라는 사실을 아는 것은 서로 다르다. 기하 구조와 의미 속성(Semantic Attribute)을 결합하면 로봇은 거리와 충돌 제약조건뿐 아니라 운용 맥락(Operational Context)을 기반으로 임무와 주행에 관한 의사결정을 수행할 수 있다.

각 로봇은 먼저 탑재 센서(Onboard Sensor)와 위치추정 시스템을 사용하여 로컬 지도(Local Map)를 구축하거나 갱신한다. 로봇 플랫폼과 환경에 따라 카메라, 라이다(LiDAR), 레이더(Radar), 깊이 센서(Depth Sensor), 위성항법시스템(GNSS), 관성측정장치(IMU) 및 기타 센서가 관측에 사용될 수 있다. 로컬 처리(Local Processing)는 선택된 정보를 다른 참여자와 공유하기 전에 원시 측정값을 지도 특징(Map Feature), 랜드마크(Landmark), 점유 정보, 검출 객체, 의미 레이블(Semantic Label) 또는 환경 이벤트로 변환한다.

고해상도 카메라와 3차원 라이다(3D LiDAR)는 많은 양의 데이터를 생성할 수 있으므로 원시 센서 데이터를 지속적으로 공유하는 것은 일반적으로 비효율적이다. 따라서 분산 시스템에서는 압축된 지도 변화(Compact Map Change), 추출 특징(Extracted Feature), 의미 관측(Semantic Observation), 서브맵(Submap), 객체 추적(Object Track) 또는 선택된 키프레임(Keyframe)을 교환하는 것이 효과적이다. 목적은 다른 로봇이 이미 보유한 측정값을 반복적으로 전송하는 것이 아니라 집단 지식(Collective Knowledge)을 변화시키는 정보를 전달하는 것이다.

서로 다른 로봇의 관측 정보는 호환 가능한 공간 기준(Spatial Reference)을 사용해야 하므로 좌표 프레임 정렬(Coordinate-Frame Alignment)은 핵심 요소이다. 로봇들은 중첩 관측(Overlapping Observation), 공유 랜드마크(Shared Landmark), GNSS 기준, 피듀셜(Fiducial), 지도 정합 알고리즘(Map-Matching Algorithm)을 통해 서로 간의 변환 관계를 설정할 때까지 독립적인 로컬 프레임(Local Frame)을 유지할 수 있다. 프레임 정렬이 잘못되면 각 로봇의 로컬 지도가 개별적으로 정확하더라도 구조물이 중복되거나 장애물의 위치가 이동하고 의미 위치가 불일치할 수 있다.

서브맵 기반 공유(Submap-Based Sharing)는 확장 가능한 분산 매핑을 위한 실용적인 방법을 제공한다. 모든 센서 측정값을 하나의 거대한 글로벌 지도(Global Map)에 지속적으로 병합하는 대신 각 로봇은 기하 정보, 자세(Pose), 랜드마크 및 의미 정보를 포함하는 지역적으로 일관된 서브맵을 생성할 수 있다. 이러한 서브맵은 상대 변환(Relative Transformation)을 통해 교환되고 연결될 수 있으므로 지역적으로 생성된 정보의 출처(Provenance)를 유지하면서 글로벌 지식을 지속적으로 발전시킬 수 있다.

지도 병합(Map Merging)을 수행하려면 독립적으로 생성된 지도 사이에서 중첩 영역(Overlapping Region)을 탐지해야 한다. 특징 정합(Feature Matching), 스캔 정합(Scan Matching), 장소 인식(Place Recognition), 루프 폐쇄(Loop Closure) 기법 또는 의미 랜드마크를 이용하여 후보 대응 관계(Candidate Correspondence)를 식별할 수 있다. 신뢰할 수 있는 관계가 발견되면 상대 자세(Relative Pose)를 추정하고 지도 그래프(Map Graph)를 최적화할 수 있다. 잘못된 대응 관계는 공유 지도를 왜곡하고 이후 여러 로봇에 영향을 줄 수 있으므로 반드시 제거해야 한다.

지도 관계가 여러 로봇에 걸쳐 형성되면 분산 자세 그래프 최적화(Distributed Pose-Graph Optimization)가 중요해진다. 노드(Node)는 로봇 자세, 키프레임 또는 서브맵을 나타낼 수 있으며, 에지(Edge)는 오도메트리(Odometry), 관측, 루프 폐쇄 또는 로봇 간 제약조건(Inter-Robot Constraint)을 나타낸다. 최적화는 이러한 관계를 최대한 만족시키는 전역적으로 일관된 구성(Global Consistent Configuration)을 찾는다. 사용 가능한 자원에 따라 로봇, 포그 인프라(Fog Infrastructure) 또는 여러 분산 참여자의 조합에서 연산을 수행할 수 있다.

서로 다른 로봇이 동일한 객체나 영역에 대해 서로 다른 레이블 또는 신뢰도를 부여할 수 있으므로 의미 관측(Semantic Observation)에는 별도의 융합 전략(Fusion Strategy)이 필요하다. 하나의 로봇은 특정 객체를 팔레트로 분류하고 다른 로봇은 이를 단순히 알 수 없는 장애물로 판단할 수 있다. 의미 융합(Semantic Fusion)은 가장 최근의 레이블을 단순히 채택하기보다 클래스 확률(Class Probability), 관측 신뢰도, 센서 품질, 시간적 지속성(Temporal Persistence), 독립적인 로봇 사이의 일치도를 결합할 수 있다.

많은 운용 환경이 동적으로 변화하기 때문에 시간 정보(Temporal Information)는 특히 중요하다. 벽과 영구 인프라는 수년 동안 유지될 수 있지만 팔레트, 차량, 사람, 임시 장벽, 공사 구역은 몇 분 이내에도 변경될 수 있다. 따라서 공유 지식은 정적(Static), 준정적(Semi-Static), 동적(Dynamic) 정보를 구분해야 하며, 이를 통해 로봇이 오래된 임시 관측 정보를 환경의 영구적인 속성으로 잘못 판단하지 않도록 해야 한다.

버전 관리(Version Management)를 통해 로봇은 자신의 로컬 지도 상태가 전체 플릿과 동기화되어 있는지를 판단할 수 있다. 지도 타일(Map Tile), 서브맵, 의미 객체 또는 지식 영역(Knowledge Region)은 식별자, 타임스탬프(Timestamp), 개정 번호(Revision Number), 출처 정보를 포함할 수 있다. 이를 통해 로봇은 전체 지도를 반복적으로 다운로드하지 않고 누락되었거나 더 새로운 버전만 요청할 수 있다. 델타 기반 동기화(Delta-Based Synchronization)는 대부분의 지도 영역이 변경되지 않는 대규모 환경에서 통신 비용을 크게 줄인다.

충돌하는 지도 정보(Conflicting Map Information)를 단순히 기존 데이터에 덮어쓰는 방식으로 해결해서는 안 된다. 정보 불일치는 환경 변화, 위치추정 오류, 센서 성능 저하 또는 지도 요소 사이의 잘못된 연관 관계를 의미할 수 있다. 충돌 해결(Conflict Resolution)에서는 관측 최신성, 출처 신뢰도, 확인한 로봇 수, 위치추정 품질, 시간적 지속성을 고려할 수 있다. 중요한 충돌은 추가 관측을 통해 충분한 증거가 확보될 때까지 여러 가설(Hypothesis)로 유지할 수도 있다.

엣지-포그-클라우드 계층 구조(Edge-Fog-Cloud Hierarchy)는 분산 지도 관리를 위한 유용한 아키텍처를 제공한다. 개별 로봇은 엣지(Edge)에서 로컬 지도와 즉각적인 장애물 정보를 유지한다. 포그 인프라는 사이트 수준의 서브맵을 병합하고 연산 비용이 높은 최적화를 수행하며 관련 지역 업데이트를 배포할 수 있다. 클라우드 시스템(Cloud System)은 즉각적인 주행 안전에 필수적인 요소가 되지 않으면서 장기 지도(Long-Term Map), 사이트 간 의미 지식(Cross-Site Semantic Knowledge), 과거 버전 및 대규모 분석을 관리할 수 있다.

지식 배포(Knowledge Distribution)는 공간적·운용적으로 선택적이어야 한다. 특정 창고 구역에서 작업하는 로봇이 멀리 떨어진 시설의 모든 상세 업데이트를 받을 필요는 없다. 지도 정보는 지리적 영역, 층(Floor), 건물, 임무 영역 또는 의미적 관련성(Semantic Relevance)에 따라 분할할 수 있다. 로봇은 현재 위치와 예상 경로에 관련된 지식을 구독함으로써 메모리 사용량, 처리 부하 및 불필요한 네트워크 트래픽을 줄일 수 있다.

피어 투 피어(Peer-to-Peer) 및 가십 메커니즘(Gossip Mechanism)은 계층형 지도 서버(Hierarchical Map Server)를 보완할 수 있다. 인접 로봇들은 최근의 장애물 관측 또는 의미 변화를 직접 교환하여 중앙 연결이 불안정한 상황에서도 유용한 정보를 전파할 수 있다. 이후 포그 노드(Fog Node)는 이러한 로컬 업데이트를 권위 있는 사이트 지도(Authoritative Site Map)와 조정할 수 있다. 이러한 하이브리드 접근 방식(Hybrid Approach)은 빠른 분산 상황 인식과 통제된 장기 지도 일관성을 결합한다.

네트워크 중단(Network Interruption)이 기본적인 주행을 방해해서는 안 된다. 각 로봇은 다른 플릿 구성요소와 연결이 끊어진 상황에서도 안전한 운용을 지속할 수 있도록 충분한 로컬 캐시 지도(Local Cached Map)를 유지해야 한다. 새롭게 관측된 변화는 로컬에 저장한 후 통신이 복구되면 동기화할 수 있다. 연결이 끊어진 여러 그룹이 공유 지식을 독립적으로 수정한 경우 재연결 시 한 그룹의 상태를 다른 그룹에 단순히 덮어쓰는 것이 아니라 통제된 조정(Controlled Reconciliation)을 수행해야 한다.

지도 품질(Map Quality)은 명시적으로 표현되어야 한다. 기하학적 불확실성(Geometric Uncertainty), 위치추정 공분산(Localization Covariance), 의미 신뢰도(Semantic Confidence), 관측 경과 시간(Observation Age), 센서 출처, 검증 상태(Validation Status)는 공유 지식을 사용하는 시스템에 중요한 맥락을 제공한다. 주행 계획기(Navigation Planner)는 최근 확인된 장애물과 불확실한 과거 관측을 서로 다르게 처리할 수 있다. 따라서 지식 품질 메타데이터(Knowledge Quality Metadata)는 별도의 진단 정보가 아니라 지도 자체의 일부가 된다.

공유 지도는 로봇의 물리적 행동에 직접 영향을 주기 때문에 보안(Security)이 중요하다. 악의적이거나 손상된 참여자는 거짓 장애물을 삽입하거나 제한 구역을 제거하고, 충전소 위치를 변경하거나 잘못된 의미 레이블을 생성할 수 있다. 로봇 인증(Robot Authentication), 메시지 무결성(Message Integrity), 권한 부여(Authorization), 서명된 지도 업데이트(Signed Map Update), 출처 추적(Provenance Tracking), 이상 탐지(Anomaly Detection), 검증 규칙을 통해 신뢰할 수 없는 정보가 플릿 지식으로 수용되는 것을 방지해야 한다.

특히 카메라가 사람, 작업장 또는 민감한 운용 영역을 관측하는 경우 개인정보 보호(Privacy)도 의미 매핑에 영향을 줄 수 있다. 상세한 시각 데이터가 필요하지 않다면 로봇은 원시 영상 대신 가공된 의미 정보(Derived Semantic Information)를 공유할 수 있다. 로컬 처리를 통해 센서 관측을 객체 범주(Object Category), 점유 상태(Occupancy State), 익명화된 특징(Anonymized Feature), 통계 요약으로 변환한 후 배포하면 운용 가치를 유지하면서 데이터 노출을 줄일 수 있다.

분산 지도 공유는 플릿 작업 할당(Fleet Task Allocation) 및 조정(Coordination)과 연결될 때 더욱 강력해진다. 새롭게 발견된 차단 통로(Blocked Corridor)는 해당 위치를 한 번도 방문하지 않은 로봇의 경로계획에도 영향을 줄 수 있다. 충전소 고장이 감지되면 배터리 인식 스케줄링(Battery-Aware Scheduling)을 변경할 수 있으며, 새롭게 지정된 제한 구역은 임무 할당에 즉시 영향을 줄 수 있다. 따라서 공유 공간 지식(Shared Spatial Knowledge)은 단순한 주행 자원을 넘어 플릿 전체 의사결정(Fleet-Wide Decision-Making)의 입력 정보가 된다.

분산 매핑 시스템의 장애를 진단하려면 관측 가능성(Observability)이 필요하다. 운영자는 어떤 로봇이 지도 변경을 생성했는지, 언제 관측했는지, 어떤 변환(Transformation)을 통해 글로벌 프레임(Global Frame)에 배치되었는지, 어떤 참여자가 이를 확인했는지, 현재 어느 지도 버전에 포함되어 있는지를 파악할 수 있어야 한다. 그렇지 않으면 지도 병합 오류(Map Merge Error)가 조용히 전파되어 나중에 위치추정, 경로계획 또는 교통 관리 장애로 나타날 수 있다.

성능은 단순한 기하학적 지도 정확도만으로 평가해서는 안 된다. 로봇 간 지도 정렬 오차(Inter-Robot Map Alignment Error), 의미 분류 정확도(Semantic Classification Accuracy), 업데이트 전파 지연시간(Update Propagation Latency), 지도 수렴 시간(Map Convergence Time), 통신 대역폭, 오래된 정보 비율(Stale-Information Ratio), 병합 성공률(Merge Success Rate), 충돌 발생 빈도(Conflict Frequency), 저장공간 증가량(Storage Growth)과 같은 지표도 중요하다. 이러한 지표를 통해 플릿 규모와 환경 복잡성이 증가하더라도 집단 매핑이 실질적인 가치를 유지하는지를 평가할 수 있다.

성숙한 시스템은 공유 지도를 정적인 파일이 아니라 분산 지식 구조(Distributed Knowledge Structure)로 취급한다. 기하 정보, 의미 정보, 신뢰도, 출처, 시간적 유효성(Temporal Validity), 버전, 운용 규칙은 로봇이 환경을 관측함에 따라 지속적으로 변화한다. 서로 다른 참여자는 일시적으로 서로 다른 부분집합 또는 개정 버전을 보유할 수 있으며, 동기화와 검증 메커니즘을 통해 플릿은 충분히 일관된 공유 환경 이해(Shared Environmental Understanding)를 향해 점진적으로 수렴한다.

궁극적으로 분산 지도 및 의미 지식 공유는 각 로봇의 지각 능력을 자체 센서와 이동 이력의 범위를 넘어 확장한다. 지역 관측(Local Observation)은 집단 공간 지능(Collective Spatial Intelligence)으로 전환되며, 로봇은 다른 플릿 구성원이 획득한 경험을 활용할 수 있다. 강건한 위치추정(Robust Localization), 의미 융합, 버전 관리, 보안, 선택적 동기화(Selective Synchronization), 엣지-포그-클라우드 처리와 결합하면 공유 지도는 조정된 다중 로봇 자율성(Coordinated Multi-Robot Autonomy)을 위한 지속적으로 진화하는 핵심 기반이 된다.

## 06.05 Hierarchical Decision Making Robot Supervisor [w/Code]

![](images/image5.png){width="7.268055555555556in" height="7.268055555555556in"}

계층적 의사결정(Hierarchical Decision-Making)은 의사결정이 적절한 공간적, 시간적, 운용적 범위에서 이루어지도록 로봇 지능(Robot Intelligence)을 여러 계층으로 구성한다. 하나의 컨트롤러가 모든 행동을 결정하도록 하는 대신 플릿 수준 감독기(Fleet-Level Supervisor), 사이트 또는 그룹 조정기(Site or Group Coordinator), 개별 로봇 감독기(Robot Supervisor), 저수준 제어 시스템(Low-Level Control System)으로 책임을 분할한다. 이러한 구조를 통해 전략적 목표와 즉각적인 물리적 반응을 동일한 의사결정 주기에 강제로 포함하지 않고 함께 운용할 수 있다.

최상위 수준에서 플릿 감독기(Fleet Supervisor)는 조직의 목표를 해석하고 이를 운용 우선순위(Operational Priority)로 변환한다. 임무 수요, 로봇 가용성, 작업 부하 분배, 충전 요구사항, 유지보수 상태, 교통 상황, 서비스 수준 제약조건(Service-Level Constraint) 등을 고려할 수 있다. 이러한 의사결정은 일반적으로 밀리초가 아닌 수분 또는 수시간 단위로 이루어지며, 개별 액추에이터 명령이 아니라 여러 로봇 그룹에 영향을 준다.

사이트 또는 그룹 감독기(Site or Group Supervisor)는 글로벌 플릿 관리(Global Fleet Management)와 개별 로봇 사이의 중간 계층을 담당한다. 창고, 생산 구역, 실외 영역 또는 임무 그룹에서 운용되는 로봇들을 조정한다. 지역 작업 할당(Regional Task Allocation), 교통 조정, 자원 예약(Resource Reservation), 혼잡 완화, 충전 조정, 지역적 장애 복구 등을 담당할 수 있다. 이 계층은 광범위한 플릿 목표를 현재 사이트 상황을 반영한 의사결정으로 변환한다.

로봇 감독기(Robot Supervisor)는 할당된 임무를 실행 가능한 로봇 행동으로 변환하는 로컬 의사결정 권한(Local Decision Authority)을 담당한다. 작업 목표를 해석하고, 로컬 상황을 평가하며, 주행 또는 조작 행동을 선택하고, 실행 상태를 모니터링하며, 복구 가능한 장애를 처리한다. 감독기는 일반적으로 모터 전류나 조향 명령을 직접 생성하지 않고 경로계획, 제어, 지각, 안전 기능을 수행하는 하위 기능 모듈을 조정한다.

감독기 아래의 행동 및 계획 계층(Behavior and Planning Layer)은 임무를 어떻게 수행할 것인지를 결정한다. 예를 들어 배송 작업은 픽업 위치로 이동, 도킹(Docking), 적재물 획득, 경로 주행, 목적지 접근, 하역, 임무 완료 과정으로 분해할 수 있다. 각 행동은 전문화된 계획기(Planner)와 제어기를 호출할 수 있으며, 감독기는 예상 선행조건(Precondition), 진행 기준(Progress Criteria), 완료 조건(Completion Condition)이 충족되는지를 지속적으로 모니터링한다.

가장 낮은 의사결정 계층에는 시간적으로 중요한 제어 및 안전 기능이 위치한다. 모션 제어기(Motion Controller), 액추에이터 루프(Actuator Loop), 장애물 회피, 비상 정지(Emergency Stop), 안정성 제어(Stability Control)와 기타 물리적 반응은 짧고 예측 가능한 지연시간으로 동작해야 한다. 이러한 기능은 상위 감독기를 일시적으로 사용할 수 없는 경우에도 로컬에서 실행할 수 있어야 한다. 따라서 계층 구조는 느린 전략적 추론과 빠른 물리적 제어를 분리하면서 이들 사이의 명확한 관계를 유지한다.

의사결정 권한(Decision Authority)은 연속적인 저수준 명령이 아니라 목표, 제약조건, 정책(Policy), 작업 할당을 통해 하위 계층으로 전달된다. 플릿 감독기는 어떤 로봇이 어떤 임무를 수행해야 하는지를 지정할 수 있지만 실제 임무 수행에 필요한 세부 궤적(Trajectory)은 로봇이 결정한다. 이러한 원칙은 상위 계층이 모든 물리적 행동을 세부적으로 제어하지 않고 의도(Intent)를 전달하도록 함으로써 로컬 자율성을 보존하고 통신 요구량을 줄인다.

정보는 상위 계층으로 이동하면서 점점 더 추상화된 형태로 변환된다. 저수준 제어기는 실행 상태, 고장, 안전 이벤트를 로봇 감독기에 보고한다. 로봇 감독기는 임무 진행 상황, 위치추정 신뢰도(Localization Confidence), 배터리 상태, 자원 사용량, 운용 조건을 요약하여 사이트 수준 조정 계층에 전달한다. 상위 계층은 모든 원시 센서 측정값이 아니라 플릿 상태와 성능 지표를 수신함으로써 처리 및 통신 부하를 줄인다.

로봇 감독기는 유한 상태 기계(Finite-State Machine), 행동 트리(Behavior Tree), 계층적 상태 기계(Hierarchical State Machine), 규칙 엔진(Rule Engine), 작업 계획기(Task Planner) 또는 이들의 조합으로 구현할 수 있다. 행동 트리는 복잡한 임무에 명시적인 순서 제어, 대체 행동(Fallback Behavior), 재시도, 복구 로직이 필요한 경우 특히 유용하다. 상태 기계는 예측 가능한 상태 전이를 제공하며, 계획 기법은 환경이나 임무를 완전히 사전 정의하기 어려운 경우 동적으로 행동 순서를 생성할 수 있다.

감독 의사결정(Supervisory Decision-Making)은 목표와 제약조건을 명확하게 구분해야 한다. 목표는 자재를 작업대로 운송하는 것과 같이 원하는 운용 결과를 나타내며, 제약조건은 제한 구역, 배터리 한계, 적재 능력, 교통 규칙 또는 안전 요구사항과 같이 반드시 만족해야 하는 조건을 정의한다. 따라서 로봇은 상위 조정 계층이 설정한 경계를 준수하면서 실행 전략을 상황에 맞게 변경할 수 있다.

서로 다른 계층이 충돌하는 목표를 생성하는 경우 권한 경계(Authority Boundary)가 중요해진다. 글로벌 최적화기(Global Optimizer)는 플릿 처리량을 최대화하는 경로를 선호할 수 있지만 로컬 로봇은 해당 경로를 일시적으로 위험하게 만드는 조건을 감지할 수 있다. 물리적 안전은 생산성 최적화보다 우선해야 한다. 명확한 우선순위 규칙(Precedence Rule)을 통해 비상 상황과 로컬 안전 제약조건이 임무 실행보다 우선하도록 하고, 안전 충돌이 없는 경우에는 임무 수준 의사결정이 플릿 전체 정책을 따르도록 해야 한다.

예외 처리(Exception Handling)는 로봇 감독기의 가장 중요한 책임 가운데 하나이다. 산업 환경에서는 임무가 항상 계획대로 진행되는 것은 아니다. 경로가 차단되거나 도킹이 실패할 수 있고, 적재물 검출이 불확실하거나 위치추정 품질이 저하될 수 있으며, 다른 로봇이 필요한 자원을 점유할 수도 있다. 감독기는 모든 비정상 상태를 즉시 사람에게 전달하기보다 장애를 분류하고 적절한 대응 방법을 선택해야 한다.

복구 가능한 장애(Recoverable Failure)는 대부분 로컬에서 처리할 수 있다. 로봇은 행동을 재시도하거나 대체 경로를 선택하고, 재위치추정(Re-Localization)을 수행하거나, 일시적인 장애물이 제거될 때까지 기다리거나, 다른 자원을 요청할 수 있다. 로컬 복구에 실패하면 문제를 사이트 감독기로 에스컬레이션(Escalation)하여 임무를 재할당하거나 다른 로봇과 조정할 수 있다. 운용 판단, 승인 또는 해결되지 않은 안전 의사결정이 필요한 경우에만 사람의 감독(Human Supervision) 단계로 전달할 필요가 있다.

이러한 에스컬레이션 구조는 사람이 모든 사소한 예외 상황에 개입할 필요를 줄여 플릿 확장성(Fleet Scalability)을 향상시킨다. 로컬 자율성(Local Autonomy)은 일상적인 장애를 처리하고, 중간 감독기는 다중 로봇 충돌을 해결하며, 사람은 사전에 정의된 자율 기능의 범위를 초과하는 상황에 집중할 수 있다. 따라서 계층 구조는 의사결정 아키텍처인 동시에 예외 필터링 메커니즘(Exception-Filtering Mechanism)으로 작동한다.

계층적 의사결정은 통신 장애(Communication Failure)에 대해서도 회복탄력성(Resilience)을 유지해야 한다. 플릿 감독기와의 연결이 끊어진 경우 사이트 감독기는 캐시된 정책(Cached Policy)과 로컬 상태를 사용하여 이미 할당된 운용을 계속 관리할 수 있다. 사이트 조정 기능까지 사용할 수 없게 되면 개별 로봇은 안전한 행동을 완료하거나 통제된 대체 상태(Controlled Fallback State)로 전환할 수 있는 충분한 권한을 유지해야 한다. 상위 계층의 상실은 기본적인 안전보다 먼저 최적화 능력을 저하시켜야 한다.

엣지-포그-클라우드 아키텍처(Edge-Fog-Cloud Architecture)는 이 계층 구조와 자연스럽게 대응되지만 두 개념이 동일한 것은 아니다. 로봇 수준 감독과 물리적 제어는 일반적으로 엣지(Edge)에 배치되고, 사이트 조정은 포그 인프라(Fog Infrastructure)에서 실행할 수 있으며, 글로벌 최적화 또는 장기 계획은 클라우드나 중앙집중형 시스템에서 수행할 수 있다. 의사결정 계층 구조는 책임(Responsibility)을 정의하고 엣지-포그-클라우드 아키텍처는 연산 위치(Computational Placement)를 정의하므로 두 개념을 분리하면 유연한 배포가 가능하다.

감독기들은 서로 다른 범위에서 의사결정을 수행하기 때문에 공유 지식(Shared Knowledge)이 필요하다. 로봇 감독기는 로컬 지도, 센서 기반 상황 정보, 즉각적인 자원 상태를 필요로 하며, 사이트 감독기는 집계된 교통, 임무, 가용성 정보를 필요로 한다. 플릿 감독기는 더욱 광범위한 운용 요약과 과거 추세(Historical Trend)를 필요로 한다. 분산 지도(Distributed Map), 의미 지식(Semantic Knowledge), 플릿 통신 메커니즘(Fleet Communication Mechanism)은 이러한 계층을 연결하는 정보 기반을 제공한다.

일관성 요구사항(Consistency Requirement)은 수행되는 의사결정에 따라 달라진다. 좁은 통로나 도킹 스테이션에 대한 배타적 접근은 강하게 조정된 소유권(Strongly Coordinated Ownership)을 요구할 수 있지만 성능 통계는 지연된 업데이트를 허용할 수 있다. 따라서 계층형 시스템은 모든 정보를 동일하게 취급해서는 안 된다. 안전 핵심 자원 상태, 임무 소유권, 명령 권한은 분석 정보나 느리게 변화하는 운용 지식보다 더 강력한 보장을 필요로 한다.

의사결정 지연시간(Decision Latency)도 계층의 범위에 맞아야 한다. 모터 제어기는 밀리초 단위로, 로컬 계획기는 수십 또는 수백 밀리초 단위로, 로봇 감독기는 수초 단위로 동작할 수 있으며, 플릿 최적화는 이보다 훨씬 긴 주기로 수행될 수 있다. 모든 의사결정을 하나의 주기로 실행하려고 하면 연산 자원을 낭비하거나 허용할 수 없는 지연이 발생한다. 따라서 다중 주기 의사결정(Multi-Rate Decision-Making)은 효과적인 로봇 감독 시스템의 본질적인 특성이다.

자원 인식(Resource Awareness)은 감독 의사결정에 반영되어야 한다. 로봇이 기술적으로 특정 임무를 수행할 수 있더라도 배터리 잔량이 부족하거나 센서 성능이 저하되었거나 사용 가능한 연산 자원이 제한되었거나 유지보수 예정 상태일 수 있다. 감독기는 로봇을 서로 동일한 작업 실행기로 취급하지 않고 능력(Capability)과 상태(Health)를 함께 고려해야 한다. 이는 서로 다른 이동 플랫폼, 매니퓰레이터(Manipulator), 센서 또는 적재 능력을 포함하는 이기종 플릿(Heterogeneous Fleet)에서 특히 중요하다.

정책 집행(Policy Enforcement)은 또 다른 중요한 계층적 기능이다. 속도 제한, 제한 구역, 충전 임계값(Charging Threshold), 인간 상호작용 요구사항, 임무 우선순위와 같은 운용 규칙은 상위 계층에서 배포하고 로컬에서 집행할 수 있다. 로봇은 플릿 정책을 준수하면서 세부 행동을 상황에 맞게 조정할 수 있다. 버전 관리된 정책(Versioned Policy)을 사용하면 이후 분석에서 특정 의사결정에 어떤 규칙이 적용되었는지도 확인할 수 있다.

보안(Security)을 위해서는 전체 계층에 걸쳐 명확한 명령 권한(Command Authority)이 필요하다. 로봇은 명령이 승인된 감독기로부터 생성되었는지, 현재 운용 상태에서 해당 명령이 유효한지, 명령 실행이 로컬 안전 제약조건을 위반하지 않는지를 판단해야 한다. 인증(Authentication), 권한 부여(Authorization), 명령 서명(Command Signing), 최신성 검사(Freshness Check), 감사 로그(Audit Logging)를 통해 침해되었거나 오래된 감독 메시지가 물리적 행동을 직접 제어하는 것을 방지할 수 있다.

계층형 시스템에서는 장애 원인을 설명하기 어려울 수 있으므로 관측 가능성(Observability)이 필수적이다. 로그에는 활성 임무(Active Mission), 감독기 상태, 선택된 행동, 의사결정 입력, 정책 버전, 복구 시도, 에스컬레이션 이벤트, 최종 결과를 기록해야 한다. 추적 가능한 의사결정 체인(Traceable Decision Chain)을 통해 엔지니어는 플릿 감독기가 특정 임무를 할당한 이유, 로봇이 특정 행동을 선택한 이유, 로컬 안전 계층이 해당 행동을 수정하거나 거부한 이유를 재구성할 수 있다.

시뮬레이션(Simulation)과 디지털 트윈(Digital Twin)은 배포 전에 감독 로직(Supervisory Logic)을 검증하는 데 활용할 수 있다. 다양한 임무 조합, 교통 상황, 로봇 고장, 통신 단절, 자원 충돌을 생성하여 계층 구조가 적절하게 대응하는지를 시험할 수 있다. 테스트는 정상적인 임무 수행뿐 아니라 성능 저하 모드(Degraded Mode), 상충하는 명령, 지연된 정보, 감독기 장애, 자율 복구와 사람 개입 사이의 전환까지 포함해야 한다.

성숙한 계층형 아키텍처(Hierarchical Architecture)는 모든 의사결정이 바로 위 계층의 승인을 받아야 하는 경직된 명령 체계를 의미하지 않는다. 대신 각 계층에는 명확하게 정의된 권한 범위(Scope of Authority)가 부여되고 해당 경계 안에서 자율적으로 동작한다. 상위 계층은 목표와 제약조건을 설정하고 하위 계층은 점점 더 구체적인 행동을 결정한다. 의사결정이 로컬 권한, 사용 가능한 지식 또는 복구 능력의 범위를 넘어서는 경우에만 상위 계층으로 에스컬레이션된다.

궁극적으로 계층적 의사결정은 대규모 로봇 플릿이 중앙집중형 전략 조정(Centralized Strategic Coordination)과 분산형 로컬 자율성(Distributed Local Autonomy)을 결합할 수 있도록 한다. 플릿 감독기는 집단 목표를 최적화하고, 중간 감독기는 로봇 그룹과 자원을 조정하며, 로봇 감독기는 임무 실행과 복구를 관리하고, 저수준 시스템은 즉각적인 물리적 행동을 보호한다. 적절하게 설계된 권한, 정보 흐름, 대체 동작(Fallback Behavior), 에스컬레이션 체계는 이러한 계층 구조를 회복탄력적인 다중 로봇 지능(Resilient Multi-Robot Intelligence)을 위한 확장 가능한 감독 기반으로 전환한다.

## 06.06 Multi Agent Reinforcement Learning MARL Intro [w/Code]

![](images/image6.png){width="7.268055555555556in" height="7.268055555555556in"}

다중 에이전트 강화학습(Multi-Agent Reinforcement Learning, MARL)은 단일 자율 에이전트(Single Autonomous Agent)를 대상으로 하는 강화학습(Reinforcement Learning)을 여러 에이전트가 동시에 학습하고 행동하는 환경으로 확장한다. 로봇 플릿(Robot Fleet)에서는 각 로봇을 환경의 일부를 관측하고, 정책(Policy)에 따라 행동을 선택하며, 보상(Reward)을 받고, 경험을 통해 행동을 적응시키는 에이전트로 모델링할 수 있다. 중요한 차이점은 이제 환경에 다른 학습 로봇들이 포함되며, 이들의 의사결정이 지속적으로 서로에게 영향을 준다는 것이다.

단일 에이전트 강화학습(Single-Agent Reinforcement Learning)에서는 일반적으로 환경의 변화가 자신의 행동과 외부 동역학(External Dynamics)에 의해 발생한다고 가정한다. MARL에서는 다른 에이전트들도 학습 과정에서 정책을 변경하기 때문에 이러한 가정이 성립하지 않는다. 따라서 하나의 로봇 관점에서 주변 로봇의 행동은 비정상성(Non-Stationarity)을 갖는 것처럼 보일 수 있다. 이러한 상호작용은 학습을 훨씬 복잡하게 만들지만 협력(Cooperation), 조정(Coordination), 경쟁(Competition), 집단 적응(Collective Adaptation)의 가능성을 제공한다.

MARL 문제는 여러 에이전트, 공유되거나 부분적으로 공유되는 환경, 관측(Observation), 행동(Action), 상태 전이 동역학(Transition Dynamics), 보상 함수(Reward Function)를 이용하여 표현할 수 있다. 각 시간 단계(Time Step)에서 모든 로봇은 센서와 사용 가능한 플릿 정보를 기반으로 관측값을 획득한다. 이후 로봇들이 행동을 선택하면 이들의 결합 행동(Joint Action)에 따라 환경이 새로운 상태로 전이되고, 보상은 개별 및 집단 성능에 대한 피드백을 제공한다.

부분 관측 가능성(Partial Observability)은 다중 로봇 시스템(Multi-Robot System)의 자연스러운 특성이다. 하나의 로봇은 일반적으로 창고, 공장, 실외 사이트 또는 분산 플릿의 전체 상태를 관측할 수 없다. 주변 장애물, 지역 교통, 임무 상태, 배터리 상태와 다른 에이전트가 전달한 일부 정보만 확인할 수 있다. 따라서 MARL은 불완전한 관측으로부터 유용한 행동을 학습하면서 통신 또는 공유 지식(Shared Knowledge)을 사용할 수 있는 경우 이를 효과적으로 활용해야 한다.

보상 함수(Reward Function)는 에이전트가 무엇을 학습하도록 유도할 것인지를 정의한다. 플릿 보상(Fleet Reward)은 임무 완료, 처리량(Throughput), 이동 효율성, 에너지 소비, 충돌 회피, 혼잡 감소, 충전 효율성 또는 균형 잡힌 작업 부하를 표현할 수 있다. 잘못 설계된 보상은 수치적인 학습 성능이 향상되더라도 의도하지 않은 행동을 발생시킬 수 있다. 따라서 보상 설계(Reward Engineering)는 단순한 수학적 구현 세부사항이 아니라 핵심적인 아키텍처 설계 과제이다.

협력형 MARL(Cooperative MARL)은 에이전트들이 공통 목표를 향해 협력한다고 가정한다. 로봇들은 플릿 처리량을 기반으로 하는 글로벌 보상(Global Reward)을 공유하거나 임무가 효율적으로 완료될 때 공동으로 보상을 받을 수 있다. 이러한 구성은 개별 로봇의 단기적인 이익을 최대화하는 것보다 그룹 전체의 성능이 중요한 창고 자율이동로봇(AMR), 협력 검사 로봇, 협업 운송 시스템 및 기타 플릿에 적합하다.

경쟁형 MARL(Competitive MARL)은 에이전트들이 서로 대립되는 목표를 갖는 환경을 다루며, 협력-경쟁 혼합 환경(Mixed Cooperative-Competitive Setting)은 공유된 이익과 충돌하는 이익을 모두 포함한다. 산업용 로봇 플릿은 일반적으로 협력이 중심이지만 여러 로봇이 동일한 통로, 충전소, 작업대, 통신 채널 또는 기타 제한된 자원을 요청하는 경우 간접적인 경쟁이 발생할 수 있다. 학습은 이러한 상호작용을 고려하면서도 경쟁이 안전이나 운용 정책을 훼손하지 않도록 해야 한다.

주요 아키텍처적 구분 중 하나는 중앙집중형(Centralized)과 분산형(Decentralized) 학습 및 실행이다. 완전 중앙집중형 정책은 이론적으로 전체 플릿 상태를 사용할 수 있지만 로봇 수가 증가함에 따라 관측 공간(Observation Space)과 행동 공간(Action Space)이 빠르게 증가한다. 완전 분산형 에이전트는 자연스럽게 확장할 수 있지만 효과적인 조정을 위한 정보가 부족할 수 있다. 따라서 MARL 아키텍처는 학습 중 중앙집중형 정보와 운용 중 분산형 자율성 사이에서 균형을 추구하는 경우가 많다.

분산 실행을 위한 중앙집중형 학습(Centralized Training with Decentralized Execution, CTDE)은 이러한 목적을 위해 널리 사용되는 MARL 원칙이다. 학습 중에는 중앙집중형 크리틱(Centralized Critic) 또는 학습 프로세스가 글로벌 상태(Global State)나 결합 행동을 포함하여 여러 에이전트의 정보에 접근할 수 있다. 배포 이후에는 각 로봇이 로컬에서 사용할 수 있는 관측 정보와 허용된 통신을 이용하여 자체 정책을 실행한다. 이를 통해 학습에서는 글로벌 정보를 활용하면서 실제 운용 로봇이 중앙 의사결정 서버에 지속적으로 의존하지 않도록 할 수 있다.

액터-크리틱 프레임워크(Actor-Critic Framework)는 CTDE 구조와 자연스럽게 결합된다. 개별 액터(Actor)는 로봇의 행동을 결정하고, 하나 이상의 크리틱(Critic)은 학습 중 사용할 수 있는 보다 광범위한 정보를 기반으로 행동의 가치를 평가한다. 이러한 원리를 기반으로 하는 알고리즘은 분산 실행을 유지하면서 조정된 행동을 학습할 수 있다. 구체적인 알고리즘은 행동이 이산형(Discrete)인지 연속형(Continuous)인지, 에이전트가 동종(Homogeneous)인지, 그리고 에이전트 사이의 상호작용이 얼마나 강한지에 따라 선택해야 한다.

가치 기반 MARL(Value-Based MARL)은 또 다른 접근 방법을 제공한다. 협력 환경에서는 글로벌 팀 가치(Global Team Value)를 개별 에이전트와 관련된 기여도로 분해할 수 있다. 가치 분해(Value Decomposition) 기반 방법은 분산형 행동 선택이 유용한 공동 목표(Joint Objective)와 일관성을 갖도록 한다. 각 로봇이 로컬에서 행동을 실행하면서도 학습 과정에서는 전체 시스템의 성능을 향상시키는 행동을 장려할 수 있기 때문에 플릿 조정에 적합하다.

정책 기반(Policy-Based) 및 액터-크리틱 기반 MARL은 로봇의 행동이 연속적이거나 복잡한 경우 특히 유용하다. 주행 속도, 가속도, 자원 입찰(Resource Bidding), 작업 선호도, 대형 제어 파라미터(Formation Parameter), 조정 의사결정은 단순한 이산 행동 공간으로 표현하기 어려울 수 있다. 학습된 정책은 관측 정보를 행동 분포(Action Distribution)로 직접 변환하고, 크리틱과 보상 신호는 반복적인 시뮬레이션 또는 기록된 상호작용을 통해 정책 개선을 유도할 수 있다.

통신(Communication) 자체도 학습 문제의 일부가 될 수 있다. 에이전트는 위치, 의도(Intent), 작업 상태, 지도 변화, 학습된 메시지(Learned Message), 압축된 잠재 표현(Compressed Latent Representation)을 교환할 수 있다. 모든 통신 규칙을 수동으로 정의하는 대신 일부 MARL 시스템은 언제 통신할지, 어떤 피어(Peer)와 통신할지, 어떤 정보를 전송할지를 학습한다. 그러나 학습된 통신도 실제 로봇 네트워크의 대역폭, 지연시간, 보안 및 장애 제약조건을 준수해야 한다.

로봇 수가 증가하면 결합 상태 및 행동 공간(Joint State and Action Space)이 급격히 증가할 수 있기 때문에 확장성(Scalability)은 중요한 과제이다. 5대의 로봇에서 효과적인 정책이 50대 또는 500대의 로봇에서도 일반화된다는 보장은 없다. 파라미터 공유(Parameter Sharing), 로컬 관측, 이웃 기반 상호작용(Neighborhood-Based Interaction), 그래프 표현(Graph Representation), 어텐션 메커니즘(Attention Mechanism), 계층적 정책(Hierarchical Policy), 평균장 근사(Mean-Field Approximation)를 사용하면 특정 플릿 규모에 대한 의존성을 줄이고 확장성을 향상시킬 수 있다.

동종 플릿(Homogeneous Fleet)은 로봇들이 유사한 센서, 동역학, 능력을 가지므로 정책 파라미터를 공유할 수 있는 경우가 많다. 각 로봇은 서로 다른 관측 정보를 사용하면서 동일한 학습 정책을 실행하므로 학습해야 할 모델의 수를 줄일 수 있다. 이기종 플릿(Heterogeneous Fleet)은 로봇 능력에 대한 추가적인 표현이 필요하다. 휠 기반 AMR, 매니퓰레이터 장착 로봇, 검사 플랫폼, 중량물 운송 로봇은 동일한 행동이나 임무 역할을 동일한 방식으로 해석할 수 없기 때문이다.

그래프 기반 표현(Graph-Based Representation)은 다중 로봇 상호작용에 특히 적합하다. 로봇을 노드(Node)로 표현하고 통신 링크, 공간적 근접성, 작업 관계 또는 자원 충돌을 에지(Edge)로 나타낼 수 있다. 그래프 신경망(Graph Neural Network, GNN)은 이러한 관계 구조를 처리하여 로봇이 플릿에 진입하거나 이탈하고 이동하더라도 적응할 수 있는 표현을 생성한다. 이를 통해 영구적으로 고정된 토폴로지를 가정하지 않고도 조정 행동을 학습할 수 있다.

기여도 할당(Credit Assignment)은 또 다른 근본적인 MARL 문제이다. 플릿이 공유 보상을 받는 경우 어떤 로봇의 행동이 성공 또는 실패에 기여했는지를 판단하기 어려울 수 있다. 많은 로봇이 동시에 의사결정을 수행한 후 처리량이 향상되었다면 개별 로봇은 자신의 행동 품질에 대한 직접적인 정보를 거의 얻지 못한다. 반사실적 추론(Counterfactual Reasoning), 보상 형성(Shaped Reward), 로컬 보조 보상(Local Auxiliary Reward), 가치 분해를 통해 보다 유용한 학습 신호를 제공할 수 있다.

다중 에이전트 환경에서는 여러 로봇이 동시에 익숙하지 않은 행동을 시험할 수 있기 때문에 탐색(Exploration)이 더욱 어려워진다. 물리 시스템에서 통제되지 않은 탐색은 혼잡, 비효율적인 행동, 장비 손상 또는 안전 위험을 발생시킬 수 있다. 따라서 로봇 플릿을 위한 MARL 학습은 제한 없는 시행착오 학습보다 시뮬레이션, 디지털 트윈(Digital Twin), 기록된 운용 데이터, 제약된 탐색(Constrained Exploration), 신중하게 통제된 실제 환경 미세조정(Real-World Fine-Tuning)을 적극적으로 활용해야 한다.

시뮬레이션은 실제 운용보다 빠르게 대량의 병렬 경험(Parallel Experience)을 생성할 수 있도록 한다. 다양한 교통 밀도, 로봇 장애, 임무 패턴, 센서 불확실성, 통신 지연, 충전 제약조건, 환경 변화를 학습 과정에서 무작위화할 수 있다. 도메인 무작위화(Domain Randomization)와 시나리오 다양성(Scenario Diversity)은 정책이 하나의 이상적인 플릿 구성에 과적합(Overfitting)되는 것을 방지하고 실제 배포 환경의 다양한 변화에 대응하는 능력을 향상시킨다.

안전 제약조건(Safety Constraint)은 학습된 최적화 목표와 분리되어 유지되어야 한다. MARL 정책은 보상 관점에서는 효율적으로 보이는 행동을 추천하더라도 충돌 여유거리, 제한 구역, 속도 제한 또는 기타 운용 요구사항을 위반할 수 있다. 따라서 결정론적 안전 계층(Deterministic Safety Layer), 규칙 기반 감독기(Rule-Based Supervisor), 제약 기반 계획기(Constrained Planner), 비상 제어기(Emergency Controller)는 학습된 행동이 실제 액추에이터에 전달되기 전에 이를 거부하거나 수정할 수 있어야 한다.

계층적 의사결정(Hierarchical Decision-Making)은 학습된 정책이 전체 로봇 스택을 직접 제어하도록 하지 않으면서 MARL을 통합할 수 있다. MARL은 작업 할당, 교통 협상(Traffic Negotiation), 대형 행동(Formation Behavior), 자원 선택 또는 기타 조정 의사결정을 최적화할 수 있으며, 로봇 감독기(Robot Supervisor)는 정책과 로컬 안전 제약조건을 집행한다. 이후 저수준 모션 제어기가 검증된 명령을 실행한다. 이를 통해 적응형 집단 지능과 결정론적 로봇 운용 사이에 통제된 경계를 형성할 수 있다.

모든 학습 에이전트가 다른 에이전트가 경험하는 환경을 지속적으로 변화시키기 때문에 학습 안정성(Training Stability)은 여전히 어려운 문제이다. 이전 정책에서 수집한 경험은 플릿 정책이 변화하면서 현재 상황을 충분히 대표하지 못할 수 있다. 재현 버퍼(Replay Buffer), 타깃 네트워크(Target Network), 중앙집중형 크리틱, 상대 또는 팀원 모델링(Opponent or Teammate Modeling), 동기화된 정책 업데이트(Synchronized Policy Update), 신중하게 제어된 학습률을 통해 불안정성을 줄일 수 있지만 MARL의 수렴은 일반적으로 단일 에이전트 학습보다 어렵다.

평가(Evaluation)는 평균 보상만이 아니라 집단 행동(Collective Behavior)을 평가해야 한다. 주요 플릿 지표에는 임무 처리량, 완료 시간, 이동 거리, 에너지 소비, 혼잡, 교착상태 발생 빈도(Deadlock Frequency), 충돌 또는 근접 사고(Near-Miss Event), 자원 활용률, 공정성(Fairness), 복구 성능, 통신 부하가 포함된다. 또한 학습 과정에서 직접 경험하지 않았던 플릿 규모, 레이아웃, 교통 패턴, 장애 조건에서도 정책을 시험해야 한다.

배포(Deployment)는 일반적으로 단계적인 검증 절차를 따라야 한다. 후보 정책(Candidate Policy)은 먼저 오프라인에서 평가한 후 시뮬레이션, 디지털 트윈 시험, 섀도 운용(Shadow Operation), 제한된 로봇 시험, 점진적으로 확대되는 플릿 배포를 거칠 수 있다. 모델 및 정책 버전은 추적 가능해야 하며, 실제 배포 이후 운용 성능이 저하될 경우 이전에 검증된 정책으로 복원할 수 있는 롤백(Rollback) 메커니즘을 유지해야 한다.

MARL은 보다 광범위한 분산 지능 아키텍처(Distributed Intelligence Architecture)와도 자연스럽게 연결된다. 연합 학습(Federated Learning)은 모델의 분산 개선을 지원하고, 가십 프로토콜(Gossip Protocol)은 선택된 지식을 전파하며, 분산 의미 지도(Distributed Semantic Map)는 공유 환경 맥락을 제공하고, 계층적 감독기(Hierarchical Supervisor)는 학습된 의사결정을 제한할 수 있다. MARL은 이러한 분산 정보를 활용하여 경험을 통해 집단 행동을 개선하는 적응형 조정 정책(Adaptive Coordination Policy)을 제공한다.

따라서 로봇 플릿에서 MARL의 목표는 기존의 플릿 관리, 경로계획 또는 안전 시스템을 제한 없는 학습 행동으로 대체하는 것이 아니다. MARL의 가치는 많은 로봇 사이의 상호작용으로 인해 사람이 설계한 규칙만으로 최적화하기 점점 어려워지는 문제에 대한 조정 전략을 학습하는 데 있다. 적절하게 제한된 MARL은 복잡한 교통, 자원, 임무 및 환경 조건에 의사결정을 적응시킴으로써 결정론적 엔지니어링(Deterministic Engineering)을 보완할 수 있다.

궁극적으로 다중 에이전트 강화학습(Multi-Agent Reinforcement Learning)은 로봇 플릿이 개별 로봇이 어떻게 행동해야 하는지만이 아니라 각 로봇의 행동이 서로 어떻게 상호작용해야 하는지를 학습할 수 있는 프레임워크를 제공한다. 협력 보상(Cooperative Reward), 중앙집중형 학습, 분산 실행, 확장 가능한 표현, 시뮬레이션 기반 학습, 감독형 안전 제약조건(Supervisory Safety Constraint)을 결합하면 MARL은 실제 다중 로봇 운용에 필요한 신뢰성을 유지하면서 분산된 로봇 에이전트들을 적응형 집단 시스템(Adaptive Collective System)으로 발전시킬 수 있다.

## 06.07 Emergent Behavior in Large Scale Robot Fleets

![](images/image7.png){width="7.268055555555556in" height="7.268055555555556in"}

대규모 로봇 플릿의 창발적 행동(Emergent Behavior in Large-Scale Robot Fleets)은 중앙 제어기(Central Controller)가 명시적으로 명령하지 않았음에도 많은 로봇 사이의 상호작용을 통해 나타나는 집단적 패턴(Collective Pattern)을 의미한다. 각 로봇은 주행, 작업 실행, 자원 사용, 통신 또는 충돌 회피를 위한 비교적 단순한 로컬 규칙(Local Rule)을 따를 수 있지만, 수백 또는 수천 개 에이전트의 행동이 결합되면 개별 규칙만으로는 항상 예측하기 어려운 복잡한 플릿 수준 동역학(Fleet-Level Dynamics)이 형성된다.

플릿 규모가 증가할수록 상호작용은 운영자가 모든 로봇을 개별적으로 분석할 수 있는 능력보다 빠르게 증가하기 때문에 창발(Emergence)은 특히 중요해진다. 10대의 로봇에서는 효율적으로 동작하는 경로 선택 규칙이 수백 대의 로봇이 동일한 통로를 이용하면 혼잡을 발생시킬 수 있다. 마찬가지로 개별적으로는 합리적인 충전 의사결정이 많은 로봇을 동시에 충전소로 이동하게 만들 수 있다. 따라서 대규모 운용에서는 집단 수준에서만 드러나는 시스템 행동(System Behavior)이 발생한다.

창발적 행동은 본질적으로 유익하거나 해로운 것으로 한정되지 않는다. 긍정적 창발(Positive Emergence)은 적응형 교통 흐름(Adaptive Traffic Flow), 자발적인 작업 부하 균형(Workload Balancing), 효율적인 공간 커버리지(Spatial Coverage), 협력 탐색(Cooperative Exploration), 로봇 장애 이후의 회복탄력적인 재분배를 만들어낼 수 있다. 반면 부정적 창발(Negative Emergence)은 혼잡 파동(Congestion Wave), 교착상태(Deadlock), 진동하는 작업 할당(Oscillating Task Assignment), 자원 기아(Resource Starvation), 불안정한 대형, 동기화된 충전 수요 또는 동일한 운용 자원을 둘러싼 반복적인 경쟁을 발생시킬 수 있다.

로컬 상호작용(Local Interaction)은 창발이 발생하는 주요 메커니즘 가운데 하나이다. 로봇은 주변 에이전트, 장애물, 자원 상태, 공유 지도(Shared Map), 교통 예약(Traffic Reservation), 전달된 의도(Communicated Intention)에 지속적으로 반응한다. 한 로봇의 작은 행동 변화는 주변 로봇이 인식하는 환경을 변화시키고, 다시 주변 로봇의 반응을 유발한다. 이러한 피드백 루프(Feedback Loop)가 플릿 전체에서 반복되면 작은 지역 이벤트가 대규모 패턴으로 증폭될 수 있다.

피드백(Feedback)은 강화형(Reinforcing) 또는 균형형(Balancing)으로 작용할 수 있다. 강화 피드백(Reinforcing Feedback)은 처음에는 더 빠르게 보이는 경로를 로봇들이 반복적으로 선택하여 결국 해당 경로에 혼잡을 발생시키는 것처럼 창발하는 패턴을 강화한다. 균형 피드백(Balancing Feedback)은 혼잡 비용 증가에 따라 로봇이 대체 경로를 선택하도록 하는 것처럼 과도한 집중을 억제한다. 따라서 바람직한 플릿 수준 행동을 형성하기 위해서는 적절한 피드백 메커니즘을 설계하는 것이 중요하다.

밀도(Density)는 집단 동역학(Collective Dynamics)에 강한 영향을 미친다. 로봇 밀도가 낮을 때에는 에이전트들이 제한된 상호작용만으로 운용할 수 있으며 단순한 분산형 규칙(Decentralized Rule)도 효과적으로 동작할 수 있다. 밀도가 증가하면 로봇 간의 조우가 빈번해지고 공유 자원을 놓고 경쟁하며 경로와 일정 사이에 의존성이 형성된다. 특정 임계값을 넘으면 교통 수요의 작은 변화만으로도 원활한 운용 상태가 심각한 혼잡 또는 교착상태로 급격히 전환될 수 있다.

공간 구조(Spatial Structure) 역시 창발 패턴이 형성되는 방식을 결정한다. 좁은 통로, 교차로, 엘리베이터, 도킹 스테이션(Docking Station), 충전 구역, 적재 구역, 공유 작업 셀(Shared Work Cell)은 상호작용 병목지점(Interaction Bottleneck)을 형성한다. 전체 시설이 충분한 처리 용량을 갖추고 있더라도 지역적인 기하 제약조건(Local Geometric Constraint)이 많은 로봇을 작은 영역에 집중시킬 수 있다. 따라서 플릿 분석은 평균 플릿 활용률뿐 아니라 로봇 행동과 환경 토폴로지(Environmental Topology)의 관계를 함께 검토해야 한다.

시간적 동기화(Temporal Synchronization)는 또 다른 형태의 창발을 발생시킬 수 있다. 동일한 정책이나 일정으로 운용되는 로봇들은 비슷한 시간에 임무를 시작하거나 배터리를 충전하고, 유지보수를 수행하거나 공유 자원을 요청할 수 있다. 이러한 동기화는 명시적으로 프로그래밍하지 않은 주기적인 수요 피크(Demand Peak)를 발생시킬 수 있다. 무작위화된 타이밍(Randomized Timing), 시차 일정(Staggered Schedule), 적응형 임계값(Adaptive Threshold), 예측형 조정(Predictive Coordination)을 도입하면 유해한 동기화를 줄일 수 있다.

작업 할당(Task Allocation) 역시 창발적인 작업 부하 패턴을 생성할 수 있다. 모든 로봇이 가장 가까운 작업을 선호하면 일부 영역에는 로봇이 과도하게 집중되는 반면 먼 지역의 작업은 누적될 수 있다. 작업 우선순위가 빠르게 변화하면 로봇이 반복적으로 작업을 포기하거나 서로 교환하여 생산적인 작업 대신 진동(Oscillation)이 발생할 수 있다. 따라서 작업 할당 메커니즘에는 단기적인 변화에 과도하게 반응하는 것을 방지하기 위한 히스테리시스(Hysteresis), 작업 유지 규칙(Commitment Rule), 전환 비용(Switching Cost) 또는 기타 안정화 메커니즘이 필요하다.

교통 시스템(Traffic System)은 창발적인 플릿 행동이 특히 명확하게 나타나는 사례이다. 로컬 충돌 회피(Local Collision Avoidance)는 개별 로봇 사이의 물리적 간격을 유지할 수 있지만 전체적인 교통 정체(Gridlock)를 방지하지는 못할 수 있다. 로봇들이 서로 양보하거나 교차로를 차단하고, 이동이 시설의 반대 방향으로 전파되는 대기열(Queue)을 형성할 수도 있다. 따라서 충돌을 방지하는 것과 원활한 교통 흐름을 유지하는 것은 동일하지 않으며, 플릿 수준 조정은 처리량, 대기열 형성, 네트워크 전체의 이동을 함께 고려해야 한다.

자원 경합(Resource Contention)에서도 유사한 현상이 발생할 수 있다. 충전소, 엘리베이터, 좁은 통로, 매니퓰레이터(Manipulator), 작업대, 통신 채널, 적재 장비는 동시에 사용할 수 있는 로봇의 수가 제한될 수 있다. 적절한 예약 또는 스케줄링 메커니즘이 없다면 개별적으로 합리적인 다수의 요청이 집단적으로 자원 기아나 비효율적인 대기를 발생시킬 수 있다. 따라서 창발적 자원 행동(Emergent Resource Behavior)은 개별 스케줄링 문제가 아니라 시스템 수준 속성(System-Level Property)으로 분석해야 한다.

통신 토폴로지(Communication Topology)는 집단 행동이 형성되는 속도에 영향을 준다. 주변 피어(Peer)와만 통신하는 로봇은 지역적으로 전파되는 패턴을 생성하는 반면 중앙집중형 또는 브로드캐스트 통신(Broadcast Communication)은 플릿의 많은 부분을 빠르게 동기화할 수 있다. 가십 프로토콜(Gossip Protocol)과 분산 지식 공유(Distributed Knowledge Sharing)는 회복탄력성을 제공하지만 전파 지연(Propagation Delay)과 일시적인 불일치(Temporary Inconsistency)를 발생시킨다. 특히 로봇이 서로 다른 버전의 공유 지식을 기반으로 행동하는 경우 이러한 특성 자체가 창발적 조정에 영향을 줄 수 있다.

이기종 플릿(Heterogeneous Fleet)은 로봇마다 속도, 적재 능력, 센서, 기동성, 에너지 특성, 임무 능력이 다르기 때문에 추가적인 복잡성을 발생시킨다. 느린 중량물 운송 로봇 하나가 다수의 소형 자율이동로봇(AMR)의 움직임에 영향을 줄 수 있으며, 특수 검사 로봇은 일반적으로 물류 로봇이 주로 사용하는 영역에 일시적인 접근 권한을 요구할 수 있다. 따라서 창발은 단순히 에이전트 수뿐 아니라 에이전트 능력과 역할의 다양성에도 영향을 받는다.

다중 에이전트 강화학습(Multi-Agent Reinforcement Learning, MARL)은 상호작용과 보상을 통해 집단 전략이 형성되도록 함으로써 창발을 의도적으로 활용할 수 있다. 협력 보상(Cooperative Reward)은 에이전트들이 사람이 직접 지정하지 않은 교통 규칙, 자원 공유 전략 또는 작업 부하 분배 방식을 발견하도록 유도할 수 있다. 그러나 학습된 창발(Learned Emergence)은 예상하지 못한 지름길이나 취약한 관행을 만들어낼 수도 있으므로 실제 배포 전 시뮬레이션, 해석 가능성(Interpretability), 제약조건, 감독 검증(Supervisory Validation)이 필수적이다.

창발적 행동은 자기조직화(Self-Organization)와 밀접한 관련이 있지만 두 개념은 동일하지 않다. 창발은 로컬 상호작용에서 발생하는 글로벌 패턴(Global Pattern)을 의미하고, 자기조직화는 상세한 중앙 제어 없이 질서 있는 구조가 형성되는 과정에 초점을 둔다. 로봇 플릿은 유용한 조직화 없이 창발적인 혼잡을 보일 수도 있으며, 의도적으로 설계된 로컬 규칙을 통해 자기조직화된 대형, 커버리지 패턴 또는 분산 작업 전문화(Distributed Task Specialization)를 유도할 수도 있다.

대규모 시뮬레이션(Large-Scale Simulation)은 특정 플릿 규모나 운용 밀도 이상에서만 나타나는 행동이 많기 때문에 창발을 연구하는 가장 중요한 도구 가운데 하나이다. 디지털 환경에서 다양한 레이아웃, 작업 분포, 통신 장애, 충전 수요, 교통 정책을 적용하여 수백 또는 수천 대의 로봇을 평가할 수 있다. 파라미터 스윕(Parameter Sweep)을 사용하면 실제 로봇을 이용한 실험으로 발견하기에는 어렵거나 비용이 많이 들거나 위험한 임계 조건(Critical Threshold)을 확인할 수 있다.

시뮬레이션은 평균 성능뿐 아니라 분포(Distribution)와 극단 조건(Extreme Condition)을 함께 분석해야 한다. 플릿이 평균적으로는 적절한 처리량을 달성하면서도 드물게 심각한 교착상태에 진입할 수 있다. 로봇 장애, 네트워크 지연, 교통 수요 피크, 자원 부족이 드물게 결합하면 불균형적으로 큰 장애를 발생시킬 수 있다. 스트레스 테스트(Stress Testing)와 몬테카를로 시뮬레이션(Monte Carlo Simulation)은 발생 확률은 낮지만 운용상 중요한 이러한 집단 행동을 발견하는 데 도움이 된다.

창발을 평가하는 지표(Metric)는 효율성과 안정성을 모두 포착해야 한다. 처리량, 임무 완료 시간, 이동 거리, 대기 시간, 에너지 소비, 혼잡, 대기열 길이, 교착상태 빈도, 자원 활용률, 작업 부하 공정성(Workload Fairness), 복구 시간은 서로 보완적인 관점을 제공한다. 공간 및 시간 상관관계 지표(Spatial and Temporal Correlation Measure)를 추가하면 일반적인 평균 지표에서는 드러나지 않는 군집화(Clustering), 동기화, 진동 또는 파동 형태의 패턴을 발견할 수 있다.

플릿 규모가 커질수록 운영자가 모든 로봇의 궤적을 직접 확인할 수 없기 때문에 관측 가능성(Observability)은 더욱 어려워진다. 플릿 모니터링 시스템(Fleet Monitoring System)은 로컬 이벤트를 혼잡 히트맵(Congestion Heatmap), 자원 압력(Resource Pressure), 대기열 증가, 비정상 동기화, 작업 불균형, 상호작용 밀도(Interaction Density)와 같은 상위 수준 지표로 집계해야 한다. 이러한 집단 지표의 변화를 탐지하면 지역적 장애가 플릿 전체의 불안정성으로 발전하기 전에 조기 경고를 제공할 수 있다.

창발적 행동의 제어는 일반적으로 과도한 중앙집중형 세부 제어(Centralized Micromanagement)를 피해야 한다. 중앙 제어는 대규모 환경에서 연산 비용이 높아지고 취약해질 수 있으며, 완전히 로컬화된 행동은 글로벌 상황 인식이 부족할 수 있다. 계층적 감독(Hierarchical Supervision)은 실용적인 절충안을 제공한다. 로컬 로봇은 즉각적인 상호작용을 처리하고, 지역 감독기는 혼잡과 자원을 조정하며, 플릿 수준 시스템은 광범위한 운용 상황에 따라 정책, 우선순위 또는 용량을 조정한다.

정책 설계(Policy Design)는 개별 로봇이 경험하는 인센티브(Incentive)와 제약조건을 변경함으로써 창발의 방향을 조정할 수 있다. 혼잡 인식 경로 비용(Congestion-Aware Routing Cost), 예약 규칙, 최소 작업 유지 기간, 적응형 충전 임계값, 공정성 페널티(Fairness Penalty), 동적 자원 가격(Dynamic Resource Pricing)은 모든 궤적을 직접 지정하지 않고도 로컬 의사결정을 변화시킬 수 있다. 목표는 다양한 운용 조건에서 집단적 결과가 안정적이고 유익하게 유지되는 로컬 규칙을 설계하는 것이다.

안전(Safety)은 유익한 창발적 행동과 독립적으로 보호되어야 한다. 플릿이 효율적인 비공식적 관행을 학습하더라도 이러한 관행이 결정론적 충돌 보호(Deterministic Collision Protection), 제한 구역 집행, 비상 정지, 검증된 자원 인터록(Resource Interlock)을 대체해서는 안 된다. 창발적 최적화(Emergent Optimization)는 검증된 제어 및 감독 메커니즘이 설정한 안전 영역(Safety Envelope) 안에서 동작해야 하며, 이를 통해 예상하지 못한 집단 패턴이 물리적 보호 기능을 우회하지 못하도록 해야 한다.

로봇이 충분한 로컬 자율성(Local Autonomy)과 분산 지식(Distributed Knowledge)을 보유하면 회복탄력성(Resilience) 자체가 창발할 수 있다. 하나의 로봇이 고장 나면 주변 에이전트들이 경로를 변경하고, 작업을 재할당하며, 전체 플릿을 완전히 다시 계획하지 않고도 교통 패턴을 재구성할 수 있다. 따라서 분산 지능(Distributed Intelligence)은 장애에 대한 점진적인 적응(Graceful Adaptation)을 가능하게 하지만, 로컬 반응이 원래의 장애를 혼잡, 진동 또는 연쇄적인 자원 부족으로 증폭시키지 않도록 해야 한다.

대규모 플릿에서는 연쇄 효과(Cascading Effect)에 특별한 주의가 필요하다. 하나의 차단된 통로가 교통을 다른 경로로 우회시키면 해당 경로의 혼잡이 증가하고 임무가 지연될 수 있다. 지연된 로봇들이 동시에 충전 임계값에 도달하면 충전기 수요가 증가하고 플릿 가용성이 더욱 감소할 수 있다. 따라서 지역적 장애로 시작된 문제가 서로 연결된 피드백 루프를 통해 주행, 스케줄링, 에너지 관리, 작업 할당 전체로 확산될 수 있다.

따라서 공학적 목표는 플릿 복잡성이 증가함에 따라 점점 피하기 어려워지는 창발 자체를 제거하는 것이 아니라 이를 이해하고, 제한하고, 활용하는 것이다. 설계자는 배포 전에 상호작용 메커니즘, 임계 밀도(Critical Density), 피드백 루프, 동기화 위험, 자원 병목지점을 식별해야 한다. 이후 시뮬레이션과 운용 텔레메트리(Operational Telemetry)를 통해 관측된 집단 행동이 허용 가능한 성능 및 안전 경계 안에 유지되는지를 검증할 수 있다.

궁극적으로 창발적 행동은 대규모 로봇 플릿이 단순히 개별 로봇을 합한 것 이상의 시스템이라는 사실을 보여준다. 로컬 의사결정은 공유 공간, 자원, 통신, 작업, 학습된 정책을 통해 상호작용하면서 어떤 단일 에이전트도 명시적으로 명령하지 않은 플릿 수준 동역학을 만들어낸다. 분산 지능, 계층적 감독, 다중 에이전트 강화학습(MARL), 시뮬레이션, 관측 가능성, 결정론적 안전 제약조건을 결합하면 이러한 동역학을 확장 가능하고 적응적이며 회복탄력적인 집단 로봇 운용(Collective Robotic Operation)으로 유도할 수 있다.

## 06.08 Privacy Preserving Fleet Learning [w/Code]

![](images/image8.png){width="7.268055555555556in" height="7.268055555555556in"}

개인정보 보호형 플릿 학습(Privacy-Preserving Fleet Learning)은 민감한 운용 데이터(Sensitive Operational Data)의 불필요한 노출을 제한하면서 여러 로봇이 공유 인공지능 모델(Shared Artificial Intelligence Model)을 개선할 수 있도록 한다. 로봇 플릿(Robot Fleet)은 카메라 영상, 라이다(LiDAR) 측정값, 이동 궤적, 시설 배치, 사람의 활동, 장비 상태, 임무 기록 등을 수집할 수 있다. 개인정보 보호를 고려한 아키텍처는 이러한 관측 정보를 보호 자산(Protected Asset)으로 취급하고 원시 정보가 로봇이나 운용 사이트 외부로 이동하는 것을 최소화한다.

플릿이 공장, 병원, 창고, 공공장소, 고객 시설 또는 지리적으로 분산된 사이트에서 운용될 경우 개인정보 보호 문제(Privacy Challenge)는 더욱 중요해진다. 로봇이 생성한 데이터에는 사람, 생산 공정, 인프라, 자산 위치, 고객 활동 또는 독점적인 운용 절차(Proprietary Operating Procedure)가 드러날 수 있다. 따라서 플릿 학습은 집단적인 모델 개선과 기밀성(Confidentiality), 데이터 소유권(Data Ownership), 규제 준수(Regulatory Compliance), 운용 보안(Operational Security) 요구사항 사이에서 균형을 유지해야 한다.

기본적인 원칙은 데이터 최소화(Data Minimization)이다. 로봇은 의도된 학습 목표에 필요한 정보만 수집하고 보관하며 전송해야 한다. 주행 모델이 식별 가능한 영상이 아니라 기하학적 특징(Geometric Feature)을 필요로 한다면 시스템은 해당 특징을 로컬에서 추출하고 원본 영상을 삭제하거나 접근을 제한할 수 있다. 데이터 생성 단계에서 불필요한 정보를 줄이면 개인정보 노출뿐 아니라 통신 및 저장공간 요구량도 감소한다.

로컬 처리(Local Processing)는 첫 번째 개인정보 보호 경계(Privacy Boundary)를 제공한다. 센서 스트림은 로봇 외부로 정보를 전송하기 전에 로봇 내부에서 특징(Feature), 임베딩(Embedding), 레이블(Label), 통계, 그래디언트(Gradient) 또는 모델 업데이트(Model Update)로 변환할 수 있다. 따라서 엣지 컴퓨팅(Edge Computing)은 지연시간을 줄이는 것뿐 아니라 민감한 원시 관측 정보를 데이터가 생성된 위치 가까이에 유지함으로써 개인정보 보호에도 기여한다.

연합 학습(Federated Learning)은 개인정보 보호형 플릿 지능(Privacy-Preserving Fleet Intelligence)을 구현하기 위한 주요 메커니즘이다. 참여 로봇 또는 사이트 수준의 엣지 시스템은 전체 로컬 데이터셋을 중앙 학습 서버에 업로드하는 대신 자체 데이터를 사용하여 모델을 학습한다. 이후 모델 업데이트를 전송하여 공유 글로벌 모델(Global Model)로 집계한다. 이러한 아키텍처는 기반이 되는 운용 데이터의 상당 부분을 로컬에 유지하면서 지식이 플릿 전체로 이동할 수 있도록 한다.

그러나 연합 학습 자체만으로 개인정보 보호가 보장되는 것은 아니다. 모델 파라미터(Model Parameter)와 그래디언트는 경우에 따라 해당 정보를 생성한 학습 샘플에 관한 정보를 노출할 수 있다. 공격자 또는 과도한 권한을 가진 집계 서비스(Aggregation Service)가 전송된 업데이트를 이용하여 로컬 데이터셋의 특성을 추론하려고 시도할 수 있다. 따라서 개인정보 보호형 플릿 학습은 원시 데이터뿐 아니라 분산 학습 과정에서 생성되는 중간 정보(Intermediate Information)도 보호해야 한다.

보안 집계(Secure Aggregation)는 집계 서버가 개별 참여자의 업데이트를 직접 확인하지 못하도록 하여 이러한 문제의 일부를 해결한다. 암호학적 메커니즘(Cryptographic Mechanism)을 이용하면 여러 로봇의 업데이트를 결합하여 서버가 집계 결과만 획득하고 개별 기여 내용은 숨길 수 있다. 이를 통해 중앙 학습 인프라에 노출되는 정보량을 줄이고 단일 집계 구성요소에 요구되는 신뢰 수준도 낮출 수 있다.

차등 개인정보 보호(Differential Privacy)는 데이터, 통계, 그래디언트 또는 모델 업데이트에 신중하게 제어된 무작위성(Randomness)을 추가하는 또 다른 보호 메커니즘이다. 목적은 특정 관측 정보가 학습 결과에 기여했는지를 판별하기 어렵게 만드는 것이다. 개인정보 보호 파라미터(Privacy Parameter)는 정보 보호와 모델 유용성(Model Utility) 사이의 절충관계를 제어하므로 시스템 설계자는 더 강력한 개인정보 보호를 위해 어느 정도의 정확도 감소를 허용할 것인지 결정해야 한다.

개인정보 보호 예산(Privacy Budget)은 차등 개인정보 보호에서 누적되는 정보 노출을 공식적으로 관리하는 방법을 제공한다. 반복적인 학습 라운드(Training Round)는 각 업데이트가 일정한 통계 정보를 노출하기 때문에 개인정보 보호 수준을 점진적으로 소모할 수 있다. 따라서 플릿 학습 시스템은 각 학습 라운드를 독립적으로 평가하지 않고 시간에 따른 개인정보 보호 지출(Privacy Expenditure)을 추적해야 한다. 로봇, 사용자 그룹, 데이터셋 또는 사이트가 허용된 개인정보 보호 예산에 접근하면 학습 참여를 중단하거나 변경해야 할 수 있다.

과도한 교란(Perturbation)은 모델 성능을 저하시킬 수 있고 너무 적은 노이즈(Noise)는 약한 보호만 제공하므로 노이즈는 신중하게 추가해야 한다. 대규모 플릿에서는 많은 참여자의 정보를 집계함으로써 개별 기여 정보를 보호하면서도 유용한 집단 수준 패턴(Population-Level Pattern)을 유지할 수 있는 경우가 있다. 적절한 메커니즘은 플릿 규모, 모델 민감도(Model Sensitivity), 학습 빈도, 정확도 저하가 운용에 미치는 영향에 따라 결정된다.

데이터 익명화(Data Anonymization)와 가명화(Pseudonymization)는 정보가 로봇 외부로 이동해야 하는 경우 노출 위험을 추가로 줄일 수 있다. 직접 식별자(Direct Identifier)는 제거하거나 다른 값으로 대체할 수 있으며 불필요한 메타데이터(Metadata)는 전송 전에 제외할 수 있다. 그러나 이동 궤적, 위치, 타임스탬프(Timestamp), 시각 특징 또는 겉보기에는 무해한 여러 속성의 조합을 이용해 개인이나 시설을 재식별(Reidentification)할 가능성이 있으므로 익명화를 절대적인 보호 수단으로 간주해서는 안 된다.

이동 데이터는 시설 배치와 운용 패턴을 노출할 수 있기 때문에 공간 개인정보 보호(Spatial Privacy)는 이동 로봇에서 특히 중요하다. 상세한 이동 궤적은 제한 구역, 생산 작업 흐름, 빈번하게 방문하는 자산 또는 사람의 활동 패턴을 드러낼 수 있다. 플릿 학습 파이프라인은 공간 집계(Spatial Aggregation), 해상도 감소, 영역 기반 통계, 선택적 보존 또는 전체 궤적 이력을 외부로 전송하지 않는 로컬 주행 지식 추출을 통해 이러한 위험을 줄일 수 있다.

시간 정보(Temporal Information) 역시 유사한 개인정보 보호 문제를 발생시킬 수 있다. 정밀한 타임스탬프는 작업 일정, 생산 주기, 유지보수 이벤트 또는 점유 패턴(Occupancy Pattern)을 노출할 수 있다. 학습 목표에 따라 시스템은 이벤트를 일정한 시간 구간으로 집계하거나 불필요한 시간 정밀도를 제거하고 운용 식별자와 학습 기록을 분리할 수 있다. 따라서 개인정보 보호 엔지니어링(Privacy Engineering)은 개별 데이터 필드만이 아니라 공간, 시간, 의미 및 신원 정보의 조합을 함께 검토해야 한다.

의미 지각(Semantic Perception)은 로봇이 사람, 차량, 장비, 문서, 화면, 제품 또는 활동을 인식할 수 있기 때문에 특별한 고려가 필요하다. 개인정보 보호형 지각 파이프라인(Privacy-Preserving Perception Pipeline)은 탐지를 로컬에서 수행하고 운용에 필요한 의미 결과만 공유할 수 있다. 예를 들어 플릿 조정 시스템은 식별 가능한 사람이 포함된 영상을 수신하지 않고도 특정 영역이 점유되어 있다는 정보만 필요할 수 있다.

개인정보 보호 강화 학습 기술을 사용하는 경우에도 접근 제어(Access Control)는 필요하다. 로봇, 포그 노드(Fog Node), 클라우드 서비스, 개발자, 운영자, 외부 파트너는 각 역할에 필요한 권한만 부여받아야 한다. 인증(Authentication), 권한 부여(Authorization), 최소 권한 접근(Least-Privilege Access), 암호화(Encryption), 키 관리(Key Management), 감사 로그(Audit Logging), 통제된 인터페이스는 개인정보 보호형 학습 메커니즘이 동작하는 보안 기반을 제공한다.

암호화는 로봇과 인프라 사이에서 이동하는 데이터와 저장된 데이터를 보호한다. 전송 암호화(Transport Encryption)는 네트워크 도청에 의한 노출을 줄이고 저장 암호화(Encrypted Storage)는 보관된 데이터셋, 체크포인트(Checkpoint), 모델 산출물(Model Artifact)을 보호한다. 동형 연산(Homomorphic Computation)이나 안전한 다자간 연산(Secure Multi-Party Computation)을 포함하는 고급 암호학적 방법은 보호된 정보에 대한 특정 연산을 지원할 수 있지만 연산 비용 때문에 실시간 로봇 응용에서는 사용이 제한될 수 있다.

신뢰 실행 환경(Trusted Execution Environment)은 민감한 집계 또는 학습 워크로드를 위한 추가적인 격리 경계(Isolation Boundary)를 제공할 수 있다. 선택된 연산을 다른 소프트웨어 구성요소의 접근을 제한하도록 설계된 보호된 하드웨어 영역에서 실행할 수 있다. 이러한 메커니즘은 특히 조직이 인프라 운영자와 기밀 학습 데이터 사이에 더 강력한 분리를 요구하는 경우 보안 집계 및 암호화를 보완할 수 있다.

개인정보 보호 정책(Privacy Policy)은 전체 데이터 생명주기(Data Lifecycle)를 따라야 한다. 정보는 센서에서 생성되고 로컬에서 처리되며 필요에 따라 보관되고 학습 산출물로 변환된 후 전송, 집계, 모델 개발에 사용되고 보관된 뒤 최종적으로 삭제된다. 네트워크 전송만 보호하는 개인정보 보호 제어는 원시 데이터셋이 무기한 저장되거나 오래된 모델 산출물이 의도된 보존 기간 이후까지 정보를 유지한다면 충분하지 않다.

따라서 데이터 보존 정책(Data Retention Policy)은 각 정보 범주를 얼마나 오랫동안 사용할 수 있으며 어떤 조건에서 삭제해야 하는지를 정의해야 한다. 원시 센서 데이터는 파생 통계(Derived Statistics) 또는 검증된 모델 업데이트보다 짧은 보존 기간이 필요할 수 있다. 보존 기간은 운용 필요성, 법적 요구사항, 디버깅 요구사항, 개인정보 보호 위험, 저장된 데이터가 미래의 데이터셋과 결합될 경우 더 많은 정보를 노출할 가능성을 반영해야 한다.

출처 추적(Provenance)과 거버넌스(Governance)는 학습 정보가 어디에서 생성되었으며 법적·운용적으로 사용할 수 있는지를 판단하는 데 필요하다. 모델 업데이트에는 불필요한 기반 데이터를 노출하지 않으면서 출처 범주, 동의 또는 승인 상태, 처리 정책, 소프트웨어 버전, 허용된 사용 목적을 설명하는 메타데이터를 포함할 수 있다. 거버넌스 메커니즘은 특정 목적으로 수집된 데이터가 관련 없는 학습 활동에 암묵적으로 재사용되는 것을 방지한다.

사이트 간 플릿 학습(Cross-Site Fleet Learning)은 추가적인 거버넌스 문제를 발생시킨다. 서로 다른 공장, 고객, 국가 또는 조직은 데이터 이동과 모델 학습에 서로 다른 규칙을 적용할 수 있다. 계층형 아키텍처(Hierarchical Architecture)는 원시 데이터를 각 사이트 내부에 유지하면서 승인된 모델 업데이트 또는 집계 지식(Aggregated Knowledge)만 교환할 수 있다. 정책 인식 집계(Policy-Aware Aggregation)는 특정 글로벌 학습 목표와 데이터 사용 조건이 호환되지 않는 참여자를 제외할 수 있다.

개인정보 보호(Privacy)와 보안(Security)은 서로 중첩되는 부분이 있지만 구분되어야 한다. 보안은 시스템과 정보를 무단 접근, 변경 또는 장애로부터 보호하는 반면 개인정보 보호는 정당한 시스템이 정보를 어떻게 수집하고, 사용하고, 결합하고, 보관하며, 공개하는지를 통제한다. 따라서 플릿이 기술적으로 안전하게 보호되어 있더라도 과도한 데이터를 수집하거나 필요한 기간보다 오래 정보를 보관한다면 개인정보 보호 원칙을 위반할 수 있다.

개인정보 보호는 안전(Safety) 및 추적 가능성(Traceability)과도 균형을 유지해야 한다. 운용 정보를 지나치게 제거하면 사고 조사가 어려워지거나 엔지니어가 안전 핵심 모델(Safety-Critical Model)을 검증하지 못할 수 있다. 따라서 목표는 무차별적인 삭제가 아니라 통제된 가용성(Controlled Availability)이어야 한다. 안전 로그, 학습 기록, 진단 증거(Diagnostic Evidence)는 각각의 목적에 따라 서로 다른 보존 기간, 접근 권한, 상세 수준을 적용할 수 있다.

모델 검증(Model Validation)은 개인정보 보호 메커니즘이 운용 성능을 허용 가능한 수준 이상으로 저하시켰는지를 확인해야 한다. 후보 모델(Candidate Model)은 개인정보 보호 변환이 적용된 이후 지각 정확도, 주행 성능, 이상 탐지 품질, 강건성(Robustness), 공정성(Fairness), 안전 관련 행동을 평가해야 한다. 개인정보 보호 보장은 그 결과로 생성된 모델이 의도된 로봇 기능을 수행하기에 충분한 신뢰성을 유지할 때 실질적인 가치를 갖는다.

개인정보 보호 인식 관측 가능성(Privacy-Aware Observability)은 보호하려는 민감한 데이터셋을 다시 만들어내지 않으면서 학습 인프라를 모니터링해야 한다. 운영자는 참여자 상태, 학습 진행 상황, 개인정보 보호 예산 소비, 집계 성공 여부, 정책 위반, 모델 성능에 관한 정보를 필요로 한다. 따라서 모니터링은 원시 로봇 관측 정보에 대한 무제한 접근 대신 신중하게 선택된 메타데이터와 집계 지표(Aggregate Metric)를 활용해야 한다.

시뮬레이션(Simulation)과 합성 데이터(Synthetic Data)는 개인정보에 민감한 실제 데이터셋에 대한 의존성을 줄일 수 있다. 디지털 트윈(Digital Twin)은 실제 사람이나 고객의 운용 상황을 기록하지 않고도 주행, 교통, 조작, 장애 시나리오를 생성할 수 있다. 합성 데이터가 모든 실제 관측을 대체할 수는 없지만 모델 개발에 필요한 민감한 정보의 양을 줄이고 제한적인 실제 환경 미세조정(Real-World Fine-Tuning)을 수행하기 전에 시험을 지원할 수 있다.

성숙한 아키텍처는 하나의 개인정보 보호 기술에만 의존하지 않고 여러 메커니즘을 결합한다. 로컬 처리는 원시 데이터 이동을 최소화하고, 연합 학습은 학습을 분산시키며, 보안 집계는 개별 업데이트를 숨기고, 차등 개인정보 보호는 정보 추론을 제한한다. 암호화는 통신과 저장 데이터를 보호하고 거버넌스는 허용된 사용 범위를 통제한다. 이러한 계층들은 함께 분산 플릿 지능(Distributed Fleet Intelligence)을 위한 심층 방어(Defense in Depth)를 제공한다.

궁극적으로 개인정보 보호형 플릿 학습은 집단 지능(Collective Intelligence)을 구현하기 위해 운용 데이터를 제한 없이 중앙에 수집해야 한다는 가정 없이도 로봇 플릿이 공동으로 학습할 수 있도록 한다. 민감한 정보를 생성 위치 가까이에 유지하고 필요한 학습 산출물만 공유하며 누적되는 정보 노출을 통제하고 전체 생명주기 거버넌스(Lifecycle Governance)를 적용함으로써 분산 로봇 시스템은 사람, 시설, 고객 및 독점적 운용 정보에 대한 강력한 보호 경계를 유지하면서 플릿 전체의 경험으로부터 지속적으로 발전할 수 있다.

## 06.09 Distributed Intelligence Latency and Consistency Trade

![](images/image9.png){width="7.268055555555556in" height="7.268055555555556in"}

로봇 플릿의 분산 지능(Distributed Intelligence)은 정보를 어디에서 처리할 것인지, 얼마나 빠르게 전파해야 하는지, 서로 다른 로봇이 공유 시스템 상태(Shared System State)를 어느 수준까지 일관되게 인식해야 하는지에 대한 지속적인 의사결정을 요구한다. 낮은 지연시간(Low Latency)은 로컬 및 비동기식 의사결정을 선호하는 반면, 강한 일관성(Strong Consistency)은 여러 참여자 사이의 조정, 동기화 또는 확인을 요구하는 경우가 많다. 이러한 목표는 서로 충돌할 수 있으므로 지연시간-일관성 절충(Latency--Consistency Trade-Off)은 대규모 다중 로봇 시스템의 핵심적인 아키텍처 설계 요소가 된다.

지연시간(Latency)은 이벤트가 발생한 시점부터 관련 구성요소가 이에 대응할 수 있는 시점까지 걸리는 시간을 의미한다. 로봇 플릿에서 지연시간에는 센서 처리, 네트워크 전송, 메시지 큐잉(Message Queuing), 분산 연산, 동기화, 액추에이터 응답이 포함될 수 있다. 기능에 따라 허용할 수 있는 지연은 크게 다르다. 비상 제동(Emergency Braking)은 밀리초 단위의 반응이 필요할 수 있지만, 플릿 최적화, 분석 또는 장기 모델 업데이트는 수초, 수분 또는 그 이상의 지연을 허용할 수 있다.

일관성(Consistency)은 분산된 참여자들이 공유 정보에 대해 어느 정도 동일한 상태에 합의하는지를 나타낸다. 로봇들은 지도, 작업 상태, 자원 예약, 교통 상황, 의미 지식(Semantic Knowledge), 정책 또는 학습 모델의 복사본을 유지할 수 있다. 강한 일관성은 참여자들이 작업을 진행하기 전에 조정된 상태를 관측하도록 하는 반면, 약한 일관성(Weaker Consistency)은 더 빠른 응답, 높은 가용성(Availability), 낮은 통신 오버헤드(Communication Overhead)를 얻기 위해 복제본 사이의 일시적인 차이를 허용한다.

강한 일관성은 서로 충돌하는 의사결정이 안전하지 않거나 운용적으로 유효하지 않은 상태를 만들 수 있는 경우 유용하다. 엘리베이터, 좁은 통로, 도킹 스테이션(Docking Station), 매니퓰레이터(Manipulator), 충전 커넥터에 대한 배타적 접근(Exclusive Access)은 명확하게 정의된 소유자(Owner)를 요구할 수 있다. 두 로봇이 동일한 배타적 예약을 동시에 보유하고 있다고 판단해서는 안 된다. 따라서 선택된 공유 자원에 대해서는 합의(Consensus), 잠금(Locking), 임대권(Lease), 트랜잭션 업데이트(Transactional Update) 또는 권위 있는 조정(Authoritative Coordination)이 필요할 수 있다.

그러나 모든 영역에서 강한 일관성을 강제하면 지연시간이 크게 증가하고 시스템 가용성이 감소할 수 있다. 로봇은 행동하기 전에 원격 노드의 응답 확인(Acknowledgment)을 기다려야 할 수 있으며, 네트워크 성능 저하는 원래 안전하게 수행할 수 있는 작업까지 지연시킬 수 있다. 또한 플릿 규모가 증가하면 조정 트래픽과 동기화 비용도 증가한다. 따라서 분산 지능에서는 모든 공유 변수가 즉각적인 글로벌 합의를 필요로 한다고 간주하지 않고 강한 일관성을 선택적으로 적용해야 한다.

최종적 일관성(Eventual Consistency)은 일시적인 불일치를 허용할 수 있고 복제본들이 이후에 수렴할 수 있는 경우 적합하다. 플릿 통계, 과거 성능 기록, 비핵심 의미 주석(Noncritical Semantic Annotation), 지도 메타데이터(Map Metadata), 진단 정보 또는 즉각적인 물리적 움직임을 직접 제어하지 않는 학습 지식 등이 이에 해당한다. 로봇은 로컬에서 사용할 수 있는 정보를 이용하여 계속 운용하면서 업데이트를 플릿 전체에 비동기식(Asynchronous)으로 전파할 수 있다.

강한 일관성과 최종적 일관성 사이의 선택은 정보 불일치가 초래할 수 있는 운용상의 결과를 기준으로 해야 한다. 불일치한 정보가 충돌, 중복된 자원 소유권, 상충하는 명령 또는 안전 제약조건 위반을 일으킬 수 있다면 더욱 강한 조정이 적절하다. 반면 불일치로 인해 일시적으로 최적이 아닌 경로 선택, 분석 지연 또는 약간 오래된 지식만 발생한다면 낮은 지연시간의 비동기식 메커니즘이 전체적으로 더 나은 성능을 제공할 수 있다.

엣지 컴퓨팅(Edge Computing)은 의사결정을 물리적인 로봇 가까이에 배치함으로써 지연시간을 줄인다. 충돌 회피, 로컬 궤적 제어(Local Trajectory Control), 장애물 대응, 위치추정(Localization), 즉각적인 안전 모니터링은 일반적으로 원격 인프라의 응답을 기다리지 않고 실행할 수 있어야 한다. 로컬 자율성(Local Autonomy)은 중요한 아키텍처 원칙을 형성한다. 결정론적 시간 한계(Deterministic Time Limit) 내에 수행해야 하는 물리적 반응의 직접적인 제어 경로에 네트워크 합의를 배치해서는 안 된다.

포그 또는 사이트 수준 컴퓨팅(Fog or Site-Level Computing)은 중간 조정 계층(Intermediate Coordination Layer)을 제공한다. 로컬 서버는 동일한 시설에서 운용되는 로봇의 교통 예약, 공유 지도, 지역 작업 상태, 자원 소유권을 관리할 수 있다. 원격 클라우드와의 통신보다 네트워크 거리가 짧기 때문에 허용 가능한 지연시간을 유지하면서 더욱 강력한 조정을 수행할 수 있다. 따라서 포그 인프라(Fog Infrastructure)는 글로벌 동기화 없이 사이트 전체의 일관성이 필요한 의사결정에 유용하다.

클라우드 시스템(Cloud System)은 즉각적인 응답보다 글로벌 가시성(Global Visibility)의 가치가 중요한 기능에 더 적합하다. 사이트 간 분석, 과거 데이터 기반 최적화, 모델 학습, 장기 계획, 소프트웨어 배포, 플릿 전체 정책 관리는 더 긴 시간 단위로 동작할 수 있다. 안전 핵심 제어(Safety-Critical Control)를 클라우드로 이동시키면 물리적 로봇 시스템에서 허용하기 어려운 광역 네트워크(Wide-Area Network)의 지연시간과 가용성에 의존하게 될 수 있다.

계층적 일관성(Hierarchical Consistency)은 엣지-포그-클라우드 분산 구조(Edge-Fog-Cloud Distribution)에서 자연스럽게 형성된다. 로봇은 강하게 일관된 로컬 제어 상태를 유지할 수 있고, 사이트는 조정된 지역 자원 상태를 유지할 수 있으며, 클라우드 인프라는 최종적으로 일관된 글로벌 요약(Global Summary)을 유지할 수 있다. 전체 플릿에 하나의 일관성 모델을 요구하는 대신 각 정보 도메인(Information Domain)에 해당 운용 범위에 적합한 조정 수준을 적용할 수 있다.

데이터 최신성(Data Freshness)은 일관성과 관련되어 있지만 별도로 다루어야 한다. 두 로봇이 내부적으로 유효한 정보를 가지고 있더라도 한쪽 복사본이 다른 쪽보다 상당히 오래되었을 수 있다. 타임스탬프(Timestamp), 시퀀스 번호(Sequence Number), 버전 식별자(Version Identifier), 임대권, 만료 시간(Expiration Time), 최신성 임계값(Freshness Threshold)을 사용하면 로봇은 해당 정보가 현재 의사결정에 여전히 적합한지 판단할 수 있다. 안전 핵심 정보는 엄격한 만료 기준을 요구할 수 있지만 천천히 변화하는 지식은 훨씬 오랫동안 유효할 수 있다.

환경이 빠르게 변화하는 경우 오래된 정보(Stale Information)는 특히 위험할 수 있다. 몇 초 전에 통행 가능하다고 보고된 통로에 현재 사람, 차량 또는 장애물이 존재할 수 있다. 따라서 분산 시스템은 글로벌 공유 상태가 로컬 지각(Local Perception)을 대체한다고 가정해서는 안 된다. 공유 지식은 계획을 지원할 수 있지만 즉각적인 물리적 안전은 현재의 온보드 센싱(Onboard Sensing)과 로컬에서 검증된 환경 정보에 계속 의존해야 한다.

네트워크 파티션(Network Partition)은 지연시간과 일관성의 절충관계를 직접적으로 드러낸다. 플릿 구성요소 사이의 통신이 중단되면 시스템은 조정된 상태를 요구하는 작업을 중지하거나 참여자들이 로컬 정보를 사용하여 계속 운용하도록 할 수 있다. 올바른 대응은 기능에 따라 달라진다. 배타적 공유 자원은 보수적인 차단(Conservative Blocking)이 필요할 수 있지만, 이전에 검증된 영역에서의 독립적인 주행은 로컬 자율성 아래에서 안전하게 지속할 수 있다.

플릿 규모가 증가할수록 가용성(Availability)은 더욱 중요해진다. 모든 의사결정이 하나의 권위 있는 서버(Authoritative Server)와의 통신을 요구한다면 서버 또는 네트워크 장애가 전체 플릿을 정지시킬 수 있다. 분산 아키텍처는 정책, 지도, 임무 맥락(Mission Context), 자원 정보를 로컬에 캐시함으로써 가용성을 향상시킬 수 있다. 그러나 캐시된 상태는 상태 발산(State Divergence)의 가능성을 만들기 때문에 연결이 끊어진 동안 어떤 의사결정을 계속 허용할 것인지 대체 운용(Fallback Operation) 규칙을 명확히 정의해야 한다.

임대권(Lease)은 일관성과 가용성 사이의 균형을 유지하기 위한 실용적인 메커니즘이다. 로봇은 정의된 시간 동안 특정 자원에 대한 임시 소유권(Temporary Ownership)을 받을 수 있다. 유효한 임대 기간에는 조정기(Coordinator)에 반복적으로 접속하지 않고 해당 자원을 사용할 수 있다. 임대 기간이 만료되면 소유권을 갱신하거나 반환해야 한다. 이를 통해 조정 지연을 줄이면서 통신 장애 이후 오래된 자원 할당에 무기한 의존하는 것을 방지할 수 있다.

버전 관리(Versioning)는 분산 지도, 정책, 모델 및 임무 데이터에서도 중요하다. 각 업데이트에는 단조 증가 버전(Monotonically Increasing Version), 논리적 타임스탬프(Logical Timestamp) 또는 개정 식별자(Revision Identifier)를 포함할 수 있다. 참여자는 오래된 정보를 탐지하고 전체 상태를 반복적으로 전송하는 대신 누락된 변경사항만 요청할 수 있다. 버전 인식 동기화(Version-Aware Synchronization)는 로봇이 독립적으로 운용한 후 다시 연결되는 경우에도 보다 통제된 상태 조정(Reconciliation)을 가능하게 한다.

비동기식 업데이트를 허용하는 경우 충돌 해결(Conflict Resolution)이 필요하다. 두 로봇은 동기화가 이루어지기 전에 서로 관련된 지도 요소, 의미 레이블, 작업 상태 또는 학습 정보를 각각 수정할 수 있다. 해결 정책은 타임스탬프, 권한 수준(Authority Level), 신뢰도(Confidence Value), 출처(Provenance), 운용 우선순위 또는 응용 분야별 병합 규칙(Application-Specific Merge Rule)을 사용할 수 있다. 물리적 결과가 발생할 수 있는 안전 핵심 충돌은 임의적인 최종 쓰기 우선(Last-Write-Wins) 방식으로 해결해서는 안 된다.

합의 프로토콜(Consensus Protocol)은 선택된 분산 의사결정에 강한 합의를 제공할 수 있지만 통신 및 연산 오버헤드를 발생시킨다. 따라서 여러 노드 사이의 합의가 실제로 정확성을 위해 필요한 정보에 한정하여 사용해야 한다. 모든 센서 관측이나 궤적 샘플에 분산 합의를 적용할 필요는 없다. 과도한 합의는 회복탄력적인 분산 아키텍처를 지연시간에 민감한 중앙집중형 의존 구조로 변화시킬 수 있다.

통신 서비스 품질(Quality of Service, QoS)은 서로 다른 정보 등급에 적절한 지연시간을 유지하는 데 도움을 줄 수 있다. 비상 이벤트, 안전 상태, 명령 권한(Command Authority), 핵심 자원 조정은 로그, 분석 정보, 지도 이력 또는 백그라운드 모델 업데이트보다 높은 우선순위를 가져야 한다. 데드라인 인식 스케줄링(Deadline-Aware Scheduling), 메시지 우선순위 지정, 제한된 큐(Bounded Queue), 대역폭 할당(Bandwidth Allocation)을 통해 낮은 우선순위의 트래픽이 적시에 필요한 정보 전달을 지연시키는 것을 방지할 수 있다.

적응형 일관성(Adaptive Consistency)은 플릿 성능을 더욱 향상시킬 수 있다. 필요한 조정 수준을 항상 고정할 필요는 없다. 로봇 밀도가 낮을 때에는 로컬 의사결정만으로 충분할 수 있지만 혼잡한 교차로에서는 더 강력한 지역 조정이 필요할 수 있다. 마찬가지로 통신 성능이 저하되면 보다 보수적인 로컬 정책을 활성화할 수 있다. 따라서 시스템은 위험 수준, 교통 밀도, 연결 상태, 임무 중요도(Mission Criticality)에 따라 일관성 메커니즘을 조정할 수 있다.

예측(Prediction)은 분산 지연으로 발생하는 실질적인 비용을 줄일 수 있다. 로봇은 이벤트가 실제로 발생하기 전에 예정된 궤적(Intended Trajectory), 예상 자원 사용량 또는 향후 작업 상태 전이를 전달할 수 있다. 주변 에이전트와 감독기(Supervisor)는 행동 완료를 기다리지 않고 자원을 미리 예약하거나 충돌 가능성을 사전에 탐지할 수 있다. 예측형 조정(Predictive Coordination)은 통신 지연 자체를 제거하지는 않지만 분산 참여자들이 서로 호환되는 의사결정에 도달할 수 있는 추가 시간을 제공한다.

시계 동기화(Clock Synchronization)도 분산 일관성에 영향을 준다. 동기화되지 않은 로봇에서 생성된 타임스탬프는 이벤트 순서(Event Ordering), 센서 융합(Sensor Fusion), 예약 유효성, 충돌 분석의 신뢰성을 떨어뜨릴 수 있다. 정밀 시간 프로토콜(Precision Time Protocol, PTP), 위성항법시스템 기반 시간(GNSS-Derived Time) 또는 기타 동기화 메커니즘을 통해 공통 시간 기준(Common Temporal Reference)을 제공할 수 있다. 필요한 동기화 정확도는 모든 구성요소에 불필요하게 높은 시간 정밀도를 요구하지 않고 응용 분야의 요구사항에 맞추어야 한다.

지연시간 및 일관성 장애를 진단하려면 관측 가능성(Observability)이 필수적이다. 모니터링 시스템은 종단 간 메시지 지연(End-to-End Message Delay), 동기화 시간, 큐 깊이(Queue Depth), 업데이트 경과 시간(Update Age), 복제본 발산(Replica Divergence), 타임아웃 빈도, 재전송, 임대권 만료, 합의 지연, 네트워크 파티션 이벤트를 기록해야 한다. 이러한 측정이 없으면 운영자는 불안정한 로봇 행동을 관찰하더라도 근본 원인이 계획, 통신 또는 오래된 분산 상태 중 어디에 있는지 판단하기 어렵다.

시뮬레이션(Simulation)과 디지털 트윈(Digital Twin)은 이상적인 네트워크가 아니라 현실적인 통신 조건에서 분산 지능을 시험해야 한다. 가변 지연시간, 패킷 손실(Packet Loss), 대역폭 제한, 지터(Jitter), 노드 장애, 네트워크 파티션, 지연된 동기화, 버스트 트래픽(Burst Traffic)을 적용하면 정상적인 시험에서는 드러나지 않는 행동을 확인할 수 있다. 특히 대규모 시뮬레이션은 로봇 수와 상호작용 밀도가 증가함에 따라 조정 오버헤드가 어떻게 변화하는지를 파악하는 데 유용하다.

성능 평가는 통신 지표와 운용 결과를 함께 고려해야 한다. 과도한 인프라를 요구한다면 낮은 네트워크 지연시간 자체가 반드시 유용한 것은 아니며, 플릿 처리량을 불필요하게 감소시킨다면 강한 일관성도 가치가 떨어진다. 주요 평가 지표에는 의사결정 지연시간(Decision Latency), 업데이트 전파 시간(Update Propagation Time), 오래된 상태 비율(Stale-State Ratio), 동기화 오버헤드, 자원 충돌 빈도, 임무 처리량, 복구 시간, 네트워크 활용률(Network Utilization), 안전 관련 개입 빈도가 포함된다.

성숙한 분산 아키텍처(Distributed Architecture)는 정보를 필요한 지연시간, 일관성, 최신성, 가용성 및 권한(Authority)에 따라 분류한다. 안전 제어는 로컬에서 결정론적으로 유지하고, 공유 물리 자원은 조정된 소유권(Coordinated Ownership)을 사용하며, 운용 지식은 제한된 일관성(Bounded Consistency) 또는 최종적 일관성을 사용할 수 있다. 장기 분석은 비동기식 수렴(Asynchronous Convergence)을 허용할 수 있다. 이러한 분류를 통해 하나의 분산 시스템 메커니즘을 모든 플릿 기능에 무차별적으로 적용하는 것을 방지할 수 있다.

궁극적으로 지연시간과 일관성은 절대적인 목표가 아니라 공학적 자원(Engineering Resource)으로 다루어야 한다. 가장 빠른 시스템이 반드시 가장 안전한 것은 아니며, 가장 강하게 동기화된 시스템이 반드시 가장 확장 가능하거나 회복탄력적인 것도 아니다. 로컬 자율성, 계층적 조정(Hierarchical Coordination), 선택적 강한 일관성(Selective Strong Consistency), 비동기식 지식 공유, 버전 관리, 서비스 품질(QoS), 신중하게 설계된 대체 동작(Fallback Behavior)을 결합하면 로봇 플릿은 대규모 분산 지능에 필요한 충분한 합의를 유지하면서도 적시에 의사결정을 수행할 수 있다.

## 06.10 Distributed Intelligence Production Case

![](images/image10.png){width="7.268055555555556in" height="7.268055555555556in"}

생산 로봇 플릿(Production Robot Fleet)의 분산 지능(Distributed Intelligence)은 자율성을 개별 기계의 독립적인 기능에서 조정된 운용 시스템(Coordinated Operational System)으로 전환한다. 실제 생산 환경에는 이동 로봇(Mobile Robot), 매니퓰레이터(Manipulator), 검사 플랫폼(Inspection Platform), 충전 인프라, 사이트 서버(Site Server), 클라우드 서비스(Cloud Service)가 포함될 수 있다. 지능은 하나의 중앙 제어기에 집중되는 것이 아니라 응답시간, 정보 범위, 연산 요구량, 운용 권한(Operational Authority)에 따라 분산된다.

수백 대의 자율이동로봇(Autonomous Mobile Robot)이 입고, 보관, 생산 공급, 검사, 출하 영역에서 운용되는 대규모 제조 및 물류 시설을 고려할 수 있다. 로봇들은 통로, 교차로, 엘리베이터, 충전소, 작업 셀(Work Cell)을 공유하면서 운송 및 검사 임무를 지속적으로 수행한다. 생산 시스템의 목표는 단순히 모든 로봇을 자율화하는 것이 아니라 지속적으로 변화하는 조건에서 안전하고 신뢰할 수 있는 시설 수준 처리량(Facility-Level Throughput)을 극대화하는 것이다.

각 로봇은 분산 아키텍처의 엣지 계층(Edge Layer)을 구성한다. 온보드 컴퓨팅(Onboard Computing)은 위치추정(Localization), 지각(Perception), 장애물 탐지, 궤적 생성(Trajectory Generation), 모션 제어, 상태 모니터링(Health Monitoring), 즉각적인 안전 대응을 수행한다. 이러한 기능은 상위 인프라와의 통신이 일시적으로 저하되어도 계속 동작한다. 로컬 자율성(Local Autonomy)은 네트워크 지연이나 중앙 서버 장애가 기본적인 물리적 안전의 직접적인 의존 요소가 되는 것을 방지한다.

로봇 감독기(Robot Supervisor)는 할당된 임무를 실행 가능한 행동으로 변환한다. 운송 임무에는 픽업 지점까지의 주행, 도킹(Docking), 적재물 확인, 경로 주행, 목적지 정렬, 하역, 완료 보고가 포함될 수 있다. 감독기는 진행 상태를 모니터링하면서 일시적인 장애물, 도킹 실패, 위치추정 불확실성 또는 경미한 경로 변경과 같은 일반적인 예외 상황을 상위 조정 계층에 지원을 요청하기 전에 자체적으로 처리한다.

사이트 수준에서는 포그 인프라(Fog Infrastructure)가 보다 넓은 운용 상황을 관리한다. 포그 인프라는 로봇으로부터 요약된 상태 정보를 수신하여 교통, 작업 분배, 공유 자원, 충전 수요, 지도 업데이트, 지역 혼잡을 조정한다. 이러한 인프라는 원격 클라우드 서비스보다 물리적·논리적으로 로봇에 가까이 위치하므로 비교적 낮은 지연시간과 강한 일관성(Strong Consistency)이 필요한 사이트 전체 의사결정을 지원할 수 있다.

클라우드 인프라(Cloud Infrastructure)는 즉각적인 모션 제어가 아니라 장기적이고 사이트 간에 적용되는 지능을 제공한다. 과거 플릿 데이터는 용량 분석(Capacity Analysis), 예지 정비(Predictive Maintenance), 모델 학습, 정책 최적화, 소프트웨어 관리, 여러 시설 간 비교에 활용할 수 있다. 클라우드 연결이 중단되더라도 생산은 로컬에서 계속되며, 클라우드는 실시간 안전이나 기본 임무 수행의 필수 구성요소가 되지 않으면서 플릿 지능을 향상시킨다.

분산 지도(Distributed Map)는 플릿을 위한 공통 공간 기반(Common Spatial Foundation)을 제공한다. 개별 로봇은 장애물, 차단된 통로, 변경된 작업 영역, 의미 객체(Semantic Object)에 대한 관측 정보를 제공한다. 사이트 인프라는 검증된 업데이트를 병합하고 관련 정보를 인접 영역에서 운용되는 로봇에 다시 배포한다. 따라서 하나의 로봇은 동일한 장소를 직접 방문하지 않고도 다른 로봇이 감지한 환경 변화의 정보를 활용할 수 있다.

의미 지식(Semantic Knowledge)은 공유 지도에 운용상의 의미를 부여한다. 특정 위치는 단순히 비어 있거나 점유된 공간으로 표현되는 것이 아니라 적재 구역, 보행자 횡단 구역, 제한 구역, 충전소, 검사 지점 또는 임시 공사 구역으로 식별될 수 있다. 로봇은 이러한 의미 정보를 사용하여 경로 선택과 임무 행동을 조정하고, 사이트 감독기(Site Supervisor)는 이를 이용하여 시설 정책과 자원 제약조건을 적용한다.

작업 할당(Task Allocation)은 글로벌 목표(Global Objective)와 로컬 실행 능력(Local Execution Capability) 사이에 분산된다. 플릿 관리자(Fleet Manager)는 임무 우선순위, 로봇 위치, 배터리 상태, 적재 능력, 로봇 상태, 교통 상황, 작업 부하를 고려한다. 로봇은 로컬 제약조건이나 현재 능력을 위반하는 작업 할당을 거부하거나 재협상할 수 있다. 이를 통해 글로벌 최적화 시스템이 물리적 상태나 운용 역할이 서로 다른 로봇을 동일한 자원으로 취급하는 것을 방지할 수 있다.

교통 조정(Traffic Coordination)은 생산 환경에서 분산 지능이 필요한 이유를 잘 보여준다. 개별 충돌 회피(Individual Collision Avoidance)는 직접적인 접촉을 방지할 수 있지만 효율적인 플릿 흐름(Fleet Flow)을 보장하지는 못한다. 사이트 수준의 조정 시스템은 교차로, 좁은 통로, 대기열, 경로 예약(Route Reservation)을 관리하는 반면 로봇은 즉각적인 장애물 회피 권한을 유지한다. 따라서 로컬 안전과 지역 교통 최적화가 서로 다른 의사결정 계층에서 동시에 수행된다.

공유 자원(Shared Resource)은 일반적인 환경 지식보다 강한 조정을 요구한다. 엘리베이터, 자동문, 도킹 스테이션, 충전 커넥터, 좁은 통로는 한 번에 하나 또는 제한된 수의 로봇만 사용할 수 있다. 예약(Reservation), 임대권(Lease) 또는 권위 있는 소유권(Authoritative Ownership)을 이용하여 충돌하는 접근을 방지하고, 로컬 제어기는 해당 자원에 진입하거나 사용하기 전에 실제 물리적 조건이 안전한지를 검증한다.

플릿 규모가 증가할수록 충전 관리(Charging Management)의 중요성도 커진다. 모든 로봇이 동일한 배터리 임계값에서 독립적으로 충전을 시작하면 동기화된 충전 수요(Synchronized Charging Demand)가 발생하여 가용 플릿 용량이 감소할 수 있다. 사이트 지능은 에너지 요구량을 예측하고, 충전 일정을 분산하며, 충전기를 예약하고, 향후 임무 수요를 고려할 수 있다. 개별 로봇은 최소 배터리 안전 한계를 계속 적용하여 플릿 최적화와 로컬 에너지 보호가 함께 작동하도록 한다.

통신에는 모든 메시지를 동일하게 처리하는 대신 차등화된 서비스 품질(Quality of Service, QoS)을 적용한다. 비상 상태, 안전 정보, 자원 소유권, 핵심 명령은 로그, 과거 지도 데이터, 분석 정보 또는 백그라운드 학습 업데이트보다 높은 우선순위를 갖는다. 이를 통해 무선 대역폭이 혼잡한 상황에서도 시간에 민감한 조정 기능을 보호하고 중요하지 않은 정보가 생산 핵심 통신(Production-Critical Communication)을 방해하는 것을 방지한다.

생산 네트워크에서는 패킷 손실(Packet Loss), 가변적인 지연시간, 일시적인 연결 단절, 인프라 장애가 불가피하게 발생한다. 따라서 로봇은 필요한 지도, 정책, 임무 맥락(Mission Context), 최근 자원 정보를 캐시(Cache)한다. 연결이 끊어진 동안에는 대체 운용 규칙(Fallback Rule)이 허용하는 작업만 계속 수행한다. 현재의 공유 소유권이 필요한 행동은 차단할 수 있지만 독립적인 주행과 이미 검증된 안전한 행동의 완료는 로컬에서 계속할 수 있다.

일관성 요구사항(Consistency Requirement)은 정보 종류에 따라 달라진다. 충전 커넥터 예약에는 강한 합의가 필요할 수 있지만 의미 지도 주석(Semantic Map Annotation)은 비동기식 전파를 허용할 수 있다. 과거의 활용률 통계는 현재 운용에 영향을 주지 않으므로 훨씬 늦게 수렴해도 된다. 정보를 지연시간, 최신성(Freshness), 일관성, 가용성, 권한에 따라 분류하면 모든 분산 데이터 교환에 비용이 높은 동기화를 적용하는 것을 방지할 수 있다.

실용적인 생산 시스템에서는 버전 관리(Versioning)와 타임스탬프(Timestamp)도 광범위하게 사용한다. 지도, 정책, 임무 정의, 모델, 구성 데이터(Configuration Data)는 식별 가능한 개정 버전(Revision)을 갖는다. 로봇은 로컬에 캐시된 정보가 오래되었는지 탐지하고 필요한 변경사항만 요청할 수 있다. 연결이 끊겼던 로봇이 네트워크에 복귀하면 버전 인식 동기화(Version-Aware Synchronization)를 통해 유효한 정보를 무조건 덮어쓰지 않고 업데이트를 조정할 수 있다.

연합 학습(Federated Learning)은 분산 운용에서 분산 개선(Distributed Improvement)으로 아키텍처를 확장할 수 있다. 로봇 또는 사이트 서버는 로컬에서 생성된 데이터를 이용하여 선택된 모델을 학습하고 전체 원시 데이터셋 대신 모델 업데이트를 교환한다. 이를 통해 잠재적으로 민감한 생산 데이터의 이동을 줄이면서 플릿의 경험을 활용하여 지각, 이상 탐지(Anomaly Detection), 운용 예측 모델을 개선할 수 있다.

로봇이 작업자, 고객 시설, 독점적인 공정 또는 제한된 인프라를 관측하는 경우 개인정보 보호형 메커니즘(Privacy-Preserving Mechanism)이 중요해진다. 로컬 처리를 통해 원시 센서 데이터를 공유하기 전에 특징, 의미 레이블, 통계 또는 모델 업데이트로 변환할 수 있다. 보안 집계(Secure Aggregation), 암호화(Encryption), 접근 제어(Access Control), 보존 정책(Retention Policy), 데이터 거버넌스(Data Governance)는 플릿 전체 학습에 사용되는 정보에 추가적인 보호 경계를 제공한다.

다중 에이전트 강화학습(Multi-Agent Reinforcement Learning, MARL)은 수작업으로 최적화하기 어려운 조정 문제에 선택적으로 도입할 수 있다. 시뮬레이션으로 학습된 정책은 작업 할당, 교통 협상(Traffic Negotiation), 자원 선택 또는 혼잡 회피를 지원할 수 있다. 학습된 의사결정은 로봇 감독기, 시설 정책, 결정론적 안전 계층(Deterministic Safety Layer)에 의해 제한된다. 따라서 생산 환경에서는 MARL을 기존 공학적 제어를 제한 없이 대체하는 수단이 아니라 최적화 메커니즘으로 사용한다.

대규모 플릿에서는 개별 로봇 수준에서 보이지 않는 시스템 수준 패턴이 발생할 수 있으므로 창발적 행동(Emergent Behavior)을 모니터링해야 한다. 혼잡 파동(Congestion Wave), 동기화된 충전, 작업 진동(Task Oscillation), 대기열 증가, 자원 기아(Resource Starvation)는 모든 로봇이 로컬 규칙에 따라 올바르게 행동하더라도 발생할 수 있다. 따라서 플릿 관측 가능성(Fleet Observability)은 개별 로봇 진단뿐 아니라 집단 수준 지표(Collective Indicator)도 포함해야 한다.

운용 텔레메트리(Operational Telemetry)는 이러한 현상을 이해하는 데 필요한 근거를 제공한다. 시스템은 임무 처리량, 완료 시간, 대기 시간, 교통 밀도, 자원 활용률, 배터리 상태, 통신 지연, 오래된 정보(Stale Information), 복구 시도, 장애 빈도, 안전 개입을 기록한다. 이러한 측정값은 네트워크 또는 인공지능 지표를 독립적으로 평가하는 대신 분산 컴퓨팅 성능을 실제 생산 결과와 연결한다.

장애 복구(Failure Recovery)는 계층적 에스컬레이션(Hierarchical Escalation)을 따른다. 로봇은 먼저 재계획(Replanning), 재시도, 재위치추정(Re-Localization), 일시적인 대기를 통해 로컬 복구를 시도한다. 문제가 여러 로봇 또는 공유 자원과 관련된 경우 사이트 감독기가 복구 또는 작업 재할당을 조정한다. 자율 복구가 정의된 권한, 안전 한계 또는 신뢰도 임계값을 초과하는 경우 사람 운영자가 개입함으로써 불필요한 수동 개입을 줄인다.

생산 시스템은 하나의 중앙집중형 시스템처럼 전체가 동시에 실패하는 것이 아니라 단계적으로 성능이 저하되는 우아한 성능 저하(Graceful Degradation)를 지원해야 한다. 클라우드 연결이 상실되면 사이트 운용보다 먼저 글로벌 분석 기능이 중단된다. 사이트 조정기가 고장 나면 지역 최적화 능력이 감소하지만 로봇은 안전한 로컬 행동을 유지한다. 개별 로봇 장애는 전체 플릿 정지가 아니라 작업 재분배를 유발한다. 따라서 분산된 권한은 아키텍처 계층 사이에서 장애가 확산되는 것을 제한한다.

디지털 트윈(Digital Twin)과 시뮬레이션(Simulation)은 변경사항을 실제 운용 플릿에 적용하기 전에 반드시 활용해야 하는 중요한 수단이다. 새로운 교통 정책, 작업 할당 전략, 통신 설정, 소프트웨어 버전, 학습 모델을 높은 로봇 밀도, 네트워크 성능 저하, 충전기 부족, 차단된 경로, 장비 장애 조건에서 평가할 수 있다. 이후 실제 생산 배포는 시뮬레이션, 섀도 테스트(Shadow Testing), 제한적 배포, 플릿 전체 배포 순으로 점진적으로 진행할 수 있다.

아키텍처에는 명확한 롤백(Rollback)과 구성 관리(Configuration Control)도 필요하다. 배포된 모든 정책, 모델, 지도, 소프트웨어 구성요소에는 추적 가능한 버전과 호환성 상태(Compatibility State)가 있어야 한다. 새로운 조정 정책이 처리량을 감소시키거나 불안정한 행동을 발생시키는 경우 운영자는 검증된 구성으로 신속하게 복원할 수 있어야 한다. 따라서 분산 지능은 정교한 알고리즘뿐 아니라 체계적인 생명주기 엔지니어링(Lifecycle Engineering)에도 크게 의존한다.

생산 환경에서 가장 중요한 원칙은 지능을 해당 정보 및 시간 요구사항을 신뢰성 있게 충족할 수 있는 위치에 배치하는 것이다. 즉각적인 물리적 반응은 로봇에 배치하고, 지역 조정은 사이트 가까이에서 수행하며, 연산 집약적인 장기 지능은 중앙 시스템이나 클라우드에서 수행할 수 있다. 공유 지식(Shared Knowledge)은 모든 의사결정을 동일한 인프라를 거치도록 강제하지 않으면서 이러한 계층을 연결한다.

따라서 성공적인 생산 적용 사례(Production Case)는 아키텍처가 얼마나 분산되어 있거나 지능적으로 보이는지가 아니라 실제 운용 결과로 평가해야 한다. 로봇 수가 증가하더라도 플릿은 안전, 처리량, 가용성, 예측 가능한 복구, 확장 가능한 통신, 관리 가능한 사람의 감독(Human Supervision)을 유지해야 한다. 추가되는 로봇이 생산 능력을 증가시키면서도 조정 복잡성이 운용 통제 범위를 넘어서지 않을 때 분산 지능은 실질적인 가치를 갖는다.

궁극적으로 생산 수준의 분산 지능(Production-Grade Distributed Intelligence)은 로컬 자율성, 사이트 수준 조정, 클라우드 규모 학습(Cloud-Scale Learning), 공유 의미 지식(Shared Semantic Knowledge), 선택적 일관성(Selective Consistency), 회복탄력적인 통신(Resilient Communication), 계층적 복구, 결정론적 안전을 결합한다. 이러한 메커니즘을 통해 수백 또는 수천 대의 로봇은 하나의 조정된 운용 시스템처럼 행동하면서도 실시간 물리 제어, 장애 허용(Fault Tolerance), 확장 가능한 다중 로봇 생산에 필요한 로컬 독립성을 유지할 수 있다.
