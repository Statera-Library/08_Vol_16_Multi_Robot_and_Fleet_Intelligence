**Volume 16 Multi Robot and Fleet Intelligence**

# 07. Swarm Robotics

## 07.01 Swarm Intelligence Principles Stigmergy Self Organization

![](images/image1.png){width="7.268055555555556in" height="7.268055555555556in"}

군집 지능(Swarm Intelligence)은 비교적 단순한 다수의 로봇이 지속적인 중앙집중식 제어(Centralized Control)에 의존하지 않고, 국소 감지(Local Sensing), 상호작용(Interaction), 적응(Adaptation)을 통해 협력적인 행동을 만들어 내는 집단적 문제 해결(Collective Problem Solving) 방식이다. 따라서 군집 로보틱스(Swarm Robotics)에서 지능은 감독 시스템(Supervisor)이나 개별 로봇에만 존재하지 않으며, 로봇과 이웃 로봇, 물리적 환경(Physical Environment) 사이에서 반복되는 상호작용을 통해 출현한다.

이러한 원리는 군집(Swarm)을 기존의 중앙집중식으로 관리되는 로봇 플릿(Robot Fleet)과 구별한다. 플릿 관리 시스템(Fleet Management System)은 전역 정보(Global Knowledge)를 유지하면서 명시적인 임무를 할당하고, 경로를 계산하며, 중앙 서비스(Central Service)를 통해 충돌과 자원 경쟁을 해결할 수 있다. 반면 군집은 분산 의사결정(Distributed Decision Making), 국소 규칙(Local Rules), 중복성(Redundancy), 집단적 적응(Collective Adaptation)을 강조한다. 개별 로봇이 제한된 정보만 보유하더라도 반복적인 국소 상호작용을 통해 유용한 전역 행동(Global Behavior)을 생성할 수 있다.

군집 지능의 생물학적 영감(Biological Inspiration)은 개미 군집(Ant Colony), 벌 군집(Bee Colony), 새 무리(Bird Flock), 물고기 떼(Fish School), 사회성 곤충(Social Insects) 등에서 얻을 수 있다. 개별 생물은 일반적으로 집단 전체 상태에 대한 완전한 표현을 유지하지 않는다. 대신 주변 개체, 환경 조건(Environmental Conditions), 국소적으로 이용 가능한 신호에 반응한다. 이러한 상호작용이 대규모 개체군 전체에서 반복되면서 이동 경로, 대형(Formation), 자원 할당(Resource Allocation), 협력 이동(Coordinated Movement)과 같은 구조가 형성된다.

자기조직화(Self-Organization)는 중앙 제어기가 모든 상호작용을 명시적으로 지정하지 않아도 전역적인 질서(Global Order)가 형성되는 과정이다. 특히 세 가지 메커니즘이 중요하다. 양의 피드백(Positive Feedback)은 유용한 행동을 증폭시키고, 음의 피드백(Negative Feedback)은 과도한 증폭을 방지하며, 무작위 탐색(Random Exploration)은 행동의 다양성을 제공한다. 이러한 메커니즘의 결합을 통해 군집은 변화하는 환경 조건에 대응하면서 적절한 해결책을 발견할 수 있다.

양의 피드백(Positive Feedback)은 성공적인 집단 의사결정(Collective Decision)을 강화할 수 있다. 넓은 영역을 탐색하던 로봇들이 유용한 지역을 발견하면 해당 지역과 관련된 정보가 강화되어 추가 로봇이 그 지역을 탐색할 가능성이 증가할 수 있다. 그러나 무제한적인 강화는 전체 군집을 하나의 해결책에 과도하게 집중시킬 수 있다. 따라서 음의 피드백(Negative Feedback), 자원 제한(Resource Limits), 혼잡 효과(Congestion Effects), 신호 감쇠(Signal Decay), 명시적인 억제(Inhibition) 등을 통해 안정성을 유지하고 활동을 분산시켜야 한다.

무작위성(Randomness) 역시 기능적인 목적을 가진다. 완전히 결정론적인 군집(Deterministic Swarm)은 국소적으로는 매력적이지만 전역적으로는 비효율적인 행동으로 반복해서 수렴할 수 있다. 탐색 방향, 이동 방향, 작업 선택 또는 통신에 작은 확률적 변화(Stochastic Variation)를 도입하면 조기 수렴(Premature Convergence)을 방지할 수 있다. 따라서 군집 설계(Swarm Design)는 알려진 기회를 활용하는 활용(Exploitation)과 새로운 대안을 찾는 탐색(Exploration)의 균형을 통해 중앙집중식 최적화 없이도 적응성을 확보한다.

스티그머지(Stigmergy)는 간접 협력(Indirect Coordination)을 구현하는 특히 중요한 메커니즘이다. 로봇이 다른 모든 로봇과 직접 통신하는 대신 공유 환경(Shared Environment)의 일부 표현을 변경하고, 다른 로봇이 그 변화에 반응하도록 한다. 결과적으로 환경 자체가 협력 메커니즘(Coordination Mechanism)의 일부가 된다. 생물학적인 페로몬 경로(Pheromone Trail)가 대표적인 사례이며, 로봇에서는 디지털 마커(Digital Marker), 지도(Map), 점유 정보(Occupancy Information), 공유 작업 상태(Shared Task State), 가상 페로몬(Virtual Pheromone) 등으로 구현할 수 있다.

가상 페로몬 시스템(Virtual Pheromone System)은 위치, 자원, 위험 요소 또는 작업에 수치 값을 연결할 수 있다. 로봇은 작업을 수행하면서 값을 남기거나 강화하고, 이러한 값은 시간이 지나면서 점차 감쇠한다. 다른 로봇들은 형성된 정보장(Information Field)을 국소 의사결정(Local Decision)의 입력으로 활용한다. 강화(Reinforcement)는 계속 유용한 정보를 유지하는 반면, 증발(Evaporation)은 오래된 정보를 제거하여 경로, 장애물, 작업량 또는 환경 조건이 변할 때 군집이 적응할 수 있도록 한다.

스티그머지(Stigmergy)는 협력이 반드시 지속적인 로봇 간 협상(Robot-to-Robot Negotiation)에 의존하지 않기 때문에 통신 요구량을 줄일 수 있다. 로봇은 주변의 환경 마커(Environmental Marker)나 국소적으로 동기화된 표현에만 접근해도 될 수 있다. 이러한 특성은 네트워크 연결이 간헐적이거나 대역폭(Bandwidth)이 제한되거나, 로봇 수가 많아져 전역적인 전대전 통신(All-to-All Communication)의 비용이 커지는 상황에서 유용하다. 직접 통신(Direct Communication)과 스티그머지 기반 협력은 함께 사용할 수도 있다.

국소 상호작용(Local Interaction)은 군집 행동의 또 다른 핵심 기반이다. 각 로봇은 일반적으로 센싱 범위(Sensing Range), 통신 범위(Communication Range), 토폴로지(Topology), 운영상의 관련성에 의해 정의되는 주변 영역만 관찰한다. 로봇의 제어 정책(Control Policy)은 국소 관측(Local Observation)을 이동, 주변 로봇 회피, 대형 합류, 작업 선택, 정보 방송(Broadcasting) 등의 행동으로 변환한다. 전역 행동은 수많은 국소 인지-행동 순환(Local Perception-Action Cycle)이 동시에 발생하면서 출현한다.

창발(Emergence)은 군집 행동이 신비하거나 통제되지 않는다는 의미가 아니다. 이는 거시적 행동(Macroscopic Behavior)이 모든 단계를 명시적으로 지시받는 것이 아니라 더 단순한 미시적 규칙(Microscopic Rules) 사이의 상호작용으로 생성된다는 의미다. 따라서 엔지니어는 국소 규칙을 설계하고 검증할 때 집단적인 결과까지 고려해야 한다. 하나의 로봇에는 합리적인 규칙이라도 수백 대의 로봇에 반복 적용되면 혼잡(Congestion), 진동(Oscillation), 교착상태(Deadlock), 군집 분열(Fragmentation), 불안정한 피드백(Unstable Feedback)을 발생시킬 수 있다.

확장성(Scalability)은 군집 아키텍처(Swarm Architecture)를 사용하는 주요 이유 중 하나이다. 중앙집중식 시스템(Centralized System)은 로봇 수가 증가함에 따라 연산, 통신, 협력의 병목현상(Bottleneck)에 직면할 수 있다. 잘 설계된 군집은 이러한 작업의 상당 부분을 구성원들에게 분산한다. 이에 따라 로봇을 추가함으로써 센싱 범위, 병렬성(Parallelism), 운영 능력(Operational Capacity)을 증가시키면서도 모든 협력 기능을 중앙 제어기에서 동일한 비율로 확장할 필요가 없어진다.

강건성(Robustness)은 중복성(Redundancy)이라는 특성과 밀접하게 연결된다. 집단 행동이 소수의 핵심 로봇이 아니라 상호 대체 가능한 다수 로봇의 기여에 의존한다면, 일부 로봇의 고장은 전체 임무 실패보다 점진적인 성능 저하(Graceful Degradation)로 이어질 수 있다. 남아 있는 로봇은 작업을 재분배하고, 공간적 공백을 메우며, 통신 이웃 관계를 재구성하거나 탐색을 계속할 수 있다. 따라서 점진적 성능 저하는 군집 설계에서 중요한 목표가 된다.

그러나 군집 시스템(Swarm System)에도 자율성(Autonomy)의 한계가 필요하다. 순수한 국소 규칙만으로 안전(Safety), 임무 우선순위(Mission Priority), 규제 준수(Regulatory Compliance), 전역 자원 최적화(Global Resource Optimization)를 자동으로 보장할 수는 없다. 따라서 산업용 구현에서는 군집 지능과 감독 제약(Supervisory Constraints)을 결합할 수 있다. 상위 계층은 운영 구역, 안전 경계, 임무 목표, 충전 정책, 비상 명령 등을 정의하면서 로봇이 하위 수준의 집단 의사결정에 대해 분산된 권한을 유지하도록 할 수 있다.

이는 제어(Control)와 제약(Constraint) 사이에 중요한 차이를 만든다. 감독 시스템(Supervisor)이 모든 로봇의 궤적이나 작업을 직접 결정할 필요는 없다. 대신 자기조직화 행동(Self-Organizing Behavior)이 허용되는 운영 범위(Operating Envelope)를 정의할 수 있다. 이러한 하이브리드 아키텍처(Hybrid Architecture)는 군집의 확장성과 복원력을 상당 부분 유지하면서 산업용 로봇 운영에 필요한 관측 가능성(Observability), 거버넌스(Governance), 결정론적 개입(Deterministic Intervention) 기능을 제공한다.

통신 토폴로지(Communication Topology)는 집단 행동에 강한 영향을 미친다. 국소 방송(Local Broadcast)을 사용하면 완전한 전역 통신 그래프(Global Communication Graph)를 구성하지 않고도 주변 로봇의 상태를 파악할 수 있다. 정보는 반복적인 피어 상호작용(Peer Interaction)을 통해 전파되므로 멀리 떨어져 직접 통신하지 않는 두 로봇 사이에서도 지식이 군집 전체로 확산될 수 있다. 이러한 원리는 이후의 국소 방송 통신, 분산 작업 할당(Distributed Task Assignment), 대형 제어(Formation Control), 고장 허용(Fault Tolerance)과 자연스럽게 연결된다.

로봇의 공간적 분포(Spatial Distribution) 역시 중요하다. 통신, 센싱, 물리적 움직임이 서로 결합되어 있기 때문이다. 하나의 로봇은 동시에 이동형 센서(Mobile Sensor), 연산 에이전트(Computational Agent), 통신 참여자(Communication Participant), 물리적 액추에이터(Physical Actuator)의 역할을 수행할 수 있다. 따라서 한 로봇의 위치 변화는 센싱 범위, 네트워크 연결성(Network Connectivity), 충돌 위험, 정보 전파에 동시에 영향을 줄 수 있다. 군집 협력에서는 정보 토폴로지(Information Topology)와 물리적 토폴로지(Physical Topology)를 함께 고려해야 한다.

군집 행동은 여러 관찰 수준에서 이해할 수 있다. 개별 수준(Individual Level)에서는 센싱, 국소 상태, 제어 규칙, 통신을 분석한다. 이웃 수준(Neighborhood Level)에서는 상호작용 패턴과 정보 전파를 연구한다. 개체군 수준(Population Level)에서는 커버리지(Coverage), 수렴(Convergence), 처리량(Throughput), 강건성, 안정성(Stability)을 평가한다. 성공적인 군집 설계를 위해서는 개별 로봇의 성능만 평가하는 것이 아니라 이러한 수준들을 서로 연결해서 분석해야 한다.

핵심적인 공학적 과제는 원하는 전역 행동이 국소 규칙으로부터 안정적으로 출현하는지를 예측하는 것이다. 집단 현상(Collective Phenomena)은 더 큰 로봇 개체 수나 특정 밀도, 통신 손실, 지연, 고장 조건에서만 나타날 수 있으므로 시뮬레이션(Simulation)이 특히 중요하다. 10대의 로봇에서는 정상적으로 동작한 매개변수가 수백 대에서는 혼잡이나 불안정한 상호작용을 만들 수 있다. 따라서 군집 평가는 정상 조건뿐 아니라 규모 확장에 따른 행동(Scaling Behavior)을 분석해야 한다.

성능 지표(Metrics)는 집단적 목표를 반영해야 한다. 응용 분야에 따라 작업 완료율(Task Completion Rate), 영역 커버리지(Area Coverage), 수렴 시간(Convergence Time), 통신 오버헤드(Communication Overhead), 에너지 소비(Energy Consumption), 충돌 빈도(Collision Frequency), 공간적 분산(Spatial Dispersion), 로봇 고장 이후의 복원력(Resilience), 복구 시간(Recovery Time) 등을 사용할 수 있다. 이러한 지표는 빠른 수렴과 탐색, 밀집된 협력과 혼잡, 풍부한 통신과 대역폭 소비, 중복성과 운영 효율 사이의 절충관계(Trade-off)를 보여준다.

따라서 산업용 군집 로보틱스(Industrial Swarm Robotics)는 단순히 동일한 로봇을 많이 배치하는 것을 의미하지 않는다. 이는 국소 자율성(Local Autonomy), 분산 상호작용(Decentralized Interaction), 자기조직화(Self-Organization), 중복성(Redundancy), 창발적 집단 행동(Emergent Collective Behavior)을 의도적으로 설계하는 아키텍처 접근법이다. 군집은 개별 로봇 자체의 능력뿐만 아니라 로봇 간 관계에서 유용한 지능이 형성되는 분산 사이버-물리 시스템(Distributed Cyber-Physical System)이 된다.

다중 로봇 및 플릿 지능(Multi-Robot and Fleet Intelligence)의 관점에서 군집 로보틱스는 기존 플릿 관리(Fleet Management)를 대체하기보다 보완한다. 전역 스케줄링(Global Scheduling), 결정론적 협력(Deterministic Coordination), 기업 시스템 통합(Enterprise Integration)이 중요할 때는 중앙집중식 플릿 시스템이 효과적이다. 반면 규모, 불확실한 환경, 분산 탐색, 복원력, 통신 제약으로 인해 국소 적응이 중요해질 때 군집 메커니즘이 유용해진다. 하이브리드 시스템(Hybrid System)은 두 접근법을 선택적으로 결합할 수 있다.

이러한 원리는 이후에 다루는 군집 알고리즘(Swarm Algorithm)의 개념적 기반을 제공한다. 플로킹(Flocking)은 국소적인 인력(Attraction), 정렬(Alignment), 분리(Separation)를 협력 이동으로 변환한다. 입자 군집 최적화(Particle Swarm Optimization, PSO)는 분산된 후보 해를 이용해 목적 공간(Objective Space)을 탐색하며, 개미 군집 최적화(Ant Colony Optimization, ACO)는 스티그머지에서 영감을 얻은 강화와 증발 메커니즘을 공식화한다. 분산 작업 할당, 대형 제어, 탐색, 통신, 고장 허용 역시 동일한 국소-전역(Local-to-Global) 철학을 실제 로봇 기능으로 확장한다.

궁극적으로 군집 지능(Swarm Intelligence)은 공학적 질문을 "중앙 제어기가 모든 로봇을 어떻게 명령해야 하는가?"에서 "어떠한 국소 정보, 상호작용 규칙, 피드백 메커니즘, 제약 조건이 전체 집단으로 하여금 요구되는 전역 행동을 생성하게 하는가?"로 전환한다. 이러한 관점의 변화가 자기조직화 로보틱스(Self-Organizing Robotics)의 핵심이며, 기존 다중 로봇 협력에서 확장 가능하고 적응적이며 복원력 있는 로봇 집단으로 발전하기 위한 개념적 연결고리를 제공한다.

## 07.02 Swarm Behavior Algorithms Flocking PSO ACO [w/Code]

![](images/image2.png){width="7.268055555555556in" height="7.268055555555556in"}

플로킹 알고리즘(Flocking Algorithm)은 중앙집중식 궤적 명령(Centralized Trajectory Command)이 아니라 단순한 국소 상호작용 규칙(Local Interaction Rule)을 통해 집단의 협력 이동을 구현한다. 고전적인 플로킹은 분리(Separation), 정렬(Alignment), 응집(Cohesion)을 기반으로 한다. 분리는 로봇 간 과도한 접근을 방지하고, 정렬은 유사한 속도나 방향을 유도하며, 응집은 로봇을 국소 집단의 중심 방향으로 끌어당긴다. 이 세 요소의 결합을 통해 분산된 의사결정만으로 조직적인 집단 이동이 형성된다.

각 로봇은 일반적으로 센싱 또는 통신 반경(Sensing or Communication Radius) 안에 있는 이웃 로봇만을 평가한다. 로봇 \\(i\\)의 최종 제어 행동은 분리, 정렬, 응집, 장애물 회피(Obstacle Avoidance), 임무 지향 이동(Mission-Directed Motion)의 가중 결합으로 해석할 수 있다. 이러한 가중치를 변경하면 집단 행동이 크게 달라진다. 응집이 지나치면 혼잡이 발생하고, 분리가 지나치면 군집이 분열될 수 있으며, 정렬이 약하면 불안정하거나 무질서한 움직임이 발생할 수 있다.

따라서 이웃 관계 정의(Neighborhood Definition)는 플로킹 방정식 자체만큼 중요하다. 거리 기반 이웃(Metric Neighborhood)은 지정된 물리적 거리 안에 있는 로봇을 포함하고, 위상 기반 이웃(Topological Neighborhood)은 일정한 수의 가장 가까운 로봇을 고려할 수 있다. 통신 연결성, 센싱 한계, 가림(Occlusion), 패킷 손실(Packet Loss), 로봇 동역학(Robot Dynamics)은 실제로 관측할 수 있는 이웃을 결정한다. 실용적인 플로킹 제어기는 이동 중 이웃 구성원이 지속적으로 변하는 상황에서도 정상적으로 동작해야 한다.

분리(Separation)는 일반적으로 로봇 간 거리가 감소할수록 크기가 증가하는 반발 벡터(Repulsive Vector)를 이용해 구현한다. 이를 통해 중앙 교통 제어기 없이도 분산형 충돌 회피 경향을 생성할 수 있다. 그러나 실제 로봇에는 유한한 제동 거리, 액추에이터 한계, 위치추정 불확실성(Localization Uncertainty), 통신 지연이 존재하므로 분리만으로 충돌 없는 운행을 보장할 수 없다. 따라서 안전이 중요한 시스템에서는 플로킹 규칙과 별도로 전용 충돌 회피(Collision Avoidance) 및 운동 제약(Motion Constraint)이 필요하다.

정렬(Alignment)은 이웃 로봇 사이의 속도 또는 진행 방향 차이를 감소시키는 것을 목적으로 한다. 로봇은 주변 이웃의 평균적인 움직임을 추정하고 자신의 속도를 해당 값에 가깝게 조정한다. 이러한 과정이 군집 전체에서 반복되면 공통된 방향으로 일관된 이동을 형성할 수 있다. 수렴 속도(Convergence Rate)는 상호작용 토폴로지, 갱신 주기, 제어기 게인(Controller Gain), 통신 품질, 개별 로봇의 동적 성능에 영향을 받는다.

응집(Cohesion)은 군집이 무한히 흩어지는 것을 방지하는 인력 요소(Attractive Component)를 제공한다. 로봇은 이웃 위치를 기반으로 국소 중심(Local Center)을 추정하고 분리 제약을 유지하면서 그 중심 방향으로 이동한다. 인력과 반발력 사이의 균형을 통해 원하는 군집 밀도를 유지할 수 있다. 실제 로봇에서는 임무 목표, 제한 구역, 통신 연결성 요구조건, 로봇 간 이질적인 성능 등을 반영하여 응집 규칙을 수정할 수 있다.

플로킹(Flocking)은 환경 목표(Environmental Objective)와 결합할 때 더욱 유용해진다. 목표 인력(Goal Attraction)은 군집을 목적지로 유도하고, 장애물 장(Obstacle Field)은 위험 요소 주변에서 대형을 변형시키며, 경계력(Boundary Force)은 로봇을 허용된 영역 내부에 유지한다. 국소 규칙에는 에너지 상태, 적재 상태, 지형 적합성, 통신 품질도 포함할 수 있다. 이를 통해 분산 행동을 유지하면서 실제 임무 수행에 필요한 운영 제약을 반영할 수 있다.

입자 군집 최적화(Particle Swarm Optimization, PSO)는 물리적인 플로킹을 직접 재현하기보다는 군집 원리를 수치 최적화(Numerical Optimization)에 적용한다. 각 입자(Particle)는 탐색 공간(Search Space)에서 하나의 후보 해(Candidate Solution)를 나타내며 위치와 속도를 유지한다. 반복적인 최적화 과정에서 입자는 자신이 발견한 최적 해와 다른 입자들이 발견한 성공적인 해에 대한 정보를 이용해 움직임을 수정하며, 전체 집단이 목적 함수(Objective Function)를 공동으로 탐색한다.

표준 입자 군집 최적화(PSO)의 갱신은 세 가지 영향을 결합한다. 관성(Inertia)은 입자의 이전 속도 일부를 유지하고, 인지 성분(Cognitive Component)은 자신의 개인 최적 위치(Personal Best Position)로 입자를 끌어당기며, 사회적 성분(Social Component)은 이웃 또는 전역 최적 위치(Global Best Position) 방향으로 입자를 유도한다. 확률 계수(Random Coefficient)는 확률적 탐색(Stochastic Exploration)을 제공하며, 이 요소들의 균형에 따라 광범위한 탐색 또는 유망 영역으로의 빠른 수렴 여부가 결정된다.

관성 가중치(Inertia Weight)는 특히 탐색과 활용의 절충(Exploration-Exploitation Trade-off)을 제어하는 데 유용하다. 높은 관성은 입자가 먼 영역까지 지속적으로 탐색하도록 유도할 수 있고, 낮은 관성은 국소적인 정밀 탐색과 수렴을 촉진한다. 인지 계수와 사회적 계수는 개별 경험과 집단 지식의 상대적 영향력을 결정한다. 잘못된 매개변수 설정은 진동, 조기 수렴(Premature Convergence), 과도한 분산 또는 느린 최적화를 발생시킬 수 있다.

입자 군집 최적화(PSO)는 의사결정을 최적화 변수(Optimization Variable)로 표현할 수 있는 로봇 문제에 적용할 수 있다. 대표적으로 매개변수 튜닝(Parameter Tuning), 대형 구성(Formation Configuration), 경로 관련 최적화, 자원 할당(Resource Allocation), 센서 배치(Sensor Placement), 임무 계획(Mission Planning) 등이 있다. 이러한 응용에서 입자는 반드시 물리적인 로봇을 의미하지 않는다. 입자는 최적화 프로세스 내부에만 존재하고, 최종적으로 얻은 해를 로봇 또는 플릿 제어기에 전달할 수도 있다.

분산 입자 군집 최적화(Distributed PSO)는 계산상의 입자 또는 후보 해를 여러 로봇에 분산시킬 수도 있다. 각 로봇은 국소 측정값을 이용하여 후보 의사결정을 평가하고 선택된 적합도 정보(Fitness Information)를 주변 로봇과 교환한다. 국소 최적 기반 PSO(Local-Best PSO)는 하나의 전역 공유 해에 대한 의존성을 줄여 분산 운용에 유리할 수 있지만, 수렴 특성은 통신 토폴로지와 군집 내부의 정보 전파 방식에 영향을 받는다.

개미 군집 최적화(Ant Colony Optimization, ACO)는 효율적인 경로를 탐색하는 개미의 간접 협력에서 영감을 얻은 방법이다. 인공 개미(Artificial Ant)는 후보 해를 구성하고 성공적인 해와 관련된 구성요소에 가상 페로몬(Virtual Pheromone)을 남긴다. 이후의 개미는 더 높은 페로몬 값을 가진 요소를 선택할 가능성이 커지면서 양의 피드백(Positive Feedback)이 형성된다. 동시에 페로몬 증발(Pheromone Evaporation)은 오래된 정보를 약화시켜 초기 선택이 탐색을 영구적으로 지배하는 것을 방지한다.

경로 계획(Path Planning) 문제에서 인공 개미는 페로몬 강도(Pheromone Intensity)와 거리 또는 예상 비용과 같은 휴리스틱 정보(Heuristic Information)의 영향을 받는 전이 확률(Transition Probability)에 따라 그래프 노드 사이를 이동한다. 후보 경로를 평가한 후 우수한 경로에 연결된 페로몬을 강화한다. 이러한 과정을 반복하면 높은 품질의 경로를 선택할 확률이 점진적으로 증가하면서도 다른 대체 경로를 계속 탐색할 수 있다.

페로몬 증발(Pheromone Evaporation)은 감쇠가 없는 강화가 군집을 초기의 차선 해(Suboptimal Solution)에 고정시킬 수 있기 때문에 개미 군집 최적화에서 필수적이다. 증발률(Evaporation Rate)은 과거 정보의 영향력이 얼마나 빠르게 감소하는지를 결정한다. 빠른 증발은 환경 변화에 대한 반응성을 향상시키지만 유용한 지식을 지나치게 빠르게 제거할 수 있으며, 느린 증발은 경험을 보존하지만 적응성을 감소시킬 수 있다. 따라서 효과적인 ACO는 기억, 탐색, 강화, 망각 사이의 균형을 필요로 한다.

개미 군집 최적화(ACO)는 모든 에이전트 사이의 지속적인 직접 협상보다 공유 정보 구조(Shared Information Structure)를 통해 협력이 이루어진다는 점에서 스티그머지(Stigmergy)와 자연스럽게 연결된다. 로봇 구현에서는 가상 페로몬을 그래프 간선(Graph Edge), 격자 셀(Grid Cell), 의미론적 지도 영역(Semantic Map Region), 분산 지도 구조(Distributed Map Structure)에 저장할 수 있다. 로봇은 성공적인 경로, 탐색 목표, 자원 위치, 작업 기회를 강화하면서 오래된 정보는 점차 감쇠하도록 만들 수 있다.

플로킹(Flocking), 입자 군집 최적화(PSO), 개미 군집 최적화(ACO)는 군집 지능(Swarm Intelligence)을 서로 다른 방식으로 구현한다. 플로킹은 주로 국소 기하학적 상호작용(Local Geometric Interaction)을 이용해 협력적인 물리적 움직임을 생성한다. PSO는 개별 경험과 집단 경험을 활용해 개체군 기반 탐색(Population-Based Search)을 수행하며, ACO는 확률적 의사결정과 스티그머지 기반 강화를 이용해 구성적 최적화(Constructive Optimization)를 수행한다. 따라서 세 알고리즘은 모두 군집 원리를 이용하지만 서로 교환 가능한 알고리즘으로 취급해서는 안 된다.

이러한 접근법은 서로 결합할 수도 있다. 플로킹은 실시간 로봇 움직임을 제어하고, PSO는 제어기 매개변수나 대형 구성을 최적화할 수 있다. ACO는 유망한 경로나 작업 순서를 결정하고, 국소 플로킹은 해당 경로를 따라 이동하면서 안전한 집단 움직임을 유지할 수 있다. 감독 계층(Supervisory Layer)은 모든 국소 상호작용을 직접 계산하지 않으면서 임무 경계와 안전 제약을 부여할 수 있으며, 이를 통해 대규모 로봇 집단에 적합한 하이브리드 아키텍처(Hybrid Architecture)를 구성할 수 있다.

각 알고리즘의 통신 요구조건(Communication Requirement)도 서로 다르다. 플로킹은 주변 로봇의 위치와 속도가 지속적으로 변하기 때문에 일반적으로 높은 빈도의 국소 상태 정보가 필요하다. 분산 PSO는 상대적으로 느린 최적화 시간 척도(Optimization Timescale)에서 후보 해의 품질과 최적 상태 정보를 교환한다. ACO는 지속적으로 유지되는 가상 페로몬 정보에 크게 의존할 수 있다. 시스템 설계자는 이러한 차이를 활용하여 지연, 대역폭, 신뢰성 요구조건에 따라 연산과 통신을 분할할 수 있다.

실제 로봇에는 이상적인 군집 시뮬레이션(Swarm Simulation)에서 단순화되는 다양한 조건이 존재한다. 센서 잡음(Sensor Noise), 위치추정 드리프트(Localization Drift), 통신 지연, 패킷 손실, 액추에이터 포화(Actuator Saturation), 이질적인 이동 성능, 배터리 제약, 비동기 갱신 주기(Asynchronous Update Rate)는 집단 동역학(Collective Dynamics)을 변화시킬 수 있다. 완벽한 동기 갱신 조건에서 안정적인 제어기도 실제 지연 환경에서는 진동하거나 군집을 분열시킬 수 있다. 따라서 알고리즘 평가는 정상적인 시뮬레이션뿐 아니라 통신 성능 저하와 실제 로봇의 물리적 제약까지 포함해야 한다.

확장성(Scalability) 역시 실험적으로 측정해야 한다. 분산 알고리즘으로 정의되어 있더라도 모든 로봇이 자신의 상태를 다른 모든 로봇에 전송하거나 하나의 중앙집중식 페로몬 데이터베이스(Centralized Pheromone Database)에 접근한다면 숨겨진 전역 병목현상(Global Bottleneck)이 발생할 수 있다. 효율적인 구현에서는 정보 교환을 관련 이웃으로 제한하고, 공유 지도를 분할하며, 국소 캐시(Local Cache)를 활용하고, 불필요한 전역 동기화(Global Synchronization)를 피해야 한다. 군집 규모가 증가함에 따라 계산 복잡도와 네트워크 트래픽을 함께 평가해야 한다.

성능 평가(Performance Evaluation)는 개별 로봇과 전체 집단의 결과를 모두 고려해야 한다. 플로킹은 충돌률, 속도 일치도(Velocity Agreement), 대형 응집도(Formation Cohesion), 분산도(Dispersion), 수렴 시간, 임무 진행률을 이용해 평가할 수 있다. PSO는 일반적으로 해의 품질(Solution Quality), 수렴 속도, 반복 실험에서의 강건성, 계산 비용을 평가한다. ACO는 경로 품질, 수렴 특성, 페로몬 다양성(Pheromone Diversity), 환경 변화 이후의 적응성, 통신 오버헤드를 평가할 수 있다.

모든 문제에 보편적으로 최적인 단일 군집 알고리즘은 존재하지 않는다. 플로킹은 협력 이동과 국소 반응성이 중요한 문제에 적합하다. PSO는 문제를 연속적인 최적화 공간 또는 매개변수화된 최적화 공간으로 표현할 수 있을 때 유용하다. ACO는 그래프 기반 경로 탐색(Graph-Based Routing), 순서 결정(Sequencing), 지속적인 스티그머지 정보가 유용한 문제에 특히 적합하다. 따라서 단순한 생물학적 유사성이 아니라 실제 응용 문제의 구조에 따라 알고리즘을 선택해야 한다.

산업용 군집 로보틱스(Industrial Swarm Robotics)에서 이러한 알고리즘은 더 큰 자율 시스템 아키텍처(Autonomy Architecture)를 구성하는 요소로 이해해야 한다. 안전 모니터(Safety Monitor), 위치추정(Localization), 통신 관리, 임무 감독(Mission Supervision), 고장 탐지(Fault Detection), 충전 로직(Charging Logic), 플릿 인터페이스(Fleet Interface)는 여전히 필요하다. 군집 알고리즘은 분산 협력과 최적화 메커니즘을 제공하고 상위 시스템은 운영 목표와 제약을 정의한다. 이러한 분리를 통해 창발적 행동과 예측 가능한 산업 운영 거버넌스를 함께 구현할 수 있다.

플로킹(Flocking), PSO, ACO는 궁극적으로 비교적 단순한 국소 규칙이 어떻게 정교한 개체군 수준 행동(Population-Level Behavior)을 생성할 수 있는지를 보여준다. 플로킹은 이웃 상호작용을 일관된 집단 이동으로 변환하고, PSO는 분산된 경험을 집단 최적화(Collective Optimization)로 변환하며, ACO는 간접적인 환경 정보를 적응형 탐색(Adaptive Search)으로 변환한다. 이들은 함께 분산 작업 할당(Distributed Task Assignment), 대형 형성(Formation), 탐색(Exploration), 경로 계획(Routing), 대규모 군집 협력(Large-Scale Swarm Coordination)을 구현하기 위한 핵심 알고리즘 패턴을 제공한다.

## 07.03 Distributed Task Assignment in Swarms [w/Code]

![](images/image3.png){width="7.268055555555556in" height="7.268055555555556in"}

로봇 군집(Robot Swarm)에서 분산 작업 할당(Distributed Task Assignment)은 지속적으로 사용 가능한 중앙 디스패처(Central Dispatcher)에 의존하지 않고 다수의 자율 로봇이 작업을 선택하고, 정보를 교환하며, 작업을 수행하는 방법을 결정한다. 하나의 전역 할당 행렬(Global Assignment Matrix)을 유지하는 대신 각 로봇은 국소 관측(Local Observation), 이웃 메시지, 작업 긴급도, 능력, 거리, 에너지 상태, 현재 작업량을 기반으로 의사결정을 수행한다. 전체 군집의 반복적인 국소 의사결정과 상호작용을 통해 집단적인 작업 할당이 형성된다.

이러한 접근법은 완전한 전역 정보(Global Knowledge)를 가정하지 않는다는 점에서 기존의 중앙집중식 다중 로봇 작업 할당(Centralized Multi-Robot Task Allocation)과 다르다. 하나의 로봇은 자신이 국소적으로 발견하거나 주변 로봇으로부터 전달받은 작업만 알고 있을 수 있으며, 멀리 떨어진 군집 영역은 서로 다른 정보를 유지할 수 있다. 따라서 작업 할당 메커니즘은 부분 정보, 비동기 갱신(Asynchronous Update), 통신 지연, 일시적인 의견 불일치를 허용하면서도 전체 군집이 효과적인 전역 작업 커버리지(Global Task Coverage)를 달성하도록 유도해야 한다.

분산 작업 할당 문제는 로봇 집합 \\(R=\\{r_1,\\ldots,r_n\\}\\)과 작업 집합 \\(T=\\{t_1,\\ldots,t_m\\}\\)으로 표현할 수 있다. 각 로봇은 이동 거리, 실행 시간, 에너지 소비, 작업 우선순위, 요구 능력, 예상 보상 등의 요소를 사용하여 후보 작업에 대한 국소 효용(Local Utility) 또는 비용(Cost)을 추정한다. 작업 할당은 이러한 국소 정보 제약(Local Information Constraint) 아래에서 집단 효용을 최대화하거나 전체 운영 비용을 최소화하는 것을 목표로 한다.

국소 효용 함수(Local Utility Function)는 임무 목표를 개별 로봇의 의사결정으로 변환하기 때문에 매우 중요하다. 가까운 작업은 이동 비용이 낮지만 전략적 가치가 제한적일 수 있고, 멀리 떨어진 긴급 작업은 더 높은 우선순위를 가질 수 있다. 따라서 효용은 정규화된 여러 요소를 설정 가능한 가중치로 결합할 수 있다. 이기종 군집(Heterogeneous Swarm)에서는 로봇마다 적재 능력, 센서, 이동성, 매니퓰레이터, 운용 시간, 환경 접근성이 다를 수 있으므로 효용 계산에 앞서 실행 가능성(Feasibility)을 확인해야 한다.

간단한 분산 전략 중 하나는 임계값 기반 반응(Threshold-Based Response)이다. 각 로봇은 작업 유형과 관련된 반응 임계값(Response Threshold)을 유지하며, 인식된 작업 자극(Task Stimulus)이 해당 임계값을 초과할수록 작업을 수락할 가능성이 높아진다. 특정 작업에 대해 낮은 임계값을 가진 로봇은 자연스럽게 전문화되고, 작업 수요가 증가하면 추가 로봇이 투입된다. 이를 통해 중앙 제어기가 모든 로봇을 직접 할당하지 않고도 유연한 분업(Division of Labor)을 형성할 수 있다.

임계값 메커니즘(Threshold Mechanism)은 시간에 따라 적응할 수도 있다. 특정 작업 유형을 성공적으로 수행하면 해당 로봇의 관련 임계값을 낮춰 이후 유사한 작업을 수락할 가능성을 높일 수 있다. 반대로 작업에 참여하지 않는 경우 임계값을 점진적으로 증가시키거나 정상화할 수 있다. 이러한 적응은 창발적 전문화(Emergent Specialization)를 형성할 수 있지만, 지나친 강화는 역할을 경직시킬 수 있다. 따라서 작업량, 로봇 가용성, 환경 조건이 변할 때 유연성을 유지하는 메커니즘이 필요하다.

시장 기반 분산 할당(Market-Inspired Distributed Assignment)은 또 다른 접근법을 제공한다. 로봇은 공지된 작업을 수행하는 비용 또는 효용을 나타내는 입찰값(Bid)을 계산하고, 주변 로봇은 이를 비교하여 승자를 선택한다. 경매(Auction)는 중앙 경매자 없이 국소적으로 수행될 수 있으며 정보는 피어 통신(Peer Communication)을 통해 전파된다. 반복적인 입찰을 이용하면 새롭게 발생하는 작업을 할당하면서 더 적합한 후보가 나타날 경우 기존 할당을 재검토할 수 있다.

합의 기반 할당(Consensus-Based Allocation)은 로봇이 국소 작업 묶음(Local Task Bundle)을 구성하고 선호하는 할당 정보를 서로 교환하도록 함으로써 이러한 개념을 확장한다. 반복적인 통신을 통해 충돌하는 작업 소유권을 해결하고 주변 로봇들이 서로 호환되는 할당 상태로 수렴할 수 있다. 합의(Consensus)를 위해 모든 로봇이 서로 직접 통신할 필요는 없으며, 연결된 통신 그래프(Communication Graph)를 따라 연속적인 이웃 정보 교환을 통해 정보가 전파될 수 있다.

군집 작업 할당(Swarm Task Assignment)은 스티그머지 메커니즘(Stigmergic Mechanism)을 사용할 수도 있다. 작업, 영역 또는 자원에 수요, 긴급도, 혼잡도, 최근 서비스 활동을 나타내는 가상 마커(Virtual Marker)를 부여할 수 있다. 로봇은 이러한 마커를 관찰하고 국소 값에 따라 행동을 선택한다. 작업을 성공적으로 수행하면 작업 수요 마커를 감소시키고, 처리되지 않은 작업은 더 강한 유인력을 축적하도록 할 수 있다. 이를 통해 공유 환경 또는 디지털 지도(Digital Map)가 분산 협력에 직접 참여하게 된다.

가상 페로몬 메커니즘(Virtual Pheromone Mechanism)은 탐색, 검사, 청소, 감시, 자원 수집과 같은 공간 기반 작업에 특히 유용하다. 로봇은 수요가 높은 영역으로 유인되는 동시에 최근 작업이 완료된 영역에서는 멀어지도록 설정할 수 있다. 마커 증발(Marker Evaporation)은 오래된 정보를 제거하여 새로운 작업이 발생하거나 우선순위가 변경될 때 군집이 적응할 수 있도록 한다. 증발 속도가 지나치게 느리면 오래된 할당 정보가 유지되고, 지나치게 빠르면 불안정한 작업 전환이 발생할 수 있다.

분산 할당에서는 중복 선택(Duplicate Selection)을 명시적으로 관리해야 한다. 여러 로봇이 동일한 고가치 작업을 독립적으로 발견하면 모두 해당 작업을 수행하려 하여 자원이 낭비될 수 있다. 국소 예약 메시지(Local Reservation Message), 임시 소유권 토큰(Temporary Ownership Token), 승자 공지(Winner Announcement), 커밋 타이머(Commitment Timer), 작업 상태 마커(Task-State Marker) 등을 사용하여 중복을 줄일 수 있다. 여러 로봇이 필요한 작업에서는 이러한 메커니즘을 이용해 필요한 팀 규모가 확보될 때까지 로봇을 모집할 수도 있다.

커밋(Commitment)은 효용을 지속적으로 재계산함으로써 로봇이 반복적으로 작업을 변경하는 현상을 방지하기 때문에 중요하다. 로봇이 조금 더 좋은 기회가 나타날 때마다 현재 작업을 포기하면 진동(Oscillation)이 발생하고 실제 작업 수행량이 감소할 수 있다. 히스테리시스(Hysteresis), 최소 커밋 기간(Minimum Commitment Period), 전환 페널티(Switching Penalty), 진행률 기반 효용(Progress-Aware Utility)을 이용하여 의사결정을 안정화할 수 있다. 동시에 불필요하거나 실행 불가능해진 작업을 포기할 수 있도록 안정성과 반응성 사이의 균형이 필요하다.

동적 작업 발생(Dynamic Task Arrival)은 실제 군집 운용의 핵심적인 특징이다. 새로운 검사 요청, 감지된 위험, 운송 작업, 탐색 목표 또는 고장이 로봇이 이미 작업을 수행하는 동안 발생할 수 있다. 분산 알고리즘은 전체 군집의 스케줄을 다시 계산하기보다 새로운 작업을 점진적으로 반영해야 한다. 국소 공지(Local Announcement)와 이웃 전파(Neighborhood Propagation)를 사용하면 긴급 정보를 확산시키면서 새로운 작업의 영향을 받지 않는 로봇은 기존 임무를 계속 수행할 수 있다.

작업 우선순위(Task Priority)는 추가적인 복잡성을 발생시킨다. 긴급 작업은 일반 작업보다 우선 수행되어야 할 수 있고, 낮은 우선순위 작업은 주변의 유휴 로봇을 기다릴 수 있다. 따라서 우선순위는 효용, 입찰, 모집, 작업 전환 규칙에 영향을 주어야 한다. 그러나 높은 우선순위 이벤트가 빈번하게 발생하는 환경에서 지나치게 공격적인 선점(Preemption)은 군집을 불안정하게 만들 수 있다. 우선순위 에이징(Priority Aging), 제한된 선점(Bounded Preemption), 임무별 예약 정책을 이용하여 반응성과 작업 완료 안정성을 함께 유지할 수 있다.

에너지 인식(Energy Awareness)도 매우 중요하다. 가장 높은 작업 효용을 가진 로봇이라도 남은 배터리가 이동, 작업 수행, 충전소까지의 안전한 복귀를 지원하지 못한다면 최적의 선택이 아닐 수 있다. 분산 효용 계산에는 충전 상태(State of Charge), 예상 에너지 소비, 충전기까지의 거리, 충전 혼잡도를 포함할 수 있다. 에너지 임계값에 접근하는 로봇은 입찰 활동을 줄이거나 충전(Charging)을 높은 우선순위의 내부 작업으로 일시적으로 분류할 수 있다.

통신 토폴로지(Communication Topology)는 작업 할당 품질에 큰 영향을 미친다. 밀집된 정보 교환은 상황 인식을 향상시키지만 대역폭과 연산 요구량을 증가시킨다. 희소한 국소 통신(Sparse Local Communication)은 확장성이 우수하지만 작업 및 할당 정보의 전파를 느리게 만든다. 가십(Gossip), 국소 방송(Local Broadcast), 이웃 테이블(Neighbor Table), 주기적 요약(Periodic Summary)을 이용하면 전역 동기화 없이 관련 상태를 전파할 수 있다. 적절한 토폴로지는 군집 규모, 로봇 밀도, 작업 변화 특성, 네트워크 신뢰성에 따라 결정된다.

일시적인 통신 분할(Communication Partition)이 발생하더라도 전체 군집이 중단되어서는 안 된다. 연결이 끊어진 하위 그룹의 로봇은 자신들이 이용할 수 있는 정보를 기반으로 국소적으로 관측 가능한 작업을 계속 할당해야 한다. 연결이 복구되면 타임스탬프(Timestamp), 작업 버전(Task Version), 소유권 리스(Ownership Lease), 결정론적 충돌 해결 규칙(Deterministic Conflict Rule)을 이용해 할당 상태를 조정할 수 있다. 이러한 분할 허용 행동(Partition-Tolerant Behavior)은 대규모 또는 통신 제약 환경에서 분산 아키텍처가 제공하는 중요한 장점이다.

로봇 고장(Robot Failure)에도 유사한 재할당 메커니즘(Reassignment Mechanism)이 필요하다. 로봇이 작업 진행 상황을 더 이상 보고하지 않으면 해당 작업은 일정 시간이 지난 후 다른 로봇이 수행할 수 있어야 한다. 하트비트(Heartbeat), 리스 만료(Lease Expiration), 진행 시간 초과(Progress Timeout), 국소 관측을 이용하여 중단된 작업을 탐지할 수 있다. 통신 장애만으로 즉시 중복 작업이 발생하지 않도록 작업 소유권은 영구적이기보다 시간 제한 방식으로 처리할 수 있다. 이를 통해 전역 재계획 없이 미완료 작업을 재분배할 수 있다.

이기종 군집(Heterogeneous Swarm)에서는 능력 인식 할당(Capability-Aware Assignment)이 필요하다. 공중 로봇은 높은 구조물을 검사하고, 지상 로봇은 화물을 운반하며, 열화상 카메라나 매니퓰레이터를 탑재한 로봇은 전문 작업을 수행할 수 있다. 따라서 작업 설명에는 요구 능력(Capability Requirement)이 포함되어야 하고 로봇은 간결한 능력 프로파일(Capability Profile)을 제공해야 한다. 실행 가능한 후보 사이에서만 작업을 할당하며, 협력 작업에서는 상호 보완적인 로봇을 모집하여 임시 임무 팀(Temporary Mission Team)을 구성할 수 있다.

공간 협력(Spatial Coordination)과 작업 할당은 밀접하게 결합되어 있다. 이론적으로 가장 좋은 작업을 선택하더라도 많은 로봇이 동일한 좁은 통로나 작업 구역을 통과하려 한다면 효율적이지 않을 수 있다. 할당 비용에는 예상 혼잡도, 이동 충돌, 지역별 로봇 밀도를 포함할 수 있다. 따라서 국소 교통 정보(Local Traffic Information)를 입찰 또는 효용에 반영하여 작업량뿐 아니라 환경 내부의 물리적 이동도 분산시킬 수 있다.

분산 작업 할당은 저수준 군집 이동(Low-Level Swarm Motion)과 서로 다른 시간 척도(Timescale)에서 동작한다. 작업 선택은 몇 초마다 또는 중요한 이벤트가 발생할 때 갱신할 수 있지만, 충돌 회피와 플로킹(Flocking)은 훨씬 높은 주기로 실행될 수 있다. 이러한 계층을 분리하면 작업 할당 메시지가 시간에 민감한 운동 제어(Time-Critical Motion Control)의 일부가 되는 것을 방지할 수 있다. 로봇은 분산 할당을 통해 작업을 선택하고, 국소 내비게이션 또는 플로킹 제어기를 통해 해당 작업 위치까지 안전하게 이동할 수 있다.

산업용 구현(Industrial Implementation)에서는 군집 작업 할당과 감독 제약(Supervisory Constraint)을 결합할 수 있다. 플릿 또는 임무 계층(Fleet or Mission Layer)은 작업 유형, 안전 구역, 마감시간, 자원 제한, 금지된 할당 등을 정의하면서 개별 작업 선택은 분산 방식으로 유지할 수 있다. 따라서 감독 시스템은 모든 로봇에 지속적으로 작업을 할당하는 대신 허용 가능한 의사결정 공간(Admissible Decision Space)을 설정한다. 이러한 하이브리드 구조(Hybrid Structure)는 확장성과 국소 복원력을 유지하면서 운영 거버넌스(Operational Governance)를 제공한다.

성능(Performance)은 전체 집단 수준에서 평가해야 한다. 관련 지표에는 작업 완료율(Task Completion Rate), 평균 대기 시간(Average Waiting Time), 이동 거리, 에너지 소비, 작업량 균형(Workload Balance), 할당 수렴 시간(Assignment Convergence Time), 통신 오버헤드, 중복 실행(Duplicate Execution), 작업 전환 빈도(Switching Frequency), 고장 이후 복구 성능 등이 포함된다. 반복적인 국소 최적화로 특정 로봇에 작업이 과도하게 집중되어 배터리나 기계 부품의 열화가 가속될 수 있으므로 공정성(Fairness)도 중요할 수 있다.

확장성 시험(Scalability Testing)에서는 로봇 수와 작업 발생률(Task Arrival Rate)을 함께 증가시켜야 한다. 20대의 로봇에서 정상적으로 동작하는 알고리즘이라도 수백 대 규모에서는 메시지 폭주(Message Storm), 느린 수렴, 과도한 경쟁(Contention), 불안정한 작업 전환이 발생할 수 있다. 따라서 실제 배치 전에 통신 손실, 메시지 지연, 로봇 고장, 이기종 능력, 변화하는 작업 밀도, 공간적 병목현상(Spatial Bottleneck)을 시뮬레이션으로 평가해야 한다. 대규모에서 나타나는 행동 자체가 알고리즘 성능의 일부이다.

궁극적으로 분산 작업 할당(Distributed Task Assignment)은 국소적인 추정, 피어 상호작용(Peer Interaction), 환경 신호를 집단 수준의 분업(Population-Level Division of Labor)으로 변환한다. 임계값 기반 반응은 단순한 자기조직화 전문화를 제공하고, 경매와 합의는 명시적인 분산 경쟁과 협의를 제공하며, 스티그머지 메커니즘은 공유 작업 신호를 통해 협력을 수행한다. 여기에 커밋, 고장 복구, 에너지 인식, 능력 제약을 결합하면 하나의 중앙 의사결정 지점에 의존하지 않고도 군집 전체가 변화하는 작업을 적응적으로 할당할 수 있다.

## 07.04 Swarm Formation and Shape Control [w/Code]

![](images/image4.png){width="7.268055555555556in" height="7.268055555555556in"}

군집 대형 및 형상 제어(Swarm Formation and Shape Control)는 분산 의사결정(Decentralized Decision Making)을 유지하면서 다수의 로봇이 원하는 공간 패턴(Spatial Pattern)으로 스스로 조직되도록 한다. 모든 로봇이 사전에 정의된 전역 궤적(Global Trajectory)을 따르도록 명령하는 대신, 국소 위치, 거리, 방향, 이웃 관계를 통해 대형 행동(Formation Behavior)을 생성한다. 목표는 군집이 이동하고 환경 변화에 적응하면서도 유용한 집단 기하 구조(Collective Geometry)를 유지하는 것이다.

대형(Formation)은 절대 좌표(Absolute Coordinate)가 아니라 상대적 관계(Relative Relationship)를 통해 표현할 수 있다. 로봇은 특정 이웃과 원하는 거리를 유지하거나, 각도 관계를 보존하거나, 기하학적 경계상의 위치를 점유하거나, 특정 영역 내부에서 정해진 밀도를 유지하도록 요구될 수 있다. 이러한 상대적 표현은 각 로봇이 전체 군집의 완전한 정보를 필요로 하지 않고 국소적으로 측정 가능한 정보만으로 제어 행동을 계산할 수 있기 때문에 분산 제어(Distributed Control)에 적합하다.

일반적인 군집 대형에는 선형(Line), 종대(Column), 원형(Circle), 격자(Lattice), 쐐기형(Wedge), 링(Ring), 그리드(Grid), 동적 변형 형상(Dynamically Deformable Shape) 등이 있다. 서로 다른 기하 구조는 서로 다른 운영 목적을 지원한다. 선형은 통로 검사에 적합하고, 그리드는 체계적인 영역 커버리지에 활용할 수 있으며, 링은 목표물을 둘러싸는 데 사용할 수 있고, 쐐기형은 협력 이동을 지원할 수 있다. 따라서 형상 선택은 센싱 범위, 이동성, 통신, 안전, 임무 요구조건을 반영해야 한다.

거리 기반 대형 제어(Distance-Based Formation Control)는 통신 또는 센싱 그래프에서 원하는 로봇 간 거리(Inter-Robot Distance)를 정의한다. 각 로봇은 측정된 거리와 목표 값을 비교하고 오차를 감소시키는 방향으로 보정 움직임을 생성한다. 주변 로봇들이 동일한 동작을 동시에 수행하면 전체 대형이 목표 기하 구조로 수렴할 수 있다. 거리 정보는 위치추정(Localization), 거리 측정(Ranging), 상대 인식(Relative Perception)을 통해 직접 추정할 수 있으므로 이러한 접근법은 실용성이 높다.

퍼텐셜 필드 방법(Potential-Field Method)은 또 다른 직관적인 메커니즘을 제공한다. 주변 로봇이 너무 멀리 떨어지면 인력(Attractive Force)을 생성하고 너무 가까워지면 반발력(Repulsive Force)을 생성한다. 이러한 가상 힘(Virtual Force)의 평형을 통해 원하는 간격을 형성한다. 추가적인 필드를 이용하여 장애물, 임무 목표, 제한 구역, 환경 경계를 표현할 수 있으므로 대형 유지와 환경 상호작용을 하나의 분산 제어 프레임워크(Distributed Control Framework)에 통합할 수 있다.

합의 기반 대형 제어(Consensus-Based Formation Control)는 주변 로봇 간 정보 교환을 이용하여 위치 오프셋(Position Offset), 속도, 진행 방향, 대형 상태와 같은 변수의 차이를 줄인다. 각 로봇은 주변 로봇과의 차이에 따라 자신의 상태를 반복적으로 조정한다. 상호작용 그래프(Interaction Graph)가 적절한 연결 조건을 만족하면 이러한 국소 갱신을 통해 일관된 전역 움직임(Global Motion)을 생성할 수 있다. 따라서 합의는 지속적인 중앙집중식 협력 없이 대형 행동을 동기화할 수 있다.

리더-팔로워 제어(Leader-Follower Control)는 대형 행동에 제한적인 계층 구조(Hierarchy)를 도입한다. 하나 이상의 리더 로봇(Leader Robot)이 이동 기준을 정의하고, 팔로워(Follower)는 리더 또는 주변 팔로워와 사전에 정의된 상대적 관계를 유지한다. 이를 통해 전역 유도가 단순해지지만 리더의 가용성에 대한 의존성이 발생할 수 있다. 다중 리더(Multi-Leader), 가상 리더(Virtual Leader), 리더 선출(Leader Election) 메커니즘을 사용하면 집단 이동의 명확한 기준을 유지하면서 이러한 취약성을 줄일 수 있다.

무리더 대형(Leaderless Formation)은 지속적인 중앙 기준을 제거하고 분산 상호작용을 통해 이동 방향을 결정한다. 임무 방향은 합의, 환경 기울기(Environmental Gradient), 임시 국소 리더, 공유 목표 정보 등을 통해 형성될 수 있다. 특정 로봇의 고장이 군집의 핵심 이동 기준을 제거하지 않기 때문에 이러한 대형은 향상된 복원력(Resilience)을 제공할 수 있다. 그러나 협력적인 병진 이동(Translation)과 회전(Rotation)을 구현하려면 참여 로봇 간에 더 강력한 합의 메커니즘이 필요할 수 있다.

그래프 이론(Graph Theory)은 대형 구조를 표현하기 위한 유용한 수학적 방법을 제공한다. 로봇은 정점(Vertex)으로 표현되고 관련된 상호작용 관계는 간선(Edge)으로 표현된다. 그래프는 어떤 로봇이 정보를 교환하거나 상대적 기하 구조에 대한 제약을 공유하는지를 결정한다. 연결성(Connectivity)은 매우 중요하며, 상호작용 그래프가 분리되면 군집이 서로 독립적인 하위 그룹으로 나뉠 수 있다. 따라서 대형 제어에서는 기하학적 형상뿐 아니라 통신 연결성 유지도 함께 고려해야 한다.

강성(Rigidity) 역시 중요한 개념이다. 대형이 강성을 가진다는 것은 지정된 로봇 간 거리를 변경하지 않고서는 기하학적 형상을 연속적으로 변형할 수 없다는 것을 의미한다. 강성 이론(Rigidity Theory)은 선택된 거리 제약이 목표 기하 구조를 유지하기에 충분한지를 판단하는 데 도움을 준다. 제약이 너무 적으면 원하지 않는 변형이 발생할 수 있고, 지나치게 많으면 통신 및 제어 복잡도가 증가한다. 실제 설계에서는 불필요한 결합을 줄이면서 안정성을 확보할 수 있는 적절한 구조가 필요하다.

형상 제어(Shape Control)는 고정된 상대 위치를 유지하는 것을 넘어 대형 제어를 확장한다. 군집은 상위 수준의 기하학적 목표를 유지하면서 확대, 축소, 회전, 분할, 병합하거나 장애물 주변에서 변형되어야 할 수 있다. 예를 들어 원형 대형은 좁은 영역을 통과할 때 일시적으로 타원형으로 변형되고 이후 원래 형상을 복원할 수 있다. 이를 위해서는 목표 대형 자체를 동적 제어 변수(Dynamic Control Variable)로 취급해야 한다.

형상 표현(Shape Representation)에는 명시적 목표 위치(Explicit Target Position), 기하학적 기본 형상(Geometric Primitive), 밀도장(Density Field), 부호 거리 함수(Signed-Distance Function), 가상 구조(Virtual Structure), 암시적 경계(Implicit Boundary) 등을 사용할 수 있다. 명시적 위치 방식은 소규모 대형에서는 편리하지만 규모가 커질수록 제약이 증가할 수 있다. 필드 기반 표현(Field-Based Representation)은 원하는 집단 형상을 만족하는 범위에서 개별 로봇이 적절한 위치를 자유롭게 점유할 수 있어 로봇 고장, 신규 참여 또는 위치 교환 상황에서 더 높은 유연성을 제공한다.

가상 구조 방법(Virtual-Structure Method)은 전체 대형을 하나의 기하학적 객체처럼 취급한다. 원하는 로봇 위치를 가상의 기준 좌표계(Virtual Reference Frame)에 상대적으로 정의하고 해당 좌표계를 병진, 회전 또는 스케일링하여 전체 대형을 이동시킨다. 이를 통해 정확한 형상을 생성할 수 있지만 완전히 중앙집중식 가상 구조는 군집 자율성을 감소시킬 수 있다. 분산 구현에서는 국소 통신과 합의를 통해 가상 기준을 복제하거나 추정할 수 있다.

행동 기반 형상 제어(Behavior-Based Shape Control)는 분리, 응집, 정렬, 목표 인력, 장애물 회피, 경계 추종(Boundary Following)과 같은 여러 국소 행동을 결합한다. 이러한 행동을 가중 결합하면 군집은 환경 변화에 반응하면서 대략적인 형상을 유지할 수 있다. 강체 기하 제어기(Rigid Geometric Controller)와 달리 행동 기반 방식은 외란과 구성원 변화에 유연하게 대응할 수 있지만 기하학적 정밀성에 대한 보장은 상대적으로 낮을 수 있다.

대형 크기 조절(Formation Resizing)은 환경의 공간 조건이 변할 때 필요하다. 좁은 통로에 접근하는 로봇들은 횡방향 간격을 줄이고 넓은 그리드 형태에서 종대 형태로 변경한 뒤 통과 후 원래 배열을 복원할 수 있다. 대형 전환 제어(Transition Control)는 갑작스러운 목표 변경으로 인해 경로가 교차하거나 혼잡이 발생하지 않도록 해야 한다. 부드러운 보간(Smooth Interpolation), 단계적 전환, 국소 재구성(Local Reconfiguration), 임시 역할 재할당을 통해 형상 변환 과정의 불안정성을 줄일 수 있다.

장애물 회피(Obstacle Avoidance)는 개별적인 회피 행동이 대형의 일관성을 무너뜨릴 수 있기 때문에 신중하게 통합해야 한다. 한 로봇이 독립적으로 장애물을 우회하면 통신 링크가 끊어지거나 큰 간격 오차가 발생할 수 있다. 대형 인식형 회피(Formation-Aware Avoidance)는 장애물 위험과 이웃 관계를 함께 고려한다. 군집 전체가 함께 변형되거나 장애물의 서로 다른 방향으로 우회하거나, 연결성과 안전을 유지하면서 일시적으로 형상 제약을 완화할 수 있다.

충돌 회피(Collision Avoidance)는 정상적인 대형 정확도보다 높은 안전 우선순위를 가져야 한다. 위치추정 오차, 예상하지 못한 장애물, 동적 객체가 존재할 때 목표 기하 구조가 로봇을 위험한 상태로 강제해서는 안 된다. 안전 계층(Safety Layer)은 최소 분리 거리, 속도 제한, 비상 제동(Emergency Braking), 충돌 없는 제어 제약(Collision-Free Control Constraint)을 적용할 수 있다. 외란이 사라진 후 대형 제어기는 점진적으로 원하는 기하 구조를 복원할 수 있다.

통신 지연(Communication Delay)과 패킷 손실(Packet Loss)은 대형 안정성(Formation Stability)에 큰 영향을 줄 수 있다. 네트워크를 통해 수신한 이웃 로봇의 위치나 속도 정보는 제어기가 사용할 때 이미 오래된 정보일 수 있다. 예측(Prediction), 타임스탬프(Timestamping), 제한 지연 설계(Bounded-Delay Design), 국소 센싱, 비동기 알고리즘(Asynchronous Algorithm)을 이용하면 완벽하게 동기화된 통신에 대한 의존성을 줄일 수 있다. 강건한 대형 제어기는 일부 통신 링크의 신뢰성이 저하되더라도 전체 대형이 붕괴하기보다 점진적으로 성능이 저하되어야 한다.

위치추정 불확실성(Localization Uncertainty)도 유사한 문제를 발생시킨다. 절대 위성항법시스템(GNSS)이나 지도 기반 위치추정(Map-Based Localization)은 특히 실내 또는 신호가 차단된 환경에서 항상 사용할 수 있거나 충분히 정밀하지 않을 수 있다. 카메라, 라이다(LiDAR), 거리 측정 무선통신(Ranging Radio), 이웃 관측을 이용한 상대 위치추정(Relative Localization)이 대형 제어를 지원할 수 있다. 하이브리드 방식은 전역 앵커(Global Anchor)와 정밀한 국소 상대 측정을 결합하여 전체 내비게이션과 내부 대형 기하 구조의 일관성을 유지할 수 있다.

이기종 군집(Heterogeneous Swarm)은 서로 다른 로봇 크기, 속도, 회전 반경, 센싱 범위, 이동 제약을 고려하는 대형 규칙이 필요하다. 공중 로봇과 지상 로봇은 동일한 기하학적 관계를 유지할 수 없는 경우가 있다. 따라서 목표 간격과 역할 할당(Role Assignment)은 로봇 유형에 따라 달라질 수 있다. 능력 인식형 대형(Capability-Aware Formation)은 특수 센서를 유리한 위치에 배치하고, 더 빠르거나 기동성이 높은 로봇을 동적으로 높은 요구가 발생하는 위치에 배치할 수 있다.

대규모 군집에서는 구성원 변화(Membership Change)를 피할 수 없다. 로봇은 새롭게 참여하거나, 이탈하거나, 고장 나거나, 충전을 수행하거나, 일시적으로 사용할 수 없는 상태가 될 수 있다. 확장 가능한 대형은 전체 구조를 완전히 재구성하지 않고도 이러한 변화에 대응해야 한다. 국소 빈자리 보충(Local Vacancy Filling), 이웃 재할당, 그래프 복구(Graph Repair), 밀도 재분배(Density Redistribution), 역할 이전(Role Transfer)을 통해 개체 수가 변하더라도 전체 형상을 유지할 수 있다. 이러한 특성은 고장 허용(Fault Tolerance)과 운영 연속성(Operational Continuity)에 직접 기여한다.

대형 분할 및 병합(Formation Splitting and Merging)은 여러 지역을 다루는 임무에서 중요하다. 하나의 군집을 여러 하위 그룹으로 분리하여 서로 다른 지역을 검사한 후 다시 하나의 큰 대형으로 결합할 수 있다. 분산 식별자(Distributed Identifier), 임시 그룹 목표, 경계 조건, 랑데부 규칙(Rendezvous Rule)을 이용해 이러한 전환을 조정할 수 있다. 제어 시스템은 그룹이 분리되거나 다시 접근할 때 모호한 구성원 관계와 충돌하는 인력(Attraction Force)이 발생하지 않도록 해야 한다.

에너지 상태(Energy State) 역시 대형의 기하 구조에 영향을 줄 수 있다. 배터리가 부족한 로봇은 충전을 위해 쉽게 이탈할 수 있는 주변부 위치로 이동하고, 완전히 충전된 로봇이 임무를 중단하지 않으면서 해당 위치를 대체할 수 있다. 센싱 임무에서는 에너지가 충분한 로봇을 더 많은 이동이나 통신 책임이 필요한 위치에 배치할 수도 있다. 따라서 대형 제어는 분산 작업 할당(Distributed Task Assignment) 및 에너지 인식형 플릿 관리(Energy-Aware Fleet Management)와 상호작용할 수 있다.

대형 제어기(Formation Controller)와 내비게이션 시스템(Navigation System)은 서로 협력하는 계층으로 동작해야 한다. 임무 계획(Mission Planning)은 군집이 어디로 이동할지를 결정하고, 대형 제어는 원하는 집단 기하 구조를 결정하며, 국소 운동 제어(Local Motion Control)는 실행 가능한 로봇 궤적을 생성한다. 필요한 경우 충돌 회피와 안전 제약이 정상 명령보다 우선할 수 있다. 이러한 계층형 아키텍처(Layered Architecture)는 기하학적 목표와 저수준 차량 동역학(Low-Level Vehicle Dynamics)이 혼동되는 것을 방지한다.

성능 평가(Performance Evaluation)는 목표 형상과 시각적으로 얼마나 유사한지만 측정해서는 안 된다. 유용한 지표에는 대형 오차(Formation Error), 로봇 간 거리 오차, 수렴 시간, 연결성, 충돌률, 에너지 소비, 통신 오버헤드, 장애물 회피 과정의 변형 정도, 외란 이후 복구 시간이 포함된다. 동적 형상(Dynamic Shape)에서는 전환의 부드러움과 재구성 과정에서도 임무 커버리지를 유지할 수 있는 능력 역시 중요하다.

대규모 평가(Large-Scale Evaluation)에서는 밀도와 로봇 개체 수의 영향을 시험해야 한다. 10대의 로봇에서 정상적으로 작동하는 제어 규칙이라도 수백 대에서는 진동, 통신 혼잡, 과도한 반발력이 발생할 수 있다. 시뮬레이션에서는 로봇 고장, 통신 지연, 센서 잡음, 이동 장애물, 좁은 통로, 이기종 동역학, 변화하는 구성원을 평가해야 한다. 확장성(Scalability)은 로봇 수가 증가해도 국소적인 연산 및 통신 요구량을 유지할 수 있는 능력에 달려 있다.

산업용 군집 대형(Industrial Swarm Formation)은 일반적으로 제한 없는 창발적 이동(Unrestricted Emergent Motion)이 아니라 감독 제약(Supervisory Constraint) 내부에서 동작해야 한다. 임무 계층(Mission Layer)은 허용 구역, 최소 안전 거리, 최대 밀도, 목표 형상, 비상 행동을 정의하고, 국소 제어기는 개별 로봇이 이러한 요구조건을 어떻게 만족할지를 결정할 수 있다. 이러한 하이브리드 접근법(Hybrid Approach)은 분산 적응성과 실제 시스템에 필요한 예측 가능성 및 안전 거버넌스(Safety Governance)를 결합한다.

궁극적으로 군집 대형 및 형상 제어(Swarm Formation and Shape Control)는 국소적인 기하학적 관계를 협력적인 공간 조직(Coordinated Spatial Organization)으로 변환한다. 거리 제어, 퍼텐셜 필드, 합의, 그래프 강성(Graph Rigidity), 가상 구조, 행동 기반 방법은 집단 기하 구조를 형성하고 유지하기 위한 상호 보완적인 메커니즘을 제공한다. 여기에 장애물 회피, 연결성 유지, 동적 재구성(Dynamic Reconfiguration), 고장 허용, 안전 제약을 결합하면 로봇 군집은 독립적으로 제어되는 로봇의 집합이 아니라 환경에 적응하는 하나의 공간 시스템(Adaptive Spatial System)으로 이동하고 행동할 수 있다.

## 07.05 Swarm Exploration and Coverage Algorithms [w/Code]

![](images/image5.png){width="7.268055555555556in" height="7.268055555555556in"}

군집 탐색 및 커버리지 알고리즘(Swarm Exploration and Coverage Algorithms)은 중앙 계획기(Central Planner)가 모든 움직임을 제어하지 않고도 다수의 로봇이 미지 또는 부분적으로 알려진 환경을 효율적으로 관측하도록 협력한다. 탐색(Exploration)은 이전에 알려지지 않은 공간을 발견하는 데 초점을 맞추고, 커버리지(Coverage)는 요구된 영역이 충분히 방문되거나 센싱되도록 하는 데 초점을 맞춘다. 실제 군집 시스템에서는 로봇이 환경 지식을 점진적으로 구축하면서 공간적으로 분산되므로 두 목표를 결합하는 경우가 많다.

군집 탐색(Swarm Exploration)의 근본적인 장점은 병렬성(Parallelism)이다. 하나의 로봇이 모든 영역을 순차적으로 방문하는 대신 다수의 로봇이 서로 다른 위치를 동시에 조사할 수 있다. 그러나 단순히 로봇 수를 증가시키는 것만으로 효율성이 보장되지는 않는다. 협력이 없으면 동일한 영역을 반복 방문하거나 좁은 통로에서 경쟁하고, 통신 연결성을 잃거나, 접근하기 어려운 영역을 탐색하지 않은 상태로 남길 수 있다. 따라서 효과적인 알고리즘은 공간적 분산(Spatial Dispersion), 정보 공유, 안전 사이의 균형을 유지해야 한다.

탐색은 점유 격자(Occupancy Grid), 위상 그래프(Topological Graph), 의미론적 지도(Semantic Map), 연속 공간 모델(Continuous Spatial Model)을 이용하여 표현할 수 있다. 각 로봇은 센서와 지도 작성 과정을 기반으로 알려진 자유 공간(Known Free Space), 점유 공간(Occupied Space), 미탐색 공간(Unexplored Space)을 구분한다. 관측 정보가 축적되면 국소 지도(Local Map)를 주변 로봇과 교환하거나 병합할 수 있다. 생성된 환경 지식은 항상 하나의 전역 지도(Global Map)로 동기화되지 않고 분산된 상태로 유지될 수도 있다.

프런티어 기반 탐색(Frontier-Based Exploration)은 가장 널리 적용할 수 있는 접근법 중 하나이다. 프런티어(Frontier)는 알려진 자유 공간과 미탐색 공간 사이의 경계를 의미한다. 로봇은 현재 지도에서 후보 프런티어를 탐지하고 거리, 예상 정보 이득(Expected Information Gain), 접근성, 혼잡도, 임무 우선순위에 따라 목적지를 선택한다. 서로 다른 로봇이 서로 다른 프런티어를 선택하면 군집의 탐색 활동이 여러 미지 영역으로 자연스럽게 분산된다.

가장 가까운 거리만을 기준으로 하는 단순한 프런티어 할당(Frontier Assignment)은 여러 로봇이 동일한 매력적인 프런티어를 선택하면서 비효율적인 군집화(Clustering)를 발생시킬 수 있다. 따라서 분산 프런티어 할당에서는 주변 로봇이 이미 선택한 목적지나 로봇 밀도가 높은 영역에 페널티를 부여한다. 효용 함수(Utility Function)는 이동 비용과 예상 정보 이득을 결합하면서 중복 탐색의 가치를 낮춤으로써 로봇들이 유용한 목표로 분산되도록 유도할 수 있다.

정보 이득(Information Gain)은 탐색 가치를 보다 명시적으로 측정하는 방법이다. 특정 후보 관측 위치에서 센싱함으로써 환경의 상당 부분에 대한 불확실성을 감소시킬 수 있다면 해당 위치의 가치가 높다. 로봇은 미확인 셀(Unknown Cell), 지도 엔트로피(Map Entropy), 예상 가시성(Expected Visibility), 의미론적 중요도(Semantic Importance), 센서 기하 구조 등을 이용하여 정보 이득을 추정할 수 있다. 정보 이득과 이동 비용을 결합하면 추가로 얻는 지식에 비해 이동 비용이 지나치게 큰 원거리 목표를 선택하는 것을 방지할 수 있다.

커버리지(Coverage)는 환경이 이미 알려져 있을 수 있다는 점에서 탐색과 다르며, 전체 요구 영역을 관측, 검사, 청소, 순찰, 살포, 스캔 또는 서비스하는 것을 목표로 한다. 커버리지 알고리즘은 로봇의 이동 및 센싱 제약을 준수하면서 누락 영역과 불필요한 중복을 최소화한다. 응용 분야에 따라 모든 지점을 물리적으로 통과하는 것보다 완전한 기하학적 커버리지(Geometric Coverage) 또는 충분한 센싱 커버리지(Sensing Coverage)를 달성하는 것이 요구될 수 있다.

보로노이 기반 커버리지(Voronoi-Based Coverage)는 자연스러운 분산 전략을 제공한다. 각 로봇은 주변 로봇을 고려하여 환경을 국소 보로노이 영역(Local Voronoi Region)으로 분할하며, 해당 영역은 다른 로봇보다 자신에게 가까운 위치들로 구성된다. 이후 로봇은 자신의 영역 중심점(Centroid)과 같은 대표 위치를 향해 이동한다. 이러한 갱신을 반복하면 모든 위치를 명시적으로 할당하지 않고도 로봇의 공간 분포와 센싱 책임을 비교적 균등하게 만들 수 있다.

중심 보로노이 테셀레이션(Centroidal Voronoi Tessellation)은 중요도, 위험도, 목표 존재 확률, 센싱 수요 등에 따라 영역에 가중치를 부여함으로써 이러한 개념을 확장한다. 우선순위가 높은 영역에는 더 많은 로봇을 배치하고 우선순위가 낮은 영역에는 적은 자원을 배치할 수 있다. 환경 정보가 변화하면 밀도 함수(Density Function)를 갱신하여 군집을 다시 분산시킬 수 있다. 이를 통해 전체 작업 공간에 균일하게 배치하는 대신 환경 변화에 따라 커버리지를 동적으로 조정할 수 있다.

퍼텐셜 필드 기반 커버리지(Potential-Field Coverage)는 충분히 탐색되지 않은 영역에 대한 가상 인력(Virtual Attraction)과 주변 로봇 또는 최근 방문 영역에 대한 반발력(Repulsion)을 이용한다. 인력장은 로봇을 정보가 부족한 영역으로 유도하고, 반발장은 중복 커버리지와 충돌을 줄인다. 환경 경계와 장애물은 추가적인 제약으로 작용한다. 이 방식은 연산이 단순하고 높은 국소성을 가지지만, 필드를 적절하게 설계하지 않으면 국소 최소점(Local Minimum)이나 진동 행동(Oscillatory Behavior)이 발생할 수 있다.

스티그머지 기반 커버리지(Stigmergic Coverage)는 또 다른 분산 메커니즘을 제공한다. 로봇은 최근 방문한 위치를 나타내는 가상 페로몬(Virtual Pheromone) 또는 디지털 마커(Digital Marker)를 남긴다. 다른 로봇은 마커가 약한 영역을 선호하여 상대적으로 방문 빈도가 낮은 공간으로 자연스럽게 이동한다. 마커 증발(Marker Evaporation)을 적용하면 충분한 시간이 지난 뒤 이전 방문 영역이 다시 매력적인 영역이 되므로 지속적인 감시, 순찰, 환경 모니터링, 반복 검사 임무에 특히 유용하다.

증발률(Evaporation Rate)은 커버리지 시스템의 시간적 기억(Temporal Memory)을 결정한다. 느린 증발은 장기간의 방문 정보를 유지하고 반복 방문을 억제하지만 주기적인 관측이 필요한 영역을 적절한 시점에 다시 방문하지 못하게 할 수 있다. 빠른 증발은 반응성을 높이지만 과도한 중복 방문을 발생시킬 수 있다. 따라서 공간 정보의 가치가 얼마나 빠르게 감소하는지와 각 영역을 얼마나 자주 다시 방문해야 하는지를 응용 요구조건에 따라 결정해야 한다.

랜덤 워크 탐색(Random-Walk Exploration)은 가장 단순한 군집 접근법 중 하나이다. 로봇은 장애물과 주변 로봇을 회피하면서 확률적 규칙(Stochastic Rule)에 따라 이동 방향을 선택한다. 순수 랜덤 워크는 구조화된 환경에서 일반적으로 비효율적이지만, 편향 랜덤 워크(Biased Random Walk)는 환경 기울기, 프런티어 정보, 페로몬 값, 목표 존재 가능성을 반영할 수 있다. 구조가 단순하고 통신 요구량이 제한적이므로 지도 작성과 네트워크 인프라가 불안정한 환경에서 유용할 수 있다.

레비 비행 기반 전략(Lévy-Flight-Inspired Strategy)은 많은 짧은 이동과 간헐적인 긴 이동을 포함하는 분포를 사용한다. 이를 통해 로봇이 국소적으로 이미 충분히 탐색된 영역에서 벗어나 일부 희소 환경에서 반복 탐색을 줄일 수 있다. 그러나 실제 로봇은 임의의 장거리를 순간적으로 이동할 수 없으므로 실용적인 구현에서는 이러한 개념을 실행 가능한 내비게이션 목표로 변환하면서 충돌 회피, 환경 경계, 차량 동역학 제약을 함께 유지해야 한다.

분산 그래프 탐색(Distributed Graph Exploration)은 통로, 도로망, 터널, 산업용 통로, 연결된 방처럼 환경을 노드(Node)와 간선(Edge)으로 표현할 수 있을 때 유용하다. 로봇은 탐색되지 않은 노드 또는 간선을 선택하고 주변 로봇과 방문 상태를 교환한다. 국소 예약(Local Reservation) 또는 소유권 메커니즘(Ownership Mechanism)을 이용하면 중복 이동을 줄일 수 있다. 그래프 기반 방법은 간선 비용, 위험도, 접근성, 통신 품질도 탐색 의사결정에 포함할 수 있다.

다중 로봇 탐색(Multi-Robot Exploration)에서는 지도 공유나 원격 감독(Remote Supervision)이 중요한 경우 통신 연결성(Communication Connectivity)을 명시적으로 관리해야 한다. 공격적인 공간 분산은 탐색 속도를 증가시키지만 로봇 사이의 연결을 단절시킬 수 있다. 연결성 인식 알고리즘(Connectivity-Aware Algorithm)은 필수 통신 링크를 끊는 이동에 페널티를 부여하거나 일부 로봇을 임시 중계기(Temporary Relay)로 배치한다. 이를 통해 임무 요구조건에 따라 최대 공간 확장과 연결된 정보 네트워크 사이에서 절충할 수 있다.

통신이 항상 지속적으로 연결될 필요는 없다. 지연 허용 탐색(Delay-Tolerant Exploration)은 일시적인 네트워크 분할(Network Partition) 동안 로봇이 독립적으로 동작하고 연결이 복구되었을 때 축적된 지도나 관측 정보를 교환할 수 있도록 한다. 조우 기반 데이터 교환(Encounter-Based Data Exchange), 저장 후 전달(Store-and-Forward Communication), 기회적 동기화(Opportunistic Synchronization)는 안정적인 통신 인프라를 보장하기 어려운 지하, 실내, 재난, 대규모 야외 환경에서 유용하다.

여러 로봇이 위치추정 불확실성(Localization Uncertainty)을 가진 상태로 중첩 영역을 관측하면 지도 일관성(Map Consistency)을 유지하기 어려워진다. 좌표계 불확실성을 고려하지 않고 지도를 직접 병합하면 구조가 중복되거나 기하학적 왜곡이 발생할 수 있다. 상대 위치추정(Relative Localization), 루프 폐쇄(Loop Closure), 공유 랜드마크(Shared Landmark), 위성항법시스템 기준점(GNSS Anchor), 로봇 간 관측을 이용하여 국소 지도를 정렬할 수 있다. 따라서 탐색 성능은 목표 선택뿐 아니라 분산 지도 작성과 위치추정의 신뢰성에도 영향을 받는다.

장애물 회피(Obstacle Avoidance)와 탐색은 서로 다른 제어 수준에서 동작해야 한다. 탐색 알고리즘은 프런티어, 보로노이 중심점, 낮은 페로몬 영역 등을 목적지로 선택하고, 국소 내비게이션 계층(Local Navigation Layer)은 해당 목적지까지의 안전한 궤적을 생성할 수 있다. 필요한 경우 충돌 회피가 정상적인 탐색 명령보다 우선한다. 이러한 분리는 전역 탐색 목표가 안전에 중요한 차량 운동을 직접 제어하는 것을 방지한다.

이기종 로봇 군집(Heterogeneous Robot Swarm)은 서로 보완적인 센싱 및 이동 능력을 결합하여 탐색 성능을 향상시킬 수 있다. 무인항공기(UAV)는 넓거나 높은 영역을 빠르게 조사하고, 지상 로봇(Ground Robot)은 표면과 제한된 공간을 검사하며, 열화상, 가스, 음향 또는 특수 센서를 장착한 로봇은 특정 목표를 조사할 수 있다. 분산 할당(Distributed Assignment)은 전체 팀의 공간 커버리지를 조정하면서 각 탐색 기회를 적절한 능력을 가진 로봇에 연결할 수 있다.

에너지 제약(Energy Constraint)은 탐색 범위에 큰 영향을 미친다. 로봇은 남은 배터리가 이동, 센싱, 충전소 또는 복구 지점까지의 안전한 복귀를 지원하지 못한다면 먼 프런티어를 선택해서는 안 된다. 에너지 인식 효용 함수(Energy-Aware Utility Function)는 배터리가 감소함에 따라 비용이 높은 목적지의 매력도를 낮출 수 있다. 또한 충전 자체를 분산 작업으로 취급하여 지나치게 많은 로봇이 동시에 탐색 임무에서 이탈하지 않도록 할 수 있다.

탐색은 불확실한 환경에서 수행되는 경우가 많기 때문에 고장 허용(Fault Tolerance)이 특히 중요하다. 하나의 로봇이 고장 나면 해당 로봇에 할당되었던 영역이나 프런티어를 일정 시간이 지난 뒤 다른 로봇이 다시 수행할 수 있어야 한다. 시간 제한 예약(Time-Limited Reservation), 하트비트 모니터링(Heartbeat Monitoring), 국소 지도 증거(Local Map Evidence), 작업 리스(Task Lease)를 이용하여 재할당을 시작할 수 있다. 환경 지식이 여러 로봇에 분산되어 있으므로 개별 로봇의 손실은 전체 임무 상태를 파괴하기보다 탐색 능력을 점진적으로 저하시켜야 한다.

동적 환경(Dynamic Environment)에서는 이전에 탐색한 영역도 다시 검토해야 한다. 문이 열리거나 닫힐 수 있고, 장애물이 이동하거나, 위험 요소가 나타나거나, 접근성이 변할 수 있다. 따라서 지도는 지속적인 구조(Persistent Structure)와 일시적인 관측(Transient Observation)을 구분해야 한다. 프런티어와 커버리지 효용에는 관측 경과 시간(Observation Age)을 포함하여 오래된 영역이 점진적으로 다시 높은 우선순위를 갖도록 할 수 있다. 이를 통해 탐색을 일회성 작업으로 처리하지 않고 최신 환경 지식을 유지할 수 있다.

탐색과 커버리지의 목표는 서로 충돌할 수 있다. 빠른 프런티어 확장은 로봇을 알려진 공간의 경계로 이동시키는 것을 선호하지만, 균일한 커버리지는 이미 알려진 영역 전체에 로봇을 분산시킬 필요가 있다. 하이브리드 전략(Hybrid Strategy)은 군집을 탐색 역할과 커버리지 역할로 분리하거나 임무 진행 상태에 따라 각 로봇의 효용을 지속적으로 조정할 수 있다. 미지 영역이 감소하고 모니터링 요구가 중요해짐에 따라 역할 할당(Role Allocation)을 동적으로 변경할 수 있다.

성능 평가(Performance Evaluation)에서는 시간에 따른 탐색 면적, 커버리지 비율, 중복률(Overlap Ratio), 정보 이득, 이동 거리, 에너지 소비, 통신 오버헤드, 지도 품질(Map Quality), 충돌률, 요구 커버리지 도달 시간을 고려해야 한다. 지속 임무(Persistent Mission)에서는 재방문 간격(Revisit Interval)과 정보 신선도(Age of Information)도 중요한 지표가 된다. 평가는 빠른 초기 발견 능력과 장시간 동안 유용한 커버리지를 유지하는 능력을 구분해야 한다.

확장성(Scalability)은 환경 크기와 로봇 수를 함께 증가시키면서 시험해야 한다. 초기에는 로봇을 추가할수록 탐색 속도가 향상되지만, 일정 규모 이후에는 혼잡, 통신 트래픽, 중복 관측, 제한된 프런티어 수로 인해 추가적인 효과가 감소한다. 효과적인 군집 알고리즘은 의사결정을 국소적으로 유지하고 전역 전대전 동기화(Global All-to-All Synchronization)를 피해야 한다. 따라서 중요한 질문은 단순히 얼마나 많은 로봇을 추가할 수 있는가가 아니라 추가된 로봇이 새로운 정보 획득에 얼마나 효율적으로 기여하는가이다.

산업용 배치(Industrial Deployment)에서는 일반적으로 분산 탐색과 감독 제약(Supervisory Constraint)을 결합한다. 임무 계층(Mission Layer)은 허용 구역, 금지 구역, 최소 통신 요구조건, 안전 경계, 검사 우선순위, 완료 기준을 정의할 수 있다. 개별 로봇은 이러한 제약 내부에서 스스로 공간적으로 분산되고 국소 목표를 선택한다. 이러한 하이브리드 구조(Hybrid Structure)는 군집의 적응성을 유지하면서 실제 자율 운영에 필요한 거버넌스(Governance)를 제공한다.

궁극적으로 군집 탐색 및 커버리지(Swarm Exploration and Coverage)는 다수의 국소 센싱 및 이동 의사결정을 협력적인 환경 지식 획득(Coordinated Environmental Knowledge Acquisition)으로 변환한다. 프런티어 선택은 새로운 공간의 발견을 유도하고, 보로노이 방법은 공간적 책임을 분산하며, 퍼텐셜 필드는 군집의 분산 정도를 조절하고, 스티그머지 마커는 중복 방문을 줄인다. 여기에 지도 작성, 통신, 에너지 관리, 고장 복구, 안전 계층을 결합하면 로봇 군집은 대규모 환경을 효율적이고 적응적이며 복원력 있게 탐색하고 모니터링할 수 있다.

## 07.06 Swarm Communication Local Broadcast [w/Code]

![](images/image6.png){width="7.268055555555556in" height="7.268055555555556in"}

군집 통신(Swarm Communication)은 모든 로봇이 다른 모든 구성원과 지속적으로 통신하지 않고도 다수의 자율 로봇이 협력할 수 있도록 하는 정보 교환 메커니즘(Information Exchange Mechanism)을 제공한다. 국소 방송(Local Broadcast)은 각 로봇이 제한된 이웃 영역에만 관련 상태 또는 이벤트 정보를 전송하기 때문에 군집 로보틱스(Swarm Robotics)에 특히 적합하다. 이후 반복적인 피어 간 상호작용(Peer-to-Peer Interaction)을 통해 집단 지식(Collective Knowledge)이 군집 전체로 전파된다.

중앙집중식 플릿 통신(Centralized Fleet Communication)과 달리 국소 방송은 모든 로봇 메시지가 중앙 서버(Central Server)를 통과해야 한다고 가정하지 않는다. 로봇은 자신의 위치, 속도, 작업 상태, 감지된 위험, 국소 지도 갱신(Local Map Update), 협력 의도(Coordination Intention)를 주변 로봇에 직접 알릴 수 있다. 이웃 로봇은 이러한 정보를 즉각적인 의사결정에 사용하고, 필요한 경우 선택된 정보를 네트워크의 더 먼 영역으로 다시 전파할 수 있다.

통신 범위(Communication Range)는 각 로봇 주변의 동적인 이웃 영역(Dynamic Neighborhood)을 자연스럽게 정의한다. 로봇이 이동함에 따라 통신 링크가 생성되고 사라지면서 네트워크 토폴로지(Network Topology)가 지속적으로 변화한다. 따라서 군집 통신 그래프(Swarm Communication Graph)는 고정된 구조가 아니라 시간에 따라 변화하는 구조(Time-Varying Structure)이다. 각 로봇이 전체 군집의 일부에만 일시적으로 접근하고 서로 다른 국소 상태 정보를 유지하더라도 알고리즘은 정상적으로 동작해야 한다.

국소 방송(Local Broadcast)은 통신 비용이 전체 군집 규모에 반드시 비례하여 증가하지 않기 때문에 확장성(Scalability)을 지원한다. 각 로봇이 주변 이웃과만 통신한다면 수백 대 규모의 군집에서도 모든 구성원이 수백 대의 로봇과 직접 메시지를 교환할 필요가 없다. 실제 통신 부하는 전체 로봇 수보다 국소 로봇 밀도(Local Robot Density), 메시지 빈도, 패킷 크기, 통신 반경에 더 큰 영향을 받는다.

무선 대역폭(Wireless Bandwidth)은 주변 로봇들이 공유하므로 방송 메시지는 간결하게 유지해야 한다. 일반적인 메시지에는 로봇 식별자, 타임스탬프(Timestamp), 위치 또는 자세 추정값, 속도, 작업 상태, 배터리 상태, 국소 위험 정보, 예약 정보, 선택된 지도 변경 사항 등이 포함될 수 있다. 전체 내부 상태를 높은 빈도로 전송하면 불필요한 트래픽이 발생한다. 따라서 군집 통신은 국소 협력에 필요한 정보만 교환하는 것이 효과적이다.

메시지 빈도(Message Frequency)는 전송되는 정보의 동적 특성을 반영해야 한다. 이동 관련 상태는 비교적 빈번한 갱신이 필요하지만, 능력 설명(Capability Description), 임무 역할, 정적 구성 정보는 훨씬 낮은 빈도로 전송할 수 있다. 이벤트 기반 통신(Event-Driven Communication)을 적용하면 일정한 최대 주기로 메시지를 보내는 대신 의미 있는 변화가 발생할 때 정보를 전송하여 네트워크 부하를 줄일 수 있다. 따라서 서로 다른 정보 유형을 서로 다른 통신 시간 척도(Communication Timescale)에서 처리할 수 있다.

이웃 탐색(Neighborhood Discovery)을 통해 로봇은 현재 어떤 피어(Peer)와 통신할 수 있는지를 판단한다. 주기적인 비콘(Beacon) 또는 하트비트(Heartbeat) 메시지를 이용하여 로봇의 식별 정보, 상태, 통신 가용성을 알릴 수 있다. 로봇은 최근 관측된 피어를 포함하는 이웃 테이블(Neighbor Table)을 유지하고, 지정된 시간 동안 메시지를 수신하지 못하면 해당 항목을 제거한다. 이러한 국소 구성원 관리 메커니즘(Local Membership Mechanism)을 통해 로봇의 이동, 고장, 재연결에 따라 군집 토폴로지가 지속적으로 적응할 수 있다.

국소 방송은 합의 알고리즘(Consensus Algorithm)과 밀접하게 연결된다. 로봇들은 주변 이웃과 추정값을 반복적으로 교환하고 수신된 정보에 따라 자신의 국소 값을 갱신한다. 위치 오프셋(Position Offset), 속도, 진행 방향, 작업 결정, 환경 측정값, 공유 변수 등이 연결된 군집 영역에서 점진적으로 수렴할 수 있다. 따라서 하나의 노드가 모든 상태를 수집하고 재분배하지 않아도 국소적인 정보 교환을 통해 전역적인 합의(Global Agreement)가 형성될 수 있다.

즉각적인 이웃 범위를 넘어 정보를 전파하려면 제어된 다중 홉 전달(Controlled Multi-Hop Forwarding)을 사용할 수 있다. 중요한 메시지를 수신한 로봇이 이를 재전송하면 정보가 연속적인 이웃 관계를 통해 군집 전체로 이동할 수 있다. 그러나 제어되지 않은 재방송은 밀집된 군집에서 방송 폭주(Broadcast Storm)를 발생시킬 수 있다. 홉 제한(Hop Limit), 시퀀스 번호(Sequence Number), 중복 억제(Duplicate Suppression), 전달 확률, 관련성 필터링(Relevance Filtering), 지리적 범위 제한 등을 이용하여 유용한 정보 전파를 유지하면서 불필요한 재전송을 제한할 수 있다.

가십 통신(Gossip Communication)은 확률적 대안을 제공한다. 모든 이웃에게 정보를 전달하는 대신 로봇은 주기적으로 하나 또는 여러 피어와 선택된 상태 정보를 교환한다. 이러한 상호작용이 반복되면서 정보가 전체 군집으로 점진적으로 확산된다. 가십 프로토콜(Gossip Protocol)은 변화하는 토폴로지와 부분 연결성에 대한 내성이 높지만 결정론적 플러딩(Deterministic Flooding)보다 정보 전파가 느릴 수 있다. 즉각적인 전역 동기화보다 확장성과 강건성(Robustness)이 중요한 환경에서 유용하다.

스티그머지 통신(Stigmergic Communication)은 직접적인 메시지 교환을 더욱 줄일 수 있다. 로봇은 공유 디지털 지도(Shared Digital Map), 가상 페로몬 필드(Virtual Pheromone Field), 작업 마커(Task Marker), 환경 상태 표현에 정보를 기록할 수 있다. 다른 로봇은 관련 영역에 진입했을 때 해당 정보를 관측한다. 이를 통해 통신의 일부가 간접적이고 공간적 맥락(Spatial Context)을 가진 형태로 전환된다. 이러한 방식은 대규모 환경의 탐색, 커버리지, 작업 할당, 교통 관리에 특히 유용하다.

무선 링크는 본질적으로 완벽하지 않으므로 군집 통신은 패킷 손실(Packet Loss)을 허용해야 한다. 간섭, 장애물, 다중경로 전파(Multipath Propagation), 로봇 방향, 네트워크 혼잡, 경쟁 트래픽으로 인해 메시지가 손실될 수 있다. 알고리즘은 모든 방송이 모든 이웃에 전달된다고 가정해서는 안 된다. 중복된 주기적 갱신, 국소 예측(Local Prediction), 시퀀스 번호, 타임아웃 규칙(Timeout Rule), 상태 추정(State Estimation)을 이용하면 일부 메시지가 손실되더라도 협력을 계속할 수 있다.

지연(Latency) 역시 집단 행동에 영향을 준다. 지연된 위치나 속도 정보를 사용하는 로봇은 이미 상당히 이동한 이웃의 과거 상태에 반응할 수 있다. 이는 대형 제어(Formation Control)를 불안정하게 만들거나 충돌 위험을 증가시킬 수 있다. 따라서 메시지에는 타임스탬프가 포함되어야 하며 제어 알고리즘은 최신 데이터와 오래된 데이터(Stale Data)를 구분해야 한다. 제한된 지연은 예측이나 외삽(Extrapolation)을 통해 보상할 수 있지만 안전이 중요한 충돌 회피는 네트워크 통신에만 의존해서는 안 된다.

비동기 운용(Asynchronous Operation)은 로봇들이 통신 및 제어 주기를 정확히 동일한 시점에 실행하는 경우가 거의 없기 때문에 기본적으로 고려해야 한다. 각 로봇은 서로 다른 프로세서 부하, 센싱 주기, 네트워크 지연, 클록 오프셋(Clock Offset)을 가질 수 있다. 따라서 분산 알고리즘은 엄격한 동기 실행(Lockstep Synchronization)을 요구하기보다 사용 가능한 최신 정보를 기반으로 동작해야 한다. 시간 동기화(Time Synchronization)는 여전히 유용하지만 완벽한 동기화가 불가능한 상황에서도 군집은 계속 동작해야 한다.

여러 로봇의 타임스탬프를 정확하게 비교해야 하는 경우 클록 동기화(Clock Synchronization)가 중요해진다. 인프라를 사용할 수 있는 환경에서는 네트워크 시간 동기화(Network Time Synchronization) 또는 정밀 시간 프로토콜(Precision Time Protocol, PTP)을 이용하여 공통 시간 기준을 제공할 수 있다. 구조화되지 않은 환경에서는 작업 협력에 근사적인 동기화만으로 충분할 수 있지만 국소 센서 융합(Local Sensor Fusion)은 더 정밀한 시간이 필요할 수 있다. 따라서 통신 아키텍처는 응용 요구조건에 맞춰 동기화 정밀도를 설정해야 한다.

다중 홉 정보 흐름(Multi-Hop Information Flow)에 협력이 의존하는 경우 연결성 유지(Connectivity Preservation)가 중요하다. 로봇이 지나치게 공격적으로 분산되면 통신 그래프가 서로 연결되지 않은 여러 구성요소로 분할될 수 있다. 연결성 인식 이동(Connectivity-Aware Motion)은 필수 통신 링크를 끊는 궤적에 페널티를 부여하고, 선택된 로봇은 임시 통신 중계기(Communication Relay) 역할을 수행할 수 있다. 이를 통해 군집은 공간적 커버리지와 전체 팀의 정보 경로 유지 사이에서 균형을 조절할 수 있다.

항상 연결된 통신(Permanent Connectivity)이 필요한 것은 아니다. 지연 허용 군집 통신(Delay-Tolerant Swarm Communication)을 사용하면 연결이 끊어진 그룹이 독립적으로 작업을 계속하고 이후 접촉이 복구되었을 때 정보를 동기화할 수 있다. 로봇은 메시지, 지도, 작업 갱신, 관측 정보를 저장한 뒤 이후 다른 로봇과 만났을 때 전달할 수 있다. 이러한 저장 후 전달(Store-and-Forward) 방식은 터널, 지하 시설, 재난 현장, 대형 창고, 통신 범위가 간헐적인 야외 환경에서 유용하다.

통신 분할(Communication Partition)이 발생하면 서로 충돌하는 국소 정보가 생성될 수 있다. 연결이 끊어진 두 하위 그룹이 동일한 작업을 독립적으로 할당하거나 서로 다른 지도 버전을 수정하거나 호환되지 않는 의사결정을 수행할 수 있다. 다시 연결되었을 때는 타임스탬프, 버전 번호(Version Number), 소유권 리스(Ownership Lease), 신뢰도 값(Confidence Value), 결정론적 우선순위(Deterministic Priority)를 기반으로 상태를 조정해야 한다. 따라서 분할 허용(Partition Tolerance)은 메시지 전송뿐 아니라 응용 계층의 충돌 해결(Application-Level Conflict Resolution)까지 필요로 한다.

로봇 밀도가 증가할수록 대역폭 할당(Bandwidth Allocation)의 중요성도 증가한다. 이동 협력, 안전 경보, 지도 갱신, 센서 데이터, 진단 정보, 임무 명령이 동일한 무선 채널을 두고 경쟁할 수 있다. 우선순위 등급(Priority Class)을 적용하면 긴급 제어 또는 안전 정보가 대용량 지도 전송이나 중요도가 낮은 텔레메트리보다 우선적으로 처리되도록 할 수 있다. 전송률 제한(Rate Limiting)과 적응형 발행(Adaptive Publishing)을 이용하면 낮은 가치의 트래픽이 군집 협력 성능을 저하시키는 것을 방지할 수 있다.

원시 센서 스트림(Raw Sensor Stream)은 일반적으로 군집 전체에 지속적으로 방송해서는 안 된다. 카메라, 라이다(LiDAR), 깊이 센서(Depth Sensor)와 같은 고대역폭 장치는 무선 네트워크를 빠르게 포화시킬 수 있다. 대신 로봇이 센서 데이터를 국소적으로 처리하고 압축된 특징(Compact Feature), 탐지 객체, 지도 변경 사항, 의미론적 이벤트(Semantic Event), 압축 요약(Compressed Summary)을 교환할 수 있다. 이러한 엣지 처리(Edge Processing) 원칙은 통신을 집단 의사결정에 직접 기여하는 정보에 집중시킨다.

통신 품질(Communication Quality) 자체를 군집 행동의 입력으로 사용할 수도 있다. 로봇은 신호 강도, 패킷 전달률(Packet Delivery Ratio), 지연, 이웃 연결 안정성을 추정하고 이를 내비게이션이나 작업 의사결정에 반영할 수 있다. 연결이 끊길 가능성이 높은 영역으로 진입하는 것을 피하거나 군집이 중계 로봇을 재배치하여 네트워크 품질을 복구할 수 있다. 따라서 통신은 단순한 인프라가 아니라 집단 상태(Collective State)의 일부가 된다.

이기종 군집(Heterogeneous Swarm)은 서로 다른 통신 기술이나 대역폭 능력을 사용하는 로봇들로 구성될 수 있다. 지상 로봇, 무인항공기, 매니퓰레이터, 고정 인프라 노드는 와이파이(Wi-Fi), 셀룰러 통신(Cellular Link), 메시 무선통신(Mesh Radio), 특수 저속 채널 등을 사용할 수 있다. 필요한 경우 게이트웨이 로봇(Gateway Robot)이 서로 다른 네트워크 구간을 연결할 수 있다. 기반 물리 링크가 서로 다르더라도 통신 프로토콜은 공통된 의미론적 메시지(Common Semantic Message)를 제공해야 한다.

국소 방송은 통신 참여자와 잠재적인 공격 표면(Attack Surface)을 증가시키므로 보안(Security)이 중요하다. 로봇은 중요한 메시지를 인증하고 허가되지 않은 명령이나 명백하게 잘못된 상태 정보를 거부해야 한다. 무결성 보호(Integrity Protection), 접근 제어(Access Control), 보안 식별(Secure Identity), 이상 탐지(Anomaly Detection)를 이용하면 악의적이거나 손상된 정보가 집단 행동에 영향을 미치는 위험을 줄일 수 있다. 동시에 보안 메커니즘은 분산 운용에 적합한 효율성을 유지해야 한다.

고장 탐지(Fault Detection)에도 통신 상태를 활용할 수 있다. 하트비트가 사라지면 로봇 고장, 네트워크 단절 또는 전원 손실을 의미할 수 있다. 주변 로봇은 해당 로봇을 일시적으로 사용 불가능한 상태로 표시하고 작업 재할당(Task Reassignment), 대형 복구(Formation Repair), 탐색 절차를 시작할 수 있다. 그러나 통신 실패가 항상 물리적 고장을 의미하는 것은 아니므로 즉각적으로 영구 제거하기보다 타임아웃, 다중 관측, 신뢰도 수준을 기반으로 판단해야 한다.

국소 방송(Local Broadcast)은 분산 작업 할당(Distributed Task Assignment)과 자연스럽게 통합된다. 로봇은 사용 가능한 작업, 입찰(Bid), 커밋(Commitment), 완료, 취소 정보를 주변 피어에 알릴 수 있다. 정보는 운영상 필요한 범위까지만 전파되어 전역 디스패처(Global Dispatcher)에 대한 의존성을 줄인다. 동일한 통신 방식은 주변 로봇의 운동 상태를 교환하여 대형 제어를 지원하고, 프런티어, 지도 또는 방문 정보를 공유하여 탐색을 지원할 수 있다.

성능 평가(Performance Evaluation)에는 패킷 전달률, 종단 간 지연(End-to-End Latency), 이웃 탐색 시간, 메시지 오버헤드, 채널 사용률(Channel Utilization), 정보 전파 시간, 연결성, 네트워크 분할 이후의 복구 성능이 포함되어야 한다. 응용 수준의 영향도 동일하게 중요하다. 일정 수준의 패킷 손실이 존재하더라도 작업 할당, 대형 제어, 탐색이 안정적으로 유지된다면 해당 네트워크는 충분히 사용 가능할 수 있다. 따라서 통신은 집단 행동과 함께 평가해야 한다.

확장성 시험(Scalability Testing)에서는 전체 로봇 수뿐 아니라 로봇 밀도도 증가시켜야 한다. 국소 프로토콜이라도 많은 로봇이 동일한 물리적 영역에 집중되어 하나의 무선 채널을 공유하면 심각한 혼잡이 발생할 수 있다. 시뮬레이션과 현장 시험에서는 메시지 충돌, 방송 폭주, 간섭, 지연된 갱신, 토폴로지 변화, 네트워크 분할을 평가해야 한다. 높은 밀도에서는 적응형 메시지 전송률(Adaptive Message Rate)과 관련성 필터링이 더욱 중요해진다.

산업용 구현(Industrial Implementation)에서는 국소 군집 통신과 감독 인프라(Supervisory Infrastructure)를 결합할 수 있다. 인접 로봇은 시간에 민감한 협력 정보를 직접 교환하고, 게이트웨이 또는 액세스 포인트(Access Point)는 임무 갱신, 로깅(Logging), 원격 모니터링, 기업 시스템 통합(Enterprise Integration)을 제공할 수 있다. 인프라 연결이 일시적으로 끊기더라도 국소 협력은 계속될 수 있다. 이러한 하이브리드 아키텍처(Hybrid Architecture)는 즉각적인 군집 상호작용과 상위 수준의 플릿 및 운영 통신을 분리한다.

궁극적으로 국소 방송을 이용한 군집 통신(Swarm Communication through Local Broadcast)은 다수의 단거리 정보 교환을 집단 협력(Collective Coordination)으로 변환한다. 이웃 탐색은 상호작용 가능한 로봇을 결정하고, 국소 메시지는 즉각적인 의사결정을 지원하며, 다중 홉 또는 가십 메커니즘은 선택된 지식을 확산시키고, 지연 허용 방식은 통신 단절 상황에서도 운용을 지속하게 한다. 여기에 대역폭 관리, 보안, 고장 처리, 국소 자율성을 결합하면 복원력 있는 로봇 군집을 위한 확장 가능한 통신 기반을 구축할 수 있다.

## 07.07 Fault Tolerance in Swarm Robots [w/Code]

![](images/image7.png){width="7.268055555555556in" height="7.268055555555556in"}

군집 로봇의 고장 허용(Fault Tolerance in Swarm Robots)은 개별 로봇, 통신 링크, 센서, 액추에이터 또는 연산 구성요소에 고장이 발생하더라도 다중 로봇 집단(Multi-Robot Collective)이 임무를 계속 수행할 수 있는 능력을 의미한다. 소수의 핵심 장치에 크게 의존하는 기존 시스템과 달리 군집 아키텍처(Swarm Architecture)는 기능을 다수의 에이전트(Agent)에 분산한다. 이러한 중복성(Redundancy)을 통해 개별 고장이 즉각적인 임무 붕괴를 초래하기보다 전체 집단의 성능이 점진적으로 감소하도록 할 수 있다.

기본 원칙은 어떤 하나의 로봇도 피할 수 없는 단일 장애점(Single Point of Failure)이 되어서는 안 된다는 것이다. 개별 로봇은 센싱, 이동, 통신, 연산 또는 작업 실행에 기여할 수 있지만 일부 구성원이 사라지더라도 핵심 군집 기능은 복구 가능해야 한다. 따라서 분산 의사결정(Distributed Decision Making), 중복 능력(Redundant Capability), 국소 상호작용(Local Interaction), 동적 재할당(Dynamic Reassignment)은 선택적인 복구 기능이 아니라 복원력(Resilience)을 위한 구조적 메커니즘이 된다.

고장(Failure)은 여러 수준에서 발생할 수 있다. 로봇은 완전한 전원 손실, 프로세서 고장, 이동 성능 저하, 센서 오작동, 액추에이터 손상, 위치추정 오류(Localization Error), 통신 단절 또는 소프트웨어 결함을 경험할 수 있다. 부분 고장(Partial Failure)은 로봇이 계속 동작하면서도 성능이 저하되거나 잘못된 행동을 생성할 수 있기 때문에 특히 어렵다. 따라서 고장 허용 군집은 완전한 기능 상실과 성능 저하, 그리고 잠재적으로 위험한 행동을 구분해야 한다.

고장 탐지(Fault Detection)는 관측 가능한 증거에서 시작한다. 주변 로봇은 하트비트 메시지(Heartbeat Message), 예상 움직임, 작업 진행 상태, 센서 일관성, 통신 활동 또는 행동 반응을 모니터링할 수 있다. 하트비트가 사라지면 고장이나 일시적인 통신 단절을 의미할 수 있으며, 명령된 움직임을 반복적으로 수행하지 못하면 이동 성능 저하를 의미할 수 있다. 관측에는 불확실성이 존재하므로 고장 탐지는 하나의 사건에 의존하기보다 타임아웃(Timeout), 신뢰도 수준(Confidence Level), 다중 지표(Multiple Indicator)를 이용해야 한다.

분산 고장 탐지(Distributed Fault Detection)는 하나의 중앙 상태 모니터(Central Health Monitor)에 대한 의존성을 제거한다. 각 로봇은 국소적으로 이용 가능한 정보를 사용하여 주변 피어(Peer)를 평가하고 고장 관측 정보를 이웃과 교환할 수 있다. 여러 로봇의 판단이 일치하면 실제 고장이라는 신뢰도를 높일 수 있다. 이러한 방식은 감독 인프라(Supervisory Infrastructure)와의 통신을 사용할 수 없을 때 특히 유용하지만, 잘못된 고장 판정을 방지하려면 서로 일치하지 않는 국소 관측을 신중하게 조정해야 한다.

고장 탐지(Failure Detection)와 고장 격리(Failure Isolation)는 서로 다른 과정이다. 탐지는 비정상 행동이 존재한다는 사실을 판단하는 것이며, 격리는 영향을 받은 로봇, 하위 시스템 또는 기능을 식별하는 것이다. 카메라가 고장 난 로봇도 이동이나 통신 서비스를 제공할 수 있지만, 조향 장치가 고장 난 로봇은 더 이상 안전하게 이동하지 못할 수 있다. 기능 수준의 고장 격리(Capability-Level Isolation)를 적용하면 부분적으로 성능이 저하된 모든 로봇을 완전히 제거하는 대신 여전히 사용할 수 있는 기능을 유지할 수 있다.

따라서 상태 정보(Health State)는 단순한 정상 또는 고장 플래그가 아니라 동적인 기능 프로파일(Dynamic Capability Profile)로 표현할 수 있다. 로봇은 사용 가능한 센싱, 이동, 조작, 통신, 에너지, 위치추정 능력과 함께 각각의 신뢰도 또는 성능 저하 수준을 알릴 수 있다. 분산 작업 할당(Distributed Task Allocation)은 사용할 수 없는 기능이 필요한 작업을 해당 로봇에 할당하지 않으면서도 여전히 안전하게 수행할 수 있는 임무에는 해당 로봇을 계속 활용할 수 있다.

작업 재할당(Task Reassignment)은 가장 중요한 군집 복구 메커니즘 중 하나이다. 로봇이 작업 수행 중 고장 나면 완료되지 않은 작업을 적합한 주변 로봇이 다시 수행할 수 있어야 한다. 작업 리스(Task Lease), 소유권 타이머(Ownership Timer), 진행 상태 모니터링, 완료 확인(Completion Acknowledgment)을 이용하면 작업이 고장 난 로봇에 영구적으로 묶이는 것을 방지할 수 있다. 재할당은 단순히 가장 가까운 생존 로봇을 선택하는 것이 아니라 능력, 거리, 에너지, 작업량, 작업 우선순위를 고려해야 한다.

중복성(Redundancy)은 많은 고장 허용 행동의 물리적 기반을 제공한다. 여러 로봇이 유사한 기능을 수행할 수 있다면 하나의 구성원을 잃더라도 다른 로봇이 이를 보완할 수 있다. 그러나 중복성을 위해 모든 로봇이 동일할 필요는 없다. 이기종 군집(Heterogeneous Swarm)은 다중 센싱 방식, 대체 통신 경로 또는 동일한 임무 목표를 수행할 수 있는 서로 다른 로봇 유형처럼 서로 중첩되는 능력을 통해 기능적 중복성(Functional Redundancy)을 제공할 수 있다.

통신 고장(Communication Failure)은 연락 두절이 반드시 로봇 자체의 고장을 의미하지 않기 때문에 별도로 처리해야 한다. 로봇은 물리적으로 정상이어도 장애물, 간섭, 통신 거리 제한 또는 네트워크 혼잡으로 인해 일시적으로 연결이 끊어질 수 있다. 군집은 통신 불확실성(Communication Uncertainty)과 확인된 물리적 고장을 구분해야 한다. 임시 소유권 리스(Temporary Ownership Lease)와 지연된 상태 조정(Delayed Reconciliation)을 이용하면 연결이 끊어진 로봇이 독립적으로 작업을 계속하는 동안 중복된 복구 동작이 발생하는 것을 방지할 수 있다.

네트워크 분할(Network Partition)은 군집을 서로 통신할 수 없는 여러 그룹으로 나눌 수 있다. 각 하위 그룹(Subgroup)은 전역 연결이 복구되기를 무한정 기다리는 대신 국소적으로 수행 가능한 작업을 계속해야 한다. 통신이 복구되면 작업 상태, 지도, 관측 정보, 로봇 상태 정보를 다시 조정해야 한다. 버전 번호(Version Number), 타임스탬프(Timestamp), 결정론적 충돌 해결 규칙(Deterministic Conflict Rule), 신뢰도 값(Confidence Value)을 이용하면 네트워크가 분리된 상태로 운용된 이후 일관성 있는 복구를 지원할 수 있다.

대형 제어(Formation Control)는 로봇이 사라질 경우 명시적인 복구 기능이 필요하다. 하나의 로봇이 손실되면 기하학적인 빈 공간이 발생하거나 중요한 통신 간선(Communication Edge)이 끊어질 수 있다. 주변 로봇은 빈자리를 채우거나 간격을 재분배하고, 대형 토폴로지(Formation Topology)를 변경하거나 대체 역할을 선출할 수 있다. 그래프 복구 메커니즘(Graph Repair Mechanism)은 대형이 적응하는 동안 연결성을 유지할 수 있다. 목표는 반드시 원래의 정확한 기하 구조를 복원하는 것이 아니라 임무에 필요한 구조를 유지하는 것이다.

탐색 및 커버리지 시스템(Exploration and Coverage System)도 유사한 방식으로 복구할 수 있다. 특정 영역을 담당한 로봇이 고장 나면 해당 로봇의 미탐색 프런티어(Unexplored Frontier) 또는 커버리지 영역이 점차 다시 높은 우선순위를 가져야 한다. 가상 페로몬 감쇠(Virtual Pheromone Decay), 작업 만료(Task Expiration), 지도 증거(Map Evidence), 국소 관측을 통해 방치된 영역이 생존 로봇에게 다시 매력적인 목표가 되도록 할 수 있다. 환경 지식이 분산되어 있으므로 하나의 로봇이 고장 나더라도 중요한 임무 정보가 손실되지 않도록 지도 정보를 충분히 복제해야 한다.

리더 기반 군집 아키텍처(Leader-Based Swarm Architecture)는 리더의 고장이 집단 이동이나 협력을 방해할 수 있기 때문에 특정한 취약성을 가진다. 리더 선출(Leader Election)을 이용하면 현재 리더를 사용할 수 없게 되었을 때 다른 로봇이 해당 역할을 수행할 수 있다. 다중 리더(Multi-Leader) 또는 가상 리더(Virtual Leader) 방식은 하나의 물리적 에이전트에 대한 의존성을 감소시킨다. 임무 요구조건이 허용한다면 무리더 합의 아키텍처(Leaderless Consensus Architecture)는 지속적인 계층 구조 없이 집단적인 기준을 형성함으로써 더 높은 복원력을 제공할 수 있다.

에너지 고갈(Energy Depletion) 역시 예측 가능한 가용성 손실(Predictable Availability Loss)의 한 형태로 처리해야 한다. 임계 배터리 수준에 접근하는 로봇은 충전을 위해 이탈하기 전에 가용성 감소를 미리 알릴 수 있다. 이를 통해 갑작스러운 정지 이후가 아니라 사전에 작업이나 대형 위치를 점진적으로 다른 로봇에 전달할 수 있다. 예측형 에너지 관리(Predictive Energy Management)는 잠재적인 일부 고장을 계획된 전환(Planned Transition)으로 변환하여 군집의 중단을 줄이고 필요한 개체 밀도를 유지하도록 한다.

점진적 성능 저하(Graceful Degradation)는 핵심적인 설계 목표이다. 군집은 단순히 고장에서 살아남는지만으로 평가해서는 안 되며 고장이 누적됨에 따라 성능이 어떻게 변화하는지도 평가해야 한다. 여러 로봇의 손실은 임무 완료 시간을 증가시키고 센싱 밀도나 통신 중복성을 감소시킬 수 있지만 임무 자체는 계속 수행할 수 있다. 시스템은 명확하게 정의된 최소 운용 능력(Minimum Operational Capability)을 더 이상 유지할 수 없을 때까지 점진적으로 성능이 저하되도록 설계해야 한다.

임계 규모 분석(Critical-Mass Analysis)은 이러한 경계를 결정하는 데 도움을 준다. 일부 임무에는 최소한의 정상 로봇 수, 통신 중계기, 센싱 장치 또는 특수 기능이 필요하다. 이러한 임계값 아래에서는 임무를 계속 수행하는 것이 안전하지 않거나 효과적이지 않을 수 있다. 따라서 고장 허용 제어는 어떠한 상황에서도 무조건 운용을 지속한다고 가정하기보다 성능 저하 운용(Degraded Operation), 재집결(Regrouping), 철수(Retreat), 안전 정지(Safe Shutdown), 추가 자원 요청을 위한 임무 수준의 조건을 포함해야 한다.

비잔틴 또는 잘못된 행동(Byzantine or Incorrect Behavior)은 단순한 로봇 손실보다 처리하기 어렵다. 오작동하는 로봇이 계속해서 그럴듯하지만 잘못된 위치, 작업 또는 센서 정보를 전송할 수 있기 때문이다. 이웃 비교(Neighbor Comparison), 일관성 검사(Consistency Checking), 물리적 타당성 검사(Physical Plausibility Test), 평판 메커니즘(Reputation Mechanism), 중복 관측(Redundant Observation)을 이용하여 모순되는 행동을 식별할 수 있다. 가능한 경우 안전에 중요한 의사결정은 하나의 피어가 제공하는 검증되지 않은 정보에 의존하지 않아야 한다.

사이버보안(Cybersecurity)과 고장 허용은 악의적인 행동이 기술적 고장과 유사하게 나타날 수 있기 때문에 밀접하게 연관된다. 위조된 신원(Spoofed Identity), 조작된 상태 메시지, 허가되지 않은 명령, 변조된 지도 정보는 집단 행동을 방해할 수 있다. 인증(Authentication), 메시지 무결성(Message Integrity), 보안 신원(Secure Identity), 접근 제어(Access Control), 이상 탐지(Anomaly Detection)를 이용하면 신뢰할 수 있는 협력 정보와 손상된 입력을 구분하는 데 도움이 된다. 복구 메커니즘은 우발적 고장과 적대적 교란(Adversarial Disturbance)을 모두 고려해야 한다.

감독 시스템 고장(Supervisory Failure)이 발생하는 동안에는 국소 자율성(Local Autonomy)이 필수적이다. 클라우드 서비스, 플릿 서버, 게이트웨이 또는 액세스 포인트(Access Point)를 사용할 수 없게 되더라도 주변 로봇은 안전을 유지하고 허용된 국소 행동을 계속 수행할 수 있는 충분한 온보드 지능(Onboard Intelligence)을 보유해야 한다. 감독 인프라는 임무 최적화와 모니터링을 제공할 수 있지만 즉각적인 충돌 회피, 기본적인 협력, 안전 상태 전환(Safe-State Transition)은 원격 연결에만 의존해서는 안 된다.

소프트웨어 고장(Software Fault)은 모듈형 아키텍처(Modular Architecture)를 통해 영향을 제한할 수 있다. 내비게이션, 작업 할당, 인식, 통신, 안전 기능을 서로 분리하면 하나의 구성요소 고장이 전체 로봇을 손상시키는 것을 방지할 수 있다. 감시 장치(Watchdog), 프로세스 재시작(Process Restart), 상태 모니터링, 폴백 제어기(Fallback Controller), 안전 운용 모드(Safe Operating Mode)를 통해 제한된 기능을 복원할 수 있다. 군집 수준의 복구는 이러한 로봇 수준 메커니즘을 대체하는 것이 아니라 보완한다.

복구 행동(Recovery Behavior)은 연쇄 고장(Cascading Failure)을 발생시키지 않아야 한다. 하나의 로봇이 고장 났을 때 작업을 지나치게 많이 재분배하면 주변 로봇에 과부하가 발생하고, 교통 혼잡이 증가하거나, 배터리가 빠르게 소모되거나, 통신 채널이 포화될 수 있다. 따라서 복구에는 부하 인식형 재할당(Load-Aware Reassignment)과 제한된 반응(Bounded Reaction)이 필요하다. 목표는 공격적인 보상으로 2차 고장을 만드는 것이 아니라 유용한 집단 기능을 안정적으로 복원하는 것이다.

공간적 위험(Spatial Risk) 역시 복구 과정에 영향을 준다. 고장 난 로봇이 통로, 교차로, 충전소 또는 작업 영역을 물리적으로 차단할 수 있다. 다른 로봇은 움직이지 않는 플랫폼을 장애물로 처리하고 작업 경로를 변경하거나 대형을 수정해야 할 수 있다. 일부 응용에서는 적절한 기능을 가진 로봇이 고장 난 로봇을 지원, 견인(Towing), 검사 또는 회수할 수도 있지만 이러한 행동은 임무 및 안전 로직에 명시적으로 포함되어야 한다.

적응형 역할 할당(Adaptive Role Allocation)을 통해 고장 허용성을 더욱 강화할 수 있다. 중요한 통신, 센싱 또는 협력 역할을 수행하는 로봇에는 지정된 백업(Backup)을 두거나 동적으로 대체 로봇을 선택할 수 있다. 역할은 에너지, 위치, 연결성, 상태에 따라 이동할 수 있다. 이를 통해 장기간의 전문화가 분산 군집을 소수의 필수 로봇에 은밀하게 의존하는 시스템으로 변화시키는 것을 방지할 수 있다.

성능 평가(Performance Evaluation)는 정상 상태의 효율성뿐 아니라 고장 발생 상태에서의 임무 완료 능력을 포함해야 한다. 유용한 지표에는 고장 탐지 시간(Detection Time), 격리 정확도(Isolation Accuracy), 오경보율(False Alarm Rate), 재할당 지연, 복구 시간, 연결성 유지, 작업 완료율, 커버리지 손실, 통신 오버헤드, 로봇 고장 증가에 따른 성능 저하 등이 포함된다. 또한 단일 고장뿐 아니라 동시 다발적 고장(Simultaneous Failure)과 상관 고장(Correlated Failure) 상황에서도 복구 품질을 평가해야 한다.

따라서 검증 과정에서는 고장 주입(Fault Injection)이 중요하다. 시뮬레이션과 실제 실험에서 의도적으로 로봇을 제거하거나 센서를 비활성화하고, 위치추정 성능을 저하시키거나, 패킷 손실을 발생시키고, 네트워크를 분할하거나, 배터리 용량을 줄이고, 액추에이터 고장을 발생시킬 수 있다. 시험에서는 서로 다른 임무 단계와 로봇 밀도에서의 고장을 평가해야 한다. 정상 조건에서만 높은 성능을 보이는 군집은 의미 있는 운용 복원력(Operational Resilience)을 입증했다고 볼 수 없다.

대규모 고장 허용(Large-Scale Fault Tolerance)은 가능한 경우 복구 메커니즘을 국소적으로 유지하는 데 달려 있다. 모든 고장이 완전한 전역 재계획(Global Replanning), 중앙집중식 진단, 네트워크 전체 동기화를 발생시킨다면 군집의 확장성 장점은 사라진다. 국소 탐지, 이웃 복구(Neighborhood Repair), 분산 재할당, 선택적 정보 전파를 이용하면 대부분의 장애를 지리적·연산적으로 제한하면서 상위 시스템에는 요약된 상태 정보만 전달할 수 있다.

산업용 배치(Industrial Deployment)에서는 분산 복구(Decentralized Recovery)와 감독 거버넌스(Supervisory Governance)를 결합하는 것이 유리하다. 국소 로봇은 고장을 탐지하고, 안전을 유지하며, 대형을 복구하고, 긴급 작업을 재할당할 수 있다. 동시에 플릿 또는 임무 계층(Fleet or Mission Layer)은 이벤트를 기록하고, 우선순위를 조정하며, 유지보수를 배정하고, 성능 저하 상태에서의 운용을 계속 허용할 것인지를 결정한다. 이러한 하이브리드 아키텍처(Hybrid Architecture)는 군집 복원력을 유지하면서 추적 가능성(Traceability)과 운영 제어를 제공한다.

궁극적으로 군집 로봇의 고장 허용(Fault Tolerance in Swarm Robots)은 중복성, 분산화(Decentralization), 국소 관측, 적응형 재할당, 점진적 성능 저하를 통해 형성된다. 군집은 개별 구성원이나 통신 링크의 사용 불가능 상태를 예외적인 사건으로 취급하기보다 언제든 발생할 수 있는 정상적인 운용 조건으로 예상해야 한다. 로봇 수준의 상태 관리(Robot-Level Health Management)와 집단 수준의 복구(Collective Recovery)를 결합하면 군집의 구성, 연결성, 사용 가능한 자원이 예상하지 못하게 변화하더라도 유용한 임무 수행 능력을 지속적으로 유지할 수 있다.

## 07.08 UAV Swarm Collision Avoidance Formation [w/Code]

![](images/image8.png){width="7.268055555555556in" height="7.268055555555556in"}

무인항공기 군집 충돌 회피 및 대형 제어(UAV Swarm Collision Avoidance and Formation Control)는 다수의 비행 로봇이 안전한 분리 거리, 임무 대형, 집단 이동을 유지하면서 3차원 공간에서 협력하도록 해야 한다. 지상 로봇과 달리 무인항공기(UAV)는 수평뿐 아니라 수직으로도 이동할 수 있어 추가적인 기동 자유도를 제공하지만 상호작용의 복잡성도 증가한다. 제어 시스템은 대형 목표와 충돌 위험, 비행체 동역학, 센싱 불확실성, 환경 제약 사이의 균형을 지속적으로 유지해야 한다.

UAV 군집은 원하는 상대 위치(Relative Position), 기체 간 거리(Inter-Vehicle Distance), 방위각(Bearing) 또는 그래프 관계(Graph Relationship)를 통해 대형의 기하 구조를 표현할 수 있다. 일반적인 구성에는 선형(Line), 종대(Column), V자형(V-Shaped), 원형(Circular), 그리드(Grid), 계층형(Layered), 3차원 격자 대형(Three-Dimensional Lattice Formation)이 포함된다. 적절한 기하 구조는 센싱 커버리지, 공기역학적 상호작용, 통신 범위, 임무 방향, 장애물 분포에 따라 달라진다. 따라서 대형 제어는 하나의 영구적인 형상을 가정하기보다 동적 재구성(Dynamic Reconfiguration)을 지원해야 한다.

충돌 회피(Collision Avoidance)는 정상적인 대형 정확도(Formation Accuracy)보다 높은 우선순위를 가져야 한다. 두 UAV가 안전하지 않은 분리 거리까지 접근하면 회피 제어기(Avoidance Controller)는 일시적으로 대형 명령을 무시하거나 수정해야 한다. 충돌 위험이 사라진 후 기체들은 점진적으로 원하는 상대 위치로 복귀할 수 있다. 이러한 우선순위 구조는 외란, 위치추정 오류 또는 예상하지 못한 기동이 발생했을 때 기하학적 대형 목표가 항공기를 위험한 궤적으로 강제하는 것을 방지한다.

안전 영역(Safety Region)은 일반적으로 각 UAV 주변에 정의되어 최소 허용 분리 거리(Minimum Allowable Separation)를 표현한다. 이러한 영역은 기체 크기, 속도, 제동 또는 감속 능력, 위치추정 불확실성(Localization Uncertainty), 통신 지연, 공기역학적 영향을 고려할 수 있다. 빠르게 이동하는 UAV는 정지 비행 중인 기체보다 전방에 더 큰 안전 여유가 필요할 수 있다. 따라서 안전 경계(Safety Envelope)는 단순한 고정 반경의 구 형태가 아니라 속도와 방향에 따라 달라질 수 있다.

퍼텐셜 필드 방법(Potential-Field Method)은 UAV 충돌 회피를 위한 직관적인 분산 메커니즘을 제공한다. 주변 UAV와의 분리 거리가 지나치게 작아지면 반발 효과(Repulsive Effect)가 발생하고, 대형 목표 또는 임무 목표는 인력 효과(Attractive Effect)를 생성한다. 장애물 역시 추가적인 반발장을 형성할 수 있다. 결과 벡터는 각 기체가 대략적인 대형을 유지하면서 안전한 방향으로 이동하도록 유도하지만, 필드가 적절하게 설계되지 않으면 국소 최소점(Local Minimum), 진동(Oscillation), 상충하는 제어 명령이 발생할 수 있다.

속도 장애물 방법(Velocity-Obstacle Method)은 미래에 발생할 수 있는 충돌 가능성을 직접적으로 판단한다. 두 UAV 사이의 상대 위치와 상대 속도를 이용하여 특정 예측 시간(Prediction Horizon) 안에 충돌을 발생시키는 속도 집합을 정의한다. 기체는 이러한 위험 영역 밖에 있으면서 원하는 대형 속도에 가능한 한 가까운 속도를 선택한다. 상호적 방식(Reciprocal Formulation)을 사용하면 하나의 기체만 회피하는 것이 아니라 두 UAV가 충돌 회피 책임을 분담할 수 있다.

최적 상호 충돌 회피(Optimal Reciprocal Collision Avoidance, ORCA)는 이러한 원리를 여러 기체가 상호작용하는 환경으로 확장할 수 있다. 각 UAV는 주변 에이전트가 생성하는 속도 제약(Velocity Constraint)을 고려하고 예측된 충돌을 피할 수 있는 실행 가능한 움직임을 선택한다. 이 방식은 중간 수준의 밀도를 가진 군집에서 부드러운 분산 행동을 제공할 수 있지만, 실제 UAV에 적용할 때는 순간적인 속도 변경을 가정하기보다 가속도 제한, 비행 동역학, 센싱 오차, 지연된 이웃 정보를 고려해야 한다.

모델 예측 제어(Model Predictive Control, MPC)는 UAV 동역학과 미래 움직임을 보다 명시적으로 고려하는 방법을 제공한다. 각 기체는 유한한 예측 구간(Finite Horizon)에서 자신의 궤적을 예측하고 대형, 충돌, 속도, 가속도, 환경 제약을 만족하면서 제어 입력을 최적화한다. 분산 모델 예측 제어(Distributed Model Predictive Control, DMPC)를 사용하면 각 UAV가 주변 기체의 예측 궤적을 이용하여 국소 최적화 문제를 해결할 수 있으므로 하나의 중앙집중식 궤적 최적화기에 대한 의존성을 줄일 수 있다.

예측 제어의 계산 비용은 주변 UAV의 수와 제약조건이 증가할수록 커진다. 따라서 확장 가능한 군집은 전체 구성원을 모두 고려하기보다 관련된 국소 이웃(Local Neighbor)으로 최적화 범위를 제한해야 한다. 이웃 선택은 거리, 예상 충돌 확률, 통신 토폴로지 또는 대형 관계를 기반으로 수행할 수 있다. 이를 통해 전체 군집이 매우 많은 기체로 구성되더라도 각 UAV의 국소 계산 복잡도를 제한할 수 있다.

제어 장벽 함수(Control Barrier Function, CBF)는 안전 제약을 강제하기 위한 또 다른 메커니즘을 제공한다. 장벽 함수는 최소 분리 거리 또는 장애물 여유 거리로 정의된 안전 집합(Safe Set)을 나타내며, 시스템이 해당 안전 집합 내부에 유지되도록 필요한 경우 정상적인 대형 명령을 수정한다. 이를 통해 성능 제어(Performance Control)와 안전 제어(Safety Control)를 효과적으로 분리할 수 있다. 대형 제어기가 선호하는 움직임을 생성하면 안전 계층이 충돌 없는 운용을 유지하기 위해 필요한 최소한의 수정만 적용한다.

대형 제어(Formation Control) 자체에는 리더-팔로워(Leader-Follower), 가상 구조(Virtual Structure), 합의(Consensus), 행동 기반(Behavior-Based), 그래프 기반(Graph-Based) 방법을 사용할 수 있다. 리더-팔로워 제어에서는 선택된 UAV가 이동 기준을 제공하고 팔로워가 상대적 오프셋을 유지한다. 가상 구조 방식은 전체 대형을 하나의 기하학적 객체로 취급한다. 합의 방식은 국소 정보 교환을 통해 위치, 속도 또는 진행 방향을 조정하고, 그래프 기반 방법은 유지해야 하는 상대적 관계를 명시적으로 정의한다.

리더 기반 UAV 대형(Leader-Based UAV Formation)은 임무 유도를 단순화하지만 리더가 고장 나거나 통신을 잃을 경우 잠재적인 취약성을 발생시킨다. 다중 리더 아키텍처(Multi-Leader Architecture), 가상 리더(Virtual Leader), 분산 리더 선출(Distributed Leader Election)을 이용하면 복원력을 향상시킬 수 있다. 무리더 합의(Leaderless Consensus)는 특정 기체에 대한 의존성을 더욱 줄이고 주변 상호작용을 통해 집단 이동 방향이 형성되도록 할 수 있다. 적절한 아키텍처는 임무의 예측 가능성, 통신 신뢰성, 요구되는 대형 정밀도에 따라 결정된다.

3차원 대형 제어(Three-Dimensional Formation Control)는 고도(Altitude)를 추가적인 협력 변수로 사용한다. UAV는 2차원 움직임만으로 해결하기 어려운 충돌을 수직 분리(Vertical Separation)를 이용하여 해결할 수 있다. 임시 고도 계층(Temporary Altitude Layer)을 이용하면 기체들이 안전하게 교차한 뒤 원래의 대형 고도로 복귀할 수 있다. 그러나 제한 없는 수직 회피는 에너지 소비를 증가시키고 센싱 목표를 방해하거나 고도 제약을 위반할 수 있으므로 수직 기동 역시 임무를 고려해야 한다.

대형 전환(Formation Transition)에서는 특별한 충돌 관리가 필요하다. 선형에서 그리드, 원형 또는 조밀한 3차원 배열로 변경하는 과정에서는 초기 대형과 최종 대형이 모두 안전하더라도 UAV의 이동 궤적이 서로 교차할 수 있다. 따라서 전환 계획(Transition Planning)은 목표 위치뿐 아니라 중간 궤적(Intermediate Trajectory)까지 고려해야 한다. 할당 알고리즘은 궤적 교차, 이동 거리, 충돌 가능성을 최소화하는 방식으로 UAV와 새로운 대형 슬롯(Formation Slot)을 연결할 수 있다.

장애물 회피(Obstacle Avoidance)는 대형 유지와 함께 조정되어야 한다. 건물, 나무, 산업 구조물, 지형 또는 이동 물체로 인해 군집의 변형이 필요할 수 있다. 좁은 공간에서는 강체 대형(Rigid Formation)을 유지하는 것이 불가능할 수 있다. 군집은 간격을 축소하거나 토폴로지를 변경하고, 일시적으로 여러 하위 그룹으로 분리하거나, 서로 다른 장애물 우회 경로를 따라 이동한 후 다시 병합할 수 있다. 따라서 복잡한 환경에서 운용하려면 대형의 유연성(Formation Flexibility)이 필수적이다.

충돌 회피를 위한 센싱(Sensing)은 위성항법시스템(GNSS), 관성측정장치(Inertial Measurement Unit, IMU), 카메라, 라이다(LiDAR), 레이더(Radar), 초광대역 거리 측정(Ultra-Wideband Ranging, UWB), UAV 간 상대 위치추정(Inter-UAV Relative Localization)을 결합할 수 있다. 하나의 센서가 모든 환경에서 항상 신뢰할 수 있는 것은 아니다. GNSS는 구조물 주변에서 성능이 저하될 수 있고, 카메라는 가시성에 영향을 받으며, 무선 거리 측정은 간섭을 받을 수 있다. 다중 센서 융합(Multi-Sensor Fusion)은 보다 강건한 상대 상태 추정을 제공하고 단일 센서 고장이 군집의 안전을 위협할 가능성을 줄인다.

상대 위치추정(Relative Localization)은 충돌 회피가 주변 UAV의 위치와 움직임에 직접적으로 의존하기 때문에 특히 중요하다. 절대 전역 위치추정(Global Localization)에 수 센티미터 이상의 오차가 존재하더라도 정확한 상대 거리 및 방위 측정을 통해 안전한 간격을 유지할 수 있다. 전역 항법 기준(Global Navigation Reference)과 국소 상대 센싱(Local Relative Sensing)을 결합하면 군집은 임무 수준의 위치 정확도를 유지하면서 내부 대형의 기하학적 일관성을 더욱 정밀하게 유지할 수 있다.

통신(Communication)은 위치, 속도, 계획된 움직임, 대형 상태, 기동 의도(Intent)를 공유하여 대형 협력을 지원한다. 각 UAV는 주로 주변 기체와 관련된 대형 이웃의 정보만 필요하므로 국소 방송(Local Broadcast)은 전대전 통신(All-to-All Communication)보다 일반적으로 확장성이 높다. 메시지 전송률은 비행 동역학을 반영해야 하며, 타임스탬프와 시퀀스 번호(Sequence Number)를 이용하면 현재 상태와 지연되거나 중복된 패킷을 구분할 수 있다.

충돌 회피는 통신에만 의존해서는 안 된다. 패킷 손실(Packet Loss), 간섭, 네트워크 분할(Network Partition), 메시지 지연으로 인해 중요한 순간에 주변 기체의 상태 정보를 사용할 수 없을 수 있다. UAV는 통신 품질이 저하되더라도 최소 안전성을 유지할 수 있도록 온보드 센싱(Onboard Sensing)과 국소 회피(Local Avoidance) 능력을 보유해야 한다. 네트워크 정보는 예측과 협력을 향상시킬 수 있지만 즉각적인 물리적 안전은 국소적으로 보장할 수 있어야 한다.

통신 지연(Communication Delay)은 안전 여유(Safety Margin)에 포함되어야 한다. 수백 밀리초 전에 수신한 주변 기체의 위치는 빠르게 움직이는 군집의 현재 기하 구조를 더 이상 정확하게 나타내지 못할 수 있다. 제어기는 속도 및 가속도 추정값을 이용하여 이웃 상태를 외삽(Extrapolation)할 수 있으며, 정보가 오래될수록 안전 경계를 확대할 수 있다. 지나치게 오래된 정보(Stale Information)는 현재 움직임을 정확하게 표현한다고 가정하지 말고 일정 시간이 지나면 폐기해야 한다.

바람과 공기역학적 외란(Aerodynamic Disturbance)은 공중 군집에 특화된 문제를 발생시킨다. 돌풍(Gust)은 UAV를 원하는 대형 위치에서 벗어나게 하고 예상하지 못한 접근 속도(Closing Velocity)를 만들 수 있다. 주변 로터의 다운워시(Downwash) 역시 기체가 지나치게 가깝거나 부적절한 수직 오프셋으로 비행할 때 안정성에 영향을 줄 수 있다. 따라서 대형 간격은 단순한 기하학적 충돌 거리뿐 아니라 공기역학적 상호작용과 환경 외란 수준도 반영해야 한다.

에너지 소비(Energy Consumption)는 대형 및 회피 의사결정에 영향을 준다. 반복적인 가속, 감속, 상승, 횡방향 기동은 비행 지속시간을 감소시킬 수 있다. 따라서 여러 개의 안전한 대안이 존재한다면 충돌 회피 알고리즘은 부드럽고 최소한의 움직임만 필요한 궤적을 선호해야 한다. 또한 대형 기하 구조를 이용하여 공기역학적 또는 센싱 책임을 분산하고, 에너지 소비가 큰 위치를 특정 UAV에 영구적으로 할당하지 않고 순환시킬 수 있다.

이기종 UAV 군집(Heterogeneous UAV Swarm)에는 능력을 고려한 대형 규칙(Capability-Aware Formation Rule)이 필요하다. 기체마다 크기, 최대 속도, 가속도, 비행 지속시간, 센싱 범위, 탑재 중량, 기동성이 다를 수 있다. 따라서 모든 기체에 동일한 최소 분리 거리나 제어 게인을 적용하는 것은 적절하지 않을 수 있다. 크거나 기동성이 낮은 UAV에는 더 큰 안전 여유가 필요하며, 빠른 기체는 신속한 재구성이 필요한 위치에 배치할 수 있다. 대형 역할(Formation Role)은 이러한 차이를 반영해야 한다.

고장 허용(Fault Tolerance)은 하나의 UAV 고장이 주변 기체에 빠르게 영향을 미칠 수 있기 때문에 필수적이다. 추진계, 위치추정, 통신 또는 배터리 문제가 발생한 기체는 가능한 경우 성능 저하 상태(Degraded Capability)를 알리고 안전한 궤적으로 대형에서 이탈해야 한다. 주변 UAV는 간격을 확대하고, 대형 그래프(Formation Graph)를 복구하며, 위치를 재분배하거나 대체 역할을 선출할 수 있다. 고장 난 기체가 제어되지 않는 충돌 위험 요소가 되어서는 안 된다.

비상 행동(Emergency Behavior)은 정상적인 군집 목표보다 결정론적으로 높은 우선순위를 가져야 한다. 제어 상실, 심각한 배터리 부족, 높은 위치추정 불확실성 또는 임박한 충돌이 발생하면 환경과 기체 상태에 따라 정지 비행(Hover), 제어된 하강(Controlled Descent), 자동 복귀(Return-to-Home), 비상 분리(Emergency Separation), 착륙(Landing)을 수행할 수 있다. 주변 UAV는 이러한 비상 상태를 인식하고 정상적인 대형 관계를 계속 강제하는 대신 안전 공간을 확보해야 한다.

고밀도 군집(Dense Swarm)은 신중한 확장성 분석(Scalability Analysis)이 필요하다. 국소 기체 밀도가 증가하면 각 UAV가 동시에 여러 충돌 제약을 받게 되어 실행 가능한 움직임을 찾기 어려워질 수 있다. 지나치게 조밀한 대형에서는 진동, 교착 상태(Deadlock), 연쇄적인 회피 기동(Cascading Avoidance Maneuver)이 발생할 수 있다. 최소 간격, 국소 밀도 제한(Local Density Limit), 적응형 대형 확장(Adaptive Formation Expansion), 교통 흐름과 유사한 방향 규칙을 적용하면 군집이 위험한 기하 상태에 도달하기 전에 기동성을 유지할 수 있다.

성능 평가(Performance Evaluation)는 대형 품질과 안전성을 모두 측정해야 한다. 유용한 지표에는 최소 UAV 간 거리, 충돌 또는 근접 충돌(Near-Collision) 횟수, 대형 오차, 수렴 시간, 궤적 부드러움(Trajectory Smoothness), 회피 기동 빈도, 에너지 소비, 통신 오버헤드, 외란 이후 복구 시간이 포함된다. 충분한 안전 여유 없이 달성한 높은 대형 정확도는 의미가 없으므로 대형 정확도만을 단독으로 평가해서는 안 된다.

검증(Validation)은 정상적인 시뮬레이션 조건을 넘어 다양한 비정상 조건을 포함해야 한다. 바람 외란, GNSS 성능 저하, 센서 잡음, 통신 지연, 패킷 손실, 이동 장애물, UAV 고장, 급격한 대형 전환, 고밀도 교통 상황을 체계적으로 적용해야 한다. 몬테카를로 시뮬레이션(Monte Carlo Simulation)을 통해 드물게 발생하는 상호작용을 발견할 수 있으며, 하드웨어 인 더 루프(Hardware-in-the-Loop)와 단계적으로 규모를 확대하는 실제 비행 시험을 통해 실제 기체 동역학 및 통신 환경에서도 가정이 유효한지 검증할 수 있다.

계층형 아키텍처(Layered Architecture)는 UAV 군집에 특히 적합하다. 임무 계획(Mission Planning)은 집단 목표를 정의하고, 대형 제어는 원하는 상대적 기하 구조를 결정하며, 궤적 생성(Trajectory Generation)은 동역학적으로 실행 가능한 움직임을 생성한다. 안전 계층(Safety Layer)은 충돌 및 장애물 제약을 강제하고, 저수준 비행 제어기(Low-Level Flight Controller)는 개별 기체를 안정화한다. 이러한 책임을 분리하면 상위 수준의 군집 알고리즘이 기본적인 비행 안전성을 직접적으로 손상시키는 것을 방지할 수 있다.

감독 시스템(Supervisory System)은 각 UAV를 지속적으로 직접 제어하지 않으면서 운영 경계를 설정할 수 있다. 지오펜스(Geofence), 고도 제한, 최소 분리 거리, 허용 대형 유형, 비상 절차, 임무 우선순위를 중앙에서 정의하고 세부적인 협력은 국소 UAV 제어기가 결정할 수 있다. 이러한 하이브리드 구조(Hybrid Structure)는 분산형 반응성과 예측 가능한 운영 거버넌스를 결합하며 감독 시스템과의 연결이 일시적으로 끊기더라도 국소 안전 행동을 지속할 수 있도록 한다.

궁극적으로 UAV 군집 충돌 회피 및 대형 제어(UAV Swarm Collision Avoidance and Formation Control)는 대형 목표와 안전 제약이 서로 경쟁하는 명령이 아니라 상호 보완적인 계층으로 동작하도록 설계해야 한다. 국소 센싱, 예측형 충돌 회피(Predictive Collision Avoidance), 분산 대형 제어, 통신, 동적 재구성, 고장 복구를 결합하면 다수의 항공기가 3차원 공간에서 일관된 집단으로 이동할 수 있다. 이를 통해 군집은 유용한 집단 기하 구조를 유지하면서도 안전한 분리 거리와 임무 연속성(Mission Continuity)을 보장하도록 지속적으로 움직임을 적응시킬 수 있다.

## 07.09 Swarm Simulation ARGoS Buzz Platform [w/Code]

![](images/image9.png){width="7.268055555555556in" height="7.268055555555556in"}

군집 로보틱스 시뮬레이션(Swarm Robotics Simulation)은 알고리즘을 실제 로봇에 배포하기 전에 집단 행동(Collective Behavior)을 개발하고 검증할 수 있는 통제된 환경을 제공한다. 군집의 성능은 다수 에이전트 사이의 상호작용에서 출현하므로 한두 대의 로봇만 평가하는 것으로는 충분하지 않다. 시뮬레이션을 이용하면 대규모 실제 플릿을 운용하는 비용과 위험 없이 로봇 수를 증가시키고, 환경을 변경하며, 통신 제약을 적용하고, 고장을 주입하며, 재현 가능한 조건에서 실험을 반복할 수 있다.

ARGoS는 대규모 로봇 실험을 위해 특별히 설계된 다중 로봇 시뮬레이터(Multi-Robot Simulator)이다. 아키텍처는 계산 효율성(Computational Efficiency), 모듈성(Modularity), 확장성(Scalability)을 중점적으로 고려하며, 모델의 복잡성과 사용 가능한 컴퓨팅 자원에 따라 수백 대에서 잠재적으로 수천 대 규모의 로봇을 포함하는 시뮬레이션을 수행할 수 있다. 모든 구성요소의 물리적 현실성을 최대화하는 대신 실험 목적에 따라 서로 다른 추상화 수준(Level of Abstraction)을 선택할 수 있도록 한다.

시뮬레이터는 로봇 엔티티(Robot Entity), 제어기(Controller), 센서, 액추에이터, 물리 엔진(Physics Engine), 시각화 구성요소(Visualization Component), 환경 객체(Environmental Object)를 통해 실험을 구성한다. 로봇 제어기는 실제 로봇 시스템과 유사한 반복 루프에서 시뮬레이션된 센서 정보를 수신하고 액추에이터 명령을 생성한다. 이러한 분리를 통해 다수의 시뮬레이터 내부 구성요소와 독립적으로 집단 알고리즘을 개발할 수 있으며 이후 실제 로봇 제어기로 이전하는 것도 지원할 수 있다.

ARGoS의 주요 특징 중 하나는 모듈형 물리 아키텍처(Modular Physics Architecture)이다. 전체 실험에 하나의 계산 비용이 높은 모델을 강제하는 대신 서로 다른 영역이나 로봇 유형에 적절한 물리 엔진을 사용할 수 있다. 상위 수준의 군집 협력에는 단순한 운동 모델(Motion Model)만으로 충분할 수 있으며, 물리적 상호작용이 중요한 부분에는 보다 상세한 동역학을 적용할 수 있다. 이를 통해 실험 요구조건에 따라 필요한 부분에 시뮬레이션 충실도(Simulation Fidelity)를 배분할 수 있다.

ARGoS는 플러그인(Plugin)을 통해 근접 센싱(Proximity Sensing), 거리 및 방위 통신(Range-and-Bearing Communication), 위치 측정(Positioning), 카메라, 광 센싱(Light Sensing), 기타 로봇별 인터페이스와 같은 일반적인 로봇 센싱 개념을 지원한다. 액추에이터 인터페이스 역시 휠, LED, 그리퍼, 통신 장치 또는 기타 메커니즘을 표현할 수 있다. 플러그인 아키텍처(Plugin Architecture)를 통해 기존 모델만으로 충분하지 않을 경우 사용자 정의 로봇 모델, 센서, 액추에이터, 제어 구성요소를 확장할 수 있다.

군집 행동은 로봇 수가 증가함에 따라 변화할 수 있기 때문에 확장성(Scalability)이 특히 중요하다. 10대의 로봇에서 정상적으로 동작하는 알고리즘이 수백 대 규모에서는 혼잡, 통신 과부하, 진동, 작업 중복을 발생시킬 수 있다. ARGoS에서는 로봇 수를 단계적으로 증가시키면서 작업 완료 시간, 커버리지, 통신 활동, 공간 분포, 충돌, 집단 수렴(Collective Convergence)과 같은 정량적 데이터를 수집할 수 있다.

Buzz는 로봇 군집을 위해 설계된 프로그래밍 언어 및 런타임(Programming Language and Runtime)을 제공함으로써 군집 시뮬레이션을 보완한다. 각 플랫폼에 별도의 저수준 협력 로직을 작성하는 대신 Buzz는 집단 행동을 직접 표현하기 위한 추상화(Abstraction)를 제공한다. 프로그램은 개별 에이전트에서 분산 실행(Decentralized Execution)을 유지하면서 로봇이 정보를 교환하고, 그룹을 구성하며, 공유 지식을 관리하고, 국소 행동을 수행하는 방식을 기술한다.

Buzz의 기본적인 추상화 중 하나는 가상 스티그머지(Virtual Stigmergy)이다. 가상 스티그머지는 로봇이 간접적으로 정보를 공유할 수 있는 분산 키-값 구조(Distributed Key-Value Structure)를 제공한다. 로봇은 특정 키와 연결된 값을 기록할 수 있으며 다른 로봇은 국소 통신을 통해 해당 정보를 수신하고 전파한다. 충돌 해결 메커니즘(Conflict Resolution Mechanism)은 서로 다른 값이 어떻게 조정될지를 결정하며, 지속적으로 사용 가능한 중앙 데이터베이스 없이 분산 공유 상태(Distributed Shared State)를 구현할 수 있도록 한다.

가상 스티그머지는 분산 작업 정보, 발견된 목표, 환경 관측, 임무 상태 또는 집단 추정값(Collective Estimate)을 공유하는 데 유용하다. 정보는 로봇 간 상호작용을 통해 전파되므로 각 로봇은 일시적으로 공유 상태에 대해 서로 다른 정보를 보유할 수 있다. 따라서 알고리즘은 즉각적인 일관성(Instantaneous Consistency)이 아니라 최종적 일관성(Eventual Consistency)을 허용해야 한다. 이러한 특성은 통신이 국소적이고 지연되며 간헐적이고 불완전한 실제 군집 네트워크의 특성을 반영한다.

Buzz는 로봇을 동적으로 논리 그룹(Logical Group)으로 구성할 수 있는 군집 추상화(Swarm Abstraction)도 제공한다. 로봇은 국소 조건, 능력, 작업 할당, 공간적 위치 또는 임무 단계에 따라 특정 군집에 참여하거나 이탈할 수 있다. 이후 전체 로봇 집단이 아니라 선택된 그룹에 특정 행동을 적용할 수 있다. 중첩되거나 서로 겹치는 논리적 구성(Nested or Overlapping Logical Organization)을 이용하면 중앙집중식 그룹 관리자 없이도 복잡한 집단 행동을 표현할 수 있다.

이웃 상호작용(Neighbor Interaction) 역시 핵심 개념이다. 로봇은 주변 피어(Peer)에 관한 정보에 접근하고 국소 이웃 상태(Local Neighborhood State)를 기반으로 연산을 수행할 수 있다. 따라서 대형 형성(Formation), 플로킹(Flocking), 충돌 회피, 합의(Consensus), 분산 작업 할당(Distributed Task Allocation)을 실제 군집에서 사용되는 것과 동일한 국소 상호작용 원리를 이용하여 표현할 수 있다. 전역 행동(Global Behavior)은 전역 궤적 계산을 통해 생성되는 것이 아니라 개별 로봇이 이러한 규칙을 반복적으로 실행하면서 출현한다.

ARGoS와 Buzz를 결합하면 시뮬레이션 환경과 군집 행동 기술(Swarm Behavior Description)을 분리할 수 있다. ARGoS는 로봇, 물리 모델, 센싱, 액추에이션, 통신 모델, 환경을 제공하고 Buzz는 분산형 집단 로직(Decentralized Collective Logic)을 표현한다. 이러한 분리는 개념적 알고리즘을 다시 설계하지 않고도 서로 다른 환경 구성, 로봇 수, 통신 조건, 고장 시나리오에서 동일한 군집 행동을 평가할 수 있다는 점에서 유용하다.

일반적인 실험은 환경, 로봇 유형, 로봇 수, 초기 분포, 제어기, 센서, 통신 매개변수, 실험 시간을 정의하는 것에서 시작한다. 로봇은 무작위 또는 사전에 정의된 배열에 따라 배치할 수 있다. 이후 시뮬레이션은 반복적인 센싱, 제어, 통신, 이동 주기를 실행하면서 관련 지표를 기록한다. 서로 다른 난수 시드(Random Seed)를 사용하는 여러 번의 실험을 통해 일관된 집단 행동과 우연히 발생한 결과를 구분할 수 있다.

통신 모델링(Communication Modeling)은 군집 시뮬레이션에서 매우 중요하다. 완벽한 전역 통신(Global Communication)을 가정하면 실제 로봇에 적용하는 순간 실패하는 알고리즘이 만들어질 수 있다. 따라서 통신 거리, 패킷 손실(Packet Loss), 간섭, 지연, 대역폭 제한, 이웃 관계 변화를 적절한 수준으로 표현해야 한다. 국소 거리 및 방위 통신(Local Range-and-Bearing Communication)은 중앙집중식 네트워크가 아니라 주변 피어와의 상호작용을 기반으로 설계된 알고리즘을 평가하는 데 특히 유용하다.

시뮬레이션에는 센서 및 위치추정 불확실성(Sensor and Localization Uncertainty)도 포함해야 한다. 완벽한 위치 측정, 정확한 장애물 탐지, 잡음 없는 거리 측정은 대형 또는 협력 알고리즘의 약점을 숨길 수 있다. 잡음 모델(Noise Model), 제한된 센싱 범위, 가림(Occlusion), 위치추정 드리프트(Localization Drift), 지연된 관측을 적용하면 실제 배포 전에 알고리즘의 민감도를 확인할 수 있다. 필요한 현실성의 수준은 실험이 개념적인 군집 행동을 평가하는지 또는 실제 구현 준비 수준을 평가하는지에 따라 달라진다.

고장 주입(Fault Injection)은 시뮬레이션이 제공하는 또 다른 주요 장점이다. 개별 로봇을 비활성화하고, 통신 링크를 제거하며, 센서 성능을 저하시키거나, 배터리 고갈을 모사하고, 제어기에 의도적인 교란을 적용할 수 있다. 이후 작업이 재할당되는지, 대형이 복구되는지, 커버리지가 허용 가능한 수준으로 유지되는지, 통신 그래프가 다시 연결되는지를 관찰할 수 있다. 실제 로봇보다 훨씬 안전하고 빠르게 많은 고장 시나리오를 평가할 수 있다.

군집 실험에서는 개별 지표(Individual Metric)와 집단 지표(Collective Metric)를 모두 평가해야 한다. 개별 지표에는 이동 거리, 에너지 추정값, 통신 부하, 수행 작업 수, 유휴 시간이 포함될 수 있다. 집단 지표에는 임무 완료 시간, 커버리지 비율, 수렴도, 처리량(Throughput), 연결성, 공간적 균일도, 충돌 빈도, 고장에 대한 복원력(Resilience)이 포함될 수 있다. 가장 유용한 측정 지표는 연구하는 집단 행동에 따라 달라진다.

시각화(Visualization)는 수치 지표만으로 해석하기 어려운 창발 행동(Emergent Behavior)을 개발자가 이해하도록 돕는다. 로봇 궤적, 대형 구조, 작업 영역, 통신 링크, 가상 페로몬 값(Virtual Pheromone Value), 목표 상태 등을 시각화하면 군집화, 교착 상태(Deadlock), 진동, 비효율적인 이동을 발견할 수 있다. 그러나 겉으로 보기에 잘 조직된 움직임도 실제 임무 지표에서는 낮은 성능을 나타낼 수 있으므로 시각적 검사는 정량적 평가를 대체하는 것이 아니라 보완해야 한다.

대규모 실험에서는 실시간 시각화 없이 헤드리스 실행(Headless Execution)을 사용하는 경우가 많다. 그래픽 렌더링을 제거하면 컴퓨팅 자원을 물리 모델과 제어기 실행에 집중할 수 있으며 다수의 실험을 자동으로 수행할 수 있다. 매개변수 스윕(Parameter Sweep)을 통해 로봇 수, 통신 반경, 제어 게인(Control Gain), 고장률, 환경 밀도를 변화시킬 수 있다. 이후 반복 실험 결과를 통계적으로 비교함으로써 시각적으로 성공한 하나의 데모에 의존하는 것을 피할 수 있다.

재현성(Reproducibility)을 확보하려면 구성 파일, 제어기 버전, 난수 시드, 시뮬레이터 버전, 로봇 모델, 실험 매개변수를 신중하게 관리해야 한다. 통신 거리나 초기 분포의 작은 변화만으로도 창발적인 군집 행동이 크게 달라질 수 있다. 따라서 실험 결과를 재현할 수 있도록 충분한 메타데이터(Metadata)를 기록해야 한다. 자동화된 실험 스크립트는 구성 생성, 시뮬레이션 실행, 로그 수집, 성능 요약을 일관된 방식으로 수행할 수 있다.

시뮬레이션 충실도(Simulation Fidelity)는 처음부터 최대화하기보다 점진적으로 증가시켜야 한다. 초기 알고리즘 개발에서는 단순화된 운동학(Simplified Kinematics)과 이상적인 센싱을 사용하여 기본적인 집단 로직을 빠르게 평가할 수 있다. 이후 통신 손실, 위치추정 오차, 현실적인 동역학, 센서 잡음, 에너지 제약, 환경 복잡도를 단계적으로 추가할 수 있다. 이러한 단계적 접근법(Staged Approach)은 군집 알고리즘 자체가 안정화되기 전에 물리적 세부사항에 과도한 계산 자원을 사용하는 것을 방지한다.

시뮬레이션과 현실 사이의 격차(Simulation-to-Reality Gap)는 여전히 중요한 문제이다. 실제 로봇은 휠 슬립(Wheel Slip), 공기역학적 외란, 센서 보정 오차, 프로세서 타이밍 변화, 무선 간섭, 기계적 공차, 예상하지 못한 환경 조건을 경험하며 시뮬레이션이 이를 완전히 표현하지 못할 수 있다. 따라서 정확한 타이밍이나 완벽한 측정에 의존하는 알고리즘은 위험하다. 강건한 군집 제어(Robust Swarm Control)는 시뮬레이션 궤적을 정확하게 재현하려 하기보다 불확실성을 허용하도록 설계해야 한다.

하드웨어 인 더 루프 시험(Hardware-in-the-Loop Testing)은 시뮬레이션된 군집 구성원과 실제 제어기, 컴퓨터, 통신 장치 또는 물리적 로봇을 결합하여 이러한 격차를 줄일 수 있다. 소수의 실제 로봇이 시뮬레이션 에이전트와 상호작용하도록 구성하면 전체 군집이 준비되기 전에 소프트웨어 및 네트워크 동작을 평가할 수 있다. 순수 시뮬레이션에서 혼합 실험(Mixed Experiment), 최종적으로 실제 로봇 배포로 단계적으로 전환하면 통합 위험(Integration Risk)을 줄일 수 있다.

가능한 경우 실제 로봇 인터페이스(Real Robot Interface)는 시뮬레이션과 유사한 제어기 추상화를 유지해야 한다. 센서 관측, 이웃 정보, 액추에이터 명령, 군집 통신이 일관된 인터페이스를 사용하면 시뮬레이션에서 개발한 행동을 구조적으로 크게 변경하지 않고 이전할 수 있다. 플랫폼별 적응(Platform-Specific Adaptation)은 집단 알고리즘 전체에 포함시키기보다 하드웨어 드라이버와 미들웨어(Middleware)에 제한할 수 있다.

ARGoS와 Buzz는 개발자가 전역 지식(Global Knowledge)을 가정하기보다 국소 정보(Local Information)를 기반으로 사고하도록 유도하기 때문에 분산 시스템 연구에 특히 유용하다. 각 로봇은 자신의 센서, 이웃 통신, 국소 메모리, 분산 공유 정보를 기반으로 의사결정을 수행해야 한다. 필요한 경우 감독 정보(Supervisory Information)를 추가할 수 있지만, 중앙 인프라를 사용할 수 없게 되었을 때 어떤 일이 발생하는지도 시뮬레이션에서 명시적으로 시험할 수 있다.

이기종 군집 실험(Heterogeneous Swarm Experiment)은 서로 다른 센서, 이동 특성, 통신 범위 또는 능력을 가진 여러 로봇 유형을 표현할 수 있다. Buzz의 논리 그룹은 기능에 따라 이러한 로봇을 구성할 수 있으며, ARGoS는 각각의 물리적 행동을 모델링한다. 이를 통해 공중 정찰 로봇(Aerial Scout), 지상 로봇, 중계 에이전트(Relay Agent), 특수 센싱 장치가 효과적으로 협력하는지와 특정 능력이 손실되었을 때도 전체 집단이 정상적으로 기능하는지를 평가할 수 있다.

시나리오 복잡도(Scenario Complexity)는 군집 시스템의 성숙도와 함께 증가시켜야 한다. 초기 시험에서는 개방된 환경과 정적 목표를 사용할 수 있으며, 이후 장애물, 좁은 통로, 동적 목표, 통신 음영 지역(Communication Shadow), 이동 위험 요소, 부분 고장을 추가할 수 있다. 최종 검증 시나리오에서는 각각의 문제를 독립적으로 시험하기보다 여러 외란을 동시에 결합해야 한다. 집단 시스템은 개별적으로는 처리 가능한 여러 문제가 예상하지 못한 방식으로 상호작용할 때 실패하는 경우가 많다.

성능 확장(Performance Scaling)은 소규모 실험에서 실제 운용 규모의 군집으로 로봇 수를 증가시키면서 측정해야 한다. 이상적으로는 로봇을 추가할수록 임무 성능이 크게 향상되면서 각 로봇의 연산량과 통신량은 제한된 수준을 유지해야 한다. 그러나 일정 규모 이후에는 혼잡이나 자원 경쟁(Resource Contention)으로 인해 수익 체감(Diminishing Returns)이 발생할 수 있다. 시뮬레이션은 이러한 포화 지점(Saturation Point)을 식별하고 서로 다른 로봇 밀도에 맞춰 협력 규칙을 조정해야 하는지를 판단하는 데 도움을 준다.

ARGoS와 Buzz는 실제 검증을 대체하는 도구가 아니라 더 넓은 군집 엔지니어링 워크플로(Swarm Engineering Workflow)의 구성요소로 이해해야 한다. 시뮬레이션은 빠른 알고리즘 개발, 통제된 실험, 확장성 연구, 고장 주입, 통계적 평가를 지원한다. 실제 시험은 센싱, 통신, 동역학, 타이밍, 안전, 환경에 대한 가정을 검증한다. 가장 강력한 개발 과정은 시뮬레이션 결과와 실제 환경에서 얻은 관측을 반복적으로 상호 반영하는 방식이다.

성숙한 군집 시뮬레이션 플랫폼(Swarm Simulation Platform)은 행동 설계, 실험 자동화, 정량적 평가, 실제 배포 준비를 하나의 과정으로 연결한다. ARGoS는 확장 가능한 다중 로봇 환경을 제공하고 Buzz는 이웃 상호작용, 논리 그룹, 가상 스티그머지와 같은 군집 지향 추상화(Swarm-Oriented Abstraction)를 제공한다. 두 기술을 결합하면 비용이 높은 대규모 실제 로봇 실험을 수행하기 전에 다양한 로봇 수, 네트워크 조건, 환경 복잡도, 고장 시나리오에서 분산 알고리즘을 체계적으로 평가할 수 있다.

## 07.10 Industrial Swarm Robotics Use Case Analysis

![](images/image10.png){width="7.268055555555556in" height="7.268055555555556in"}

산업용 군집 로보틱스(Industrial Swarm Robotics)는 생산, 물류, 검사, 유지보수, 농업, 건설, 에너지 및 기타 운영 환경에서 다수의 자율 기계가 대규모로 협력해야 하는 상황에 분산형 다중 로봇 협력(Decentralized Multi-Robot Coordination)을 적용한다. 군집의 산업적 가치는 단순히 로봇 수를 늘리는 데서 발생하지 않는다. 작업을 분산하고, 변화하는 수요에 적응하며, 운영상의 단일 장애점(Single Point of Failure)을 제거하고, 필요에 따라 단계적으로 처리 능력을 확장할 수 있다는 점에서 핵심 가치가 발생한다.

효과적인 산업용 군집 아키텍처(Industrial Swarm Architecture)는 기존의 중앙집중식 디스패치 플릿(Centrally Dispatched Fleet)과 차이가 있다. 플릿 관리 시스템(Fleet Management System)은 모든 임무를 할당하고 전역 최적화(Global Optimization)를 수행할 수 있지만, 군집에서는 개별 로봇 또는 국소 그룹(Local Group)이 주변 정보를 이용하여 일부 의사결정을 수행할 수 있다. 산업용 구현에서는 두 모델을 결합하는 경우가 많으며, 감독 시스템(Supervisory System)이 목표, 안전 정책, 생산 우선순위를 설정하고 분산형 협력이 국소적인 실행을 담당한다.

창고 및 공장의 자재 운송(Material Transport)은 가장 실용적인 군집 활용 사례 중 하나이다. 대규모 자율이동로봇(Autonomous Mobile Robot, AMR) 집단은 부품, 팔레트, 토트(Tote), 공구, 완제품을 저장소, 생산라인, 검사 공정, 출하 영역 사이에서 운반할 수 있다. 고정 경로를 영구적으로 할당하는 대신 로봇은 수요, 혼잡도, 배터리 상태, 거리, 국소 교통 상황에 따라 작업과 경로를 동적으로 선택한다. 이를 통해 생산 변화에 맞추어 자재 흐름(Material Flow)을 지속적으로 적응시킬 수 있다.

분산 작업 할당(Distributed Task Allocation)은 운송 수요가 빠르게 변화할 때 특히 유용하다. 로봇은 자신의 가용성을 알리고, 주변 작업 요청을 평가하며, 입찰(Bid)을 교환하거나 시장 기반 할당 메커니즘(Market-Inspired Allocation Mechanism)을 이용하여 작업을 결정할 수 있다. 하나의 로봇을 사용할 수 없게 되면 완료되지 않은 작업은 자동으로 작업 풀(Task Pool)로 반환될 수 있다. 이를 통해 수동으로 설정된 로봇과 작업 스테이션 간 관계에 대한 의존성을 줄이고 제품 구성이 변화하는 유연 생산(Flexible Manufacturing)을 지원할 수 있다.

로봇 밀도가 증가할수록 교통 협력(Traffic Coordination)의 중요성도 커진다. 중앙집중식 경로 계획(Centralized Route Planning)은 전역 최적화를 제공할 수 있지만 대규모 로봇 집단에서는 연산 및 통신 병목이 발생할 수 있다. 국소 군집 규칙(Local Swarm Rule)은 교차로, 좁은 통로, 적재 영역, 충전 구역에서 발생하는 즉각적인 상호작용을 해결함으로써 전역 계획을 보완할 수 있다. 로봇은 우선순위를 협상하고, 짧은 경로 구간을 예약하거나, 국소 혼잡도에 따라 속도를 조절할 수 있다.

군집 로보틱스는 분산형 머신 텐딩(Distributed Machine Tending)도 지원할 수 있다. 매니퓰레이터를 탑재한 여러 이동 로봇이 CNC 장비, 검사 스테이션, 적층 제조 장비(Additive Manufacturing Equipment), 조립 셀(Assembly Cell)을 지원할 수 있다. 각 기계에 하나의 로봇을 영구적으로 전담시키는 대신 공유 로봇 집단이 장비 준비 상태, 공정 완료, 자재 가용성, 공구 요구조건에 대응할 수 있다. 따라서 동일한 로봇 자원을 하나의 시설 내 여러 생산 공정에서 공유하여 활용할 수 있다.

산업 검사(Industrial Inspection)는 대규모 시설에 반복적으로 관찰해야 하는 많은 설비 자산이 존재하기 때문에 또 하나의 강력한 응용 분야이다. 지상 로봇, 무인항공기(UAV), 등반 로봇(Climbing Robot), 특수 검사 플랫폼이 파이프라인, 탱크, 전기 설비, 구조물, 창고 랙, 생산 장비를 서로 나누어 검사할 수 있다. 분산 커버리지 알고리즘(Distributed Coverage Algorithm)은 중복 검사를 줄이면서 위험도와 유지보수 일정에 따라 필요한 영역을 반복적으로 점검할 수 있도록 한다.

이기종 군집(Heterogeneous Swarm)은 서로 다른 플랫폼이 상호 보완적인 능력을 제공할 수 있기 때문에 검사 분야에서 특히 유용하다. UAV는 높은 구조물을 검사하고, 지상 로봇은 더 무거운 센서를 운반하며, 소형 로봇은 제한된 공간으로 진입할 수 있다. 열화상 카메라, 음향 센서, 가스 감지기, 라이다(LiDAR), 비전 카메라, 진동 센서를 서로 다른 에이전트에 분산 배치할 수 있다. 이후 작업 할당 시스템은 검사 요구조건과 사용 가능한 센싱 및 이동 능력을 연결한다.

유지보수 작업(Maintenance Operation)은 검사를 협력형 개입(Cooperative Intervention)으로 확장할 수 있다. 센싱 로봇이 비정상 상태를 발견하면 해당 위치와 심각도를 주변 에이전트 또는 감독 시스템에 전달할 수 있다. 이후 공구, 교체 부품 또는 조작 능력(Manipulation Capability)을 갖춘 다른 로봇이 대응할 수 있다. 이를 통해 탐지와 개입을 분리하고 모든 로봇에 고가의 특수 장비를 장착하는 대신 제한된 특수 장비를 더 큰 로봇 집단에서 공유할 수 있다.

청소 작업(Cleaning)은 군집 커버리지(Swarm Coverage)와 자연스럽게 결합될 수 있다. 여러 자율 청소 로봇이 대형 공장, 공항, 병원, 쇼핑 시설, 창고, 물류센터를 동적으로 변화하는 작업 영역으로 나누어 담당할 수 있다. 보로노이 분할(Voronoi Partitioning), 가상 페로몬(Virtual Pheromone), 커버리지 지도(Coverage Map)를 이용하면 반복 청소를 줄이면서 누락된 영역을 식별할 수 있다. 특정 구역을 사용할 수 없거나 오염도가 높거나 혼잡하거나 일시적으로 우선순위가 높아지는 경우 로봇을 동적으로 재배치할 수 있다.

농업 응용(Agricultural Application)은 군집 개념을 대규모 야외 환경으로 확장한다. 소형 자율 기계들은 정찰, 살포, 제초, 파종, 수확 지원, 토양 측정, 작물 모니터링을 병렬로 수행할 수 있다. 하나의 매우 큰 농기계 대신 다수의 소형 기계를 사용하면 토양 압밀(Soil Compaction)을 줄일 수 있으며 운영 중복성(Operational Redundancy)을 확보할 수 있다. 국소 협력을 통해 농지를 분할하고 GNSS, 비전, 환경 센싱을 이용하여 개별 작업을 수행할 수 있다.

건설 현장(Construction Site)은 산업용 군집에 더 어려우면서도 잠재적 가치가 높은 환경이다. 로봇은 자재를 운반하고, 작업 진행 상황을 조사하며, 구조물을 스캔하고, 위치를 표시하며, 안전 상태를 검사하거나 반복적인 건설 공정을 지원할 수 있다. 환경이 지속적으로 변화하므로 정적 지도와 고정된 워크플로만으로는 충분하지 않다. 군집 구성원은 접근 경로, 장애물, 건설 단계가 변화함에 따라 공유 공간 지식(Shared Spatial Knowledge)을 갱신하고 작업을 재분배해야 한다.

에너지 인프라(Energy Infrastructure)는 또 하나의 중요한 활용 사례를 제공한다. 분산 로봇은 태양광 발전소, 풍력 시설, 변전소, 파이프라인, 저장 시설, 유틸리티 회랑(Utility Corridor)을 검사할 수 있다. 넓은 지리적 영역을 순차적으로 검사하면 많은 비용이 필요하지만 병렬 로봇 커버리지(Parallel Robotic Coverage)를 이용하면 검사 주기를 단축할 수 있다. 통신 인프라가 제한된 환경에서도 국소 자율성(Local Autonomy)과 지연 허용 데이터 교환(Delay-Tolerant Data Exchange)을 통해 작업을 지속하고 연결이 가능해졌을 때 관측 정보를 동기화할 수 있다.

위험 산업 환경(Hazardous Industrial Environment)은 군집 로봇을 적용할 수 있는 특히 강력한 근거를 제공한다. 화학 시설, 광산, 재난 지역, 고온 환경, 방사선 환경 또는 오염 지역은 작업자를 허용할 수 없는 위험에 노출시킬 수 있다. 다수의 로봇이 센싱과 탐색 작업을 분산하고, 통신 중계기(Communication Relay)를 유지하며, 위험 지도를 생성하고, 중복 관측(Redundant Observation)을 제공할 수 있다. 비교적 저비용의 로봇 한 대를 잃더라도 전체 임무가 반드시 종료되는 것은 아니다.

산업 사고 현장의 탐색 및 지도작성(Search and Mapping)에서는 이기종 군집 역할(Heterogeneous Swarm Role)을 활용할 수 있다. 일부 로봇은 미지의 영역을 탐색하고, 다른 로봇은 통신 연결성을 유지하며, 특수 로봇은 가스, 열, 방사선, 구조적 불안정성 또는 고립된 작업자를 탐지할 수 있다. 분산 프런티어 할당(Distributed Frontier Assignment)은 불필요한 중복 탐색을 방지하고, 동적 역할 할당(Dynamic Role Allocation)은 위험 요소, 차단된 경로 또는 로봇 고장으로 운영 상황이 변화할 때 군집이 대응할 수 있도록 한다.

재고 모니터링(Inventory Monitoring)은 확장 가능한 또 하나의 응용 분야이다. 카메라, RFID 리더, 바코드 스캐너 또는 깊이 센서(Depth Sensor)를 탑재한 이동 로봇이 저장 공간을 순찰하면서 재고 정보를 지속적으로 갱신할 수 있다. 대규모 정기 재고 조사를 수행하는 대신 군집이 정상 운영 과정에서 정보를 점진적으로 수집할 수 있다. 커버리지 일정(Coverage Scheduling)은 회전율이 높은 위치, 기록의 불확실성이 높은 영역 또는 재고 불일치가 자주 발생하는 위치에 우선순위를 부여할 수 있다.

산업용 군집 배치(Industrial Swarm Deployment)에서는 작업자의 존재를 반드시 고려해야 한다. 로봇은 지게차, 기술자, 생산 작업자, 방문자, 수동 조작 장비 주변에서 운용될 수 있다. 군집의 효율성이 사람의 안전보다 우선할 수는 없다. 국소 충돌 회피(Local Collision Avoidance), 속도 감소, 보호 영역(Protective Zone), 통행 우선권 규칙(Right-of-Way Rule), 감독 안전 정책이 집단 행동을 제한해야 한다. 로봇 밀도가 높아질수록 사람 인식형 협력(Human-Aware Coordination)의 중요성도 증가한다.

안전 아키텍처(Safety Architecture)는 집단 최적화(Collective Optimization)와 안전 필수 제어(Safety-Critical Control)를 분리해야 한다. 군집 알고리즘은 작업 할당, 대형, 커버리지 또는 교통 전략을 결정할 수 있지만 인증되거나 독립적으로 검증된 안전 기능이 속도, 분리 거리, 비상 정지, 제한 구역을 강제해야 한다. 따라서 집단 지능(Collective Intelligence)에 고장이 발생하더라도 기본적인 보호 기능이 제거되는 것이 아니라 생산성만 감소하도록 해야 한다. 이러한 분리는 실제 산업 현장에 적용하기 위한 핵심 조건이다.

통신 아키텍처(Communication Architecture) 역시 산업 환경의 특성을 반영해야 한다. 금속 구조물, 기계 장비, 전자기 간섭(Electromagnetic Interference), 네트워크 혼잡, 이동 장애물로 인해 무선 링크의 신뢰성이 저하될 수 있다. 군집은 영구적인 전역 연결(Global Connectivity)을 가정해서는 안 된다. 국소 방송(Local Broadcast), 메시 통신(Mesh Communication), 저장 후 전달(Store-and-Forward), 온보드 자율성(Onboard Autonomy)을 이용하면 일시적인 통신 성능 저하에서도 운용을 유지할 수 있으며, 연결이 가능한 경우 공장 인프라가 상위 수준의 협력을 제공할 수 있다.

위치추정 요구조건(Localization Requirement)은 작업에 따라 크게 달라진다. 자재 운송은 개방된 통로에서 센티미터 수준의 내비게이션 정확도를 허용할 수 있지만 도킹(Docking), 조작, 충전, 정밀 검사에서는 훨씬 높은 상대 위치 정밀도가 필요할 수 있다. 산업용 군집은 LiDAR 지도나 GNSS와 같은 전역 위치추정(Global Localization)을 국소 피두셜(Local Fiducial), 비주얼 마커(Visual Marker), UWB, 머신 비전(Machine Vision), 상대 센싱(Relative Sensing)과 결합할 수 있다. 정밀도는 시설 전체에 동일하게 적용하기보다 작업 요구조건에 따라 배분해야 한다.

다수의 로봇이 충전 자원(Charging Resource)을 공유하면 에너지 관리(Energy Management)는 집단 스케줄링 문제(Collective Scheduling Problem)가 된다. 모든 로봇이 유사한 배터리 임계값에 독립적으로 반응하면 동시에 충전소로 이동하여 운영 능력이 급격히 감소할 수 있다. 군집 인식형 충전(Swarm-Aware Charging)은 충전 시간을 분산하고, 충전기를 예약하며, 배터리 상태를 교환하고, 최소 활성 로봇 수(Minimum Active Population)를 유지할 수 있다. 충분한 에너지를 가진 로봇은 충전 중인 로봇의 작업을 일시적으로 분담할 수 있다.

고장 허용(Fault Tolerance)은 군집 시스템이 제공하는 가장 강력한 운영상의 장점 중 하나이다. 개별 로봇이 고장 나면 주변 로봇이 해당 작업을 재분배하고, 커버리지 공백을 복구하거나, 움직이지 않는 로봇을 피해 경로를 변경할 수 있다. 목표는 정상 성능을 완벽하게 유지하는 것이 아니라 점진적 성능 저하(Graceful Degradation)를 구현하는 것이다. 유지보수 인력이 고장 난 로봇을 제거하는 동안에도 나머지 군집은 감소된 수준이지만 유용한 운영 능력을 유지할 수 있다.

그러나 중복성(Redundancy)이 자동으로 복원력(Resilience)을 보장하는 것은 아니다. 모든 로봇이 하나의 무선 액세스 포인트, 중앙 데이터베이스, 지도 서버 또는 스케줄러에 의존한다면 해당 인프라의 고장으로 전체 군집이 정지할 수 있다. 따라서 산업용 아키텍처에서는 숨겨진 단일 장애점(Hidden Single Point of Failure)을 식별해야 한다. 핵심 상태 정보에는 복제(Replication), 국소 캐싱(Local Caching), 분산 복구 규칙, 중복 네트워크 또는 감독 서비스가 중단되었을 때 사용할 폴백 운용(Fallback Operation)이 필요할 수 있다.

자율 노드의 수가 증가할수록 사이버보안(Cybersecurity)의 중요성도 높아진다. 각 로봇, 게이트웨이, 무선 링크, 업데이트 메커니즘, 관리 인터페이스가 공격 표면(Attack Surface)의 일부가 될 수 있다. 인증(Authentication), 보안 신원(Secure Identity), 메시지 무결성(Message Integrity), 접근 제어(Access Control), 소프트웨어 서명(Software Signing), 네트워크 분할(Network Segmentation), 이상 모니터링(Anomaly Monitoring)을 아키텍처 단계부터 포함해야 한다. 손상된 정보가 집단 의사결정 메커니즘을 통해 검증 없이 확산되어서는 안 된다.

상호운용성(Interoperability)은 또 하나의 주요 산업적 과제이다. 시설에는 서로 다른 공급업체의 로봇과 함께 PLC, 제조 실행 시스템(Manufacturing Execution System, MES), 창고 관리 시스템(Warehouse Management System, WMS), 엘리베이터, 자동문, 생산 장비, 안전 시스템이 존재할 수 있다. 따라서 군집 계층(Swarm Layer)은 집단 협력의 의미론(Collective Semantics)을 공급업체별 인터페이스와 분리해야 한다. 표준화된 작업, 상태, 지도, 교통, 능력 표현을 이용하면 통합 비용을 줄이고 협력 로직이 특정 플랫폼에 지나치게 종속되는 것을 방지할 수 있다.

디지털 트윈(Digital Twin)과 시뮬레이션은 대규모 로봇 집단을 실제로 구매하기 전에 배치 계획을 지원할 수 있다. 시설의 기하 구조, 교통 패턴, 작업 수요, 충전 위치, 통신 커버리지, 로봇 고장을 모델링하여 필요한 로봇 수를 추정하고 병목 지점을 식별할 수 있다. 군집 시뮬레이션(Swarm Simulation)은 로봇 밀도가 실제 운용 수준에 접근했을 때만 혼잡이나 창발 행동(Emergent Behavior)이 나타날 수 있기 때문에 특히 중요하다.

경제성 평가(Economic Evaluation)는 단순한 기술적 실현 가능성을 입증하는 것이 아니라 군집 배치를 기존 자동화 방식과 비교해야 한다. 주요 평가 항목에는 처리량(Throughput), 인력 절감, 자산 활용률(Asset Utilization), 설치 비용, 유지보수 노력, 에너지 소비, 가동 중단 시간(Downtime), 확장성, 생산 중단 비용이 포함된다. 작업량의 변동이 크거나, 커버리지 영역이 넓거나, 고정형 자동화 비용이 높거나, 운영 연속성(Operational Continuity)의 경제적 가치가 높은 환경에서 군집 시스템의 매력도가 높아진다.

단계적 배치 전략(Phased Deployment Strategy)은 산업 현장의 위험을 줄인다. 초기에는 소수의 로봇과 제한적인 자율 협력 기능으로 운용을 시작하면서 감독 시스템이 강한 제어 권한을 유지할 수 있다. 이후 위치추정, 통신, 작업 할당, 안전, 복구 행동이 검증됨에 따라 더 많은 분산 기능과 추가 로봇을 도입할 수 있다. 이를 통해 군집 시스템이 더 큰 운영 책임을 맡기 전에 충분한 실제 운영 증거(Operational Evidence)를 축적할 수 있다.

핵심 성과 지표(Key Performance Indicator, KPI)는 개별 로봇의 성능뿐 아니라 집단 전체의 성능을 평가해야 한다. 유용한 지표에는 작업 처리량, 평균 응답 시간, 커버리지 완성도, 교통 지연, 로봇 활용률, 충전 가용성, 고장 복구 시간, 통신 오버헤드, 안전 개입 횟수, 로봇이 추가되거나 제거될 때의 성능 변화가 포함된다. 확장성은 로봇 수가 증가하더라도 유의미한 한계 생산성(Marginal Productivity)을 유지할 수 있는지를 통해 입증해야 한다.

따라서 가장 강력한 산업용 군집 활용 사례는 병렬성(Parallelism), 유연성(Flexibility), 중복성, 공간적 분산(Spatial Distribution)이 측정 가능한 이점을 제공하는 분야이다. 대규모 영역 검사, 동적 물류, 분산 청소, 위험 지역 탐색, 농업, 인프라 모니터링, 유연 생산은 상당한 효과를 얻을 수 있다. 반대로 하나의 고정된 반복 작업만 필요한 응용 분야에서는 군집의 복잡성으로 얻을 수 있는 이점이 작으며 기존 자동화 방식이 더 적합할 수 있다.

궁극적으로 산업용 군집 로보틱스(Industrial Swarm Robotics)는 개별 기계를 제어하는 방식에서 분산된 물리적 능력(Distributed Physical Capability)을 관리하는 방식으로의 전환을 의미한다. 감독 시스템은 목표, 제약조건, 거버넌스(Governance)를 정의하고, 로봇은 국소 및 분산 메커니즘을 통해 작업, 이동, 센싱, 에너지, 복구를 협력적으로 수행한다. 강건한 통신, 안전 아키텍처, 상호운용성, 시뮬레이션, 사이버보안, 측정 가능한 운영 경제성(Operational Economics)을 결합하면 군집 로보틱스는 확장 가능한 자율 산업 시스템(Scalable Autonomous Industrial System)을 위한 실용적인 기반으로 발전할 수 있다.
