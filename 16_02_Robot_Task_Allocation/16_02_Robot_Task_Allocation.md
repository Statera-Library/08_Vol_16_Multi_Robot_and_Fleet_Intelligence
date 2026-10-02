**Volume 16 Multi Robot and Fleet Intelligence**


# 02. Robot Task Allocation

##  

## 02.01 Task Allocation Problem Formulation MRTA Framework

![](images/image1.png){width="7.268055555555556in" height="7.268055555555556in"}

Multi-Robot Task Allocation (MRTA) defines the problem of deciding which robots should perform which tasks, at what time, and under what operational constraints. In a fleet system, allocation sits between mission generation and robot execution. It transforms incoming work orders into robot-task assignments while considering robot capabilities, locations, availability, workload, energy state, task priorities, and environmental conditions. The surrounding volume places this formulation before algorithmic methods such as auctions, Hungarian assignment, integer linear programming, online allocation, and reinforcement learning.

An MRTA problem can be represented through a set of robots \\(R=\\{r_1,r_2,\\ldots,r_m\\}\\), a set of tasks \\(T=\\{t_1,t_2,\\ldots,t_n\\}\\), and an assignment relation connecting them. Each robot has a state describing properties such as pose, velocity, payload capacity, battery level, tool configuration, current mission, and operational status. Each task similarly contains requirements such as location, service duration, deadline, priority, payload, required skills, and precedence relationships.

The fundamental decision variable expresses whether a robot is assigned to a task. In a simple binary formulation, \\(x_{ij}=1\\) indicates that robot \\(r_i\\) performs task \\(t_j\\), while \\(x_{ij}=0\\) indicates otherwise. More complex systems may introduce variables for start time, completion time, route sequence, charging decisions, resource reservations, or cooperative assignments. The resulting decision space grows rapidly as fleet size, task count, and operational constraints increase.

The objective function defines what constitutes a desirable allocation. A basic formulation may minimize the total assignment cost, expressed conceptually as \\( \\min \\sum_i\\sum_j c_{ij}x_{ij} \\), where \\(c_{ij}\\) represents the cost of assigning robot \\(i\\) to task \\(j\\). Cost does not have to represent physical distance alone. It can combine estimated travel time, energy consumption, task execution time, congestion exposure, lateness penalties, robot wear, and other operational factors.

In industrial fleets, task allocation is therefore usually a multi-objective decision problem. Minimizing travel distance can conflict with balancing robot utilization, preserving battery reserves, meeting deadlines, or maximizing throughput. A robot located closest to a task may not be the best candidate if its battery is low, its payload capability is insufficient, or assigning it would create congestion elsewhere. Practical MRTA systems consequently evaluate utility or cost from several fleet-level and robot-level variables simultaneously.

Constraints define the feasible region of the allocation problem. A task requiring one robot must normally be assigned exactly once, while an individual robot may be prevented from executing overlapping tasks. Capability constraints prohibit assignments to robots lacking required sensors, manipulators, payload capacity, environmental ratings, or certifications. Temporal constraints may enforce release times and deadlines, while spatial and resource constraints can represent restricted zones, elevators, docking stations, work cells, or shared infrastructure.

Robot and task heterogeneity fundamentally changes the formulation. In a homogeneous fleet, robots may be approximately interchangeable, allowing assignment to depend mainly on distance, availability, or queue length. In a heterogeneous fleet, the allocation engine must match task requirements against explicit robot capabilities. This becomes especially important when a fleet contains AMRs, mobile manipulators, inspection robots, towing platforms, or other machines whose mobility, payload, sensing, and manipulation capabilities differ significantly.

MRTA problems are also classified by how many robots and tasks participate in each assignment. Single-robot tasks require one robot, whereas multi-robot tasks require coordinated participation by several robots. A robot may execute a single task at a time or receive a sequence of tasks forming a schedule. These distinctions determine whether the problem resembles bipartite matching, scheduling, vehicle routing, coalition formation, or a combination of several optimization problems.

Time introduces another major dimension. Static MRTA assumes that the relevant robots and tasks are known when optimization begins. Real fleet operations are usually dynamic: new orders arrive, priorities change, robots complete missions, batteries decline, paths become congested, and failures remove resources from service. Allocation therefore becomes an online decision process in which assignments may need to be generated or revised continuously as fleet state changes.

A useful MRTA architecture separates problem formulation from the allocation algorithm itself. The formulation layer converts fleet state and mission requirements into robots, tasks, costs, utilities, and constraints. An allocation solver then searches for feasible assignments, and an execution layer dispatches the resulting missions to robots. Feedback from robot execution updates the fleet state and may trigger reassignment when tasks fail, robots become unavailable, or operating conditions change.

This separation is important because no single allocation algorithm is universally optimal. Greedy assignment can provide rapid decisions with low computational overhead, while auction mechanisms support flexible distributed or market-based allocation. The Hungarian algorithm is appropriate for structured one-to-one assignment, and integer linear programming can express richer combinations of objectives and constraints. The chapter structure deliberately progresses from MRTA formulation into these algorithmic approaches and later into dynamic, heterogeneous, battery-aware, and learning-based allocation.

Centralized MRTA uses a fleet-level allocator with broad visibility of robot and task states. This enables globally informed optimization and consistent enforcement of shared constraints, but computation and communication can become demanding as the fleet grows. Distributed allocation allows robots or local agents to negotiate assignments using partial information, improving autonomy and resilience but making global optimality and consistency more difficult. Hybrid architectures combine fleet-wide supervision with local decision authority.

Scalability is consequently part of the problem formulation rather than merely an implementation concern. If every robot can potentially serve every task, the number of candidate relationships increases with fleet and task population, while sequencing and temporal decisions can expand the search space far more aggressively. Large fleets therefore benefit from techniques such as candidate filtering, spatial partitioning, hierarchical allocation, rolling-horizon optimization, and decomposition before expensive optimization is performed.

Uncertainty must also be represented explicitly or indirectly. Travel time may change because of traffic, task duration may vary, localization confidence can degrade, and battery consumption depends on payload and motion conditions. An assignment that appears optimal from nominal values can become poor during execution. Robust MRTA therefore benefits from updated state estimation, uncertainty margins, prediction models, and periodic replanning rather than treating the initial allocation as permanently valid.

Task allocation should not be confused with path planning or traffic coordination. MRTA primarily determines responsibility: which robot or robot group should execute each task. Navigation determines how the assigned robot reaches its destination, while coordination manages interactions such as shared corridors, intersections, zones, and resources. Nevertheless, these layers are coupled because realistic assignment costs depend on route length, congestion, reservations, and predicted completion time. The volume accordingly treats task allocation before dedicated multi-robot coordination.

A production MRTA system ultimately operates as a closed decision loop. Fleet state and external orders define the current problem instance; the allocator evaluates feasible robot-task combinations; an optimization or policy mechanism selects assignments; missions are dispatched; and execution results return as new state. The process repeats whenever meaningful events occur. This event-driven perspective allows task allocation to respond naturally to new jobs, task completion, failures, charging requirements, and operational priority changes.

The quality of an MRTA framework should therefore be evaluated at both assignment and fleet levels. Relevant measures include assignment cost, task completion time, throughput, deadline satisfaction, robot utilization, workload balance, energy consumption, computational latency, and robustness to disturbances. An algorithm producing mathematically low assignment cost may still perform poorly operationally if decisions take too long, create traffic bottlenecks, repeatedly exhaust the same robots, or react inadequately to dynamic arrivals.

MRTA is consequently best understood as the decision foundation connecting fleet management with autonomous execution. Its formulation determines what information the system considers, which assignments are legal, and what operational goals the fleet optimizes. Once robots, tasks, decision variables, objective functions, constraints, dynamics, and uncertainty are represented coherently, different allocation methods can be compared on a common foundation and selected according to fleet scale, heterogeneity, real-time requirements, and industrial operating conditions.

다중 로봇 작업 할당(Multi-Robot Task Allocation, MRTA)은 어떤 로봇이 어떤 작업(Task)을 언제 수행해야 하는지, 그리고 어떠한 운영 제약조건(Operational Constraint) 아래에서 수행해야 하는지를 결정하는 문제로 정의된다. 플릿 시스템(Fleet System)에서 작업 할당(Task Allocation)은 미션 생성(Mission Generation)과 로봇 실행(Robot Execution) 사이에 위치하며, 입력되는 작업 지시를 로봇의 능력, 위치, 가용성, 작업 부하, 에너지 상태, 작업 우선순위 및 환경 조건을 고려한 로봇-작업 할당(Robot-Task Assignment)으로 변환한다.

MRTA 문제는 로봇 집합(Robot Set) \\(R=\\{r_1,r_2,\\ldots,r_m\\}\\), 작업 집합(Task Set) \\(T=\\{t_1,t_2,\\ldots,t_n\\}\\), 그리고 이들을 연결하는 할당 관계(Assignment Relation)를 통해 표현할 수 있다. 각 로봇은 위치 자세(Pose), 속도(Velocity), 적재 용량(Payload Capacity), 배터리 수준(Battery Level), 도구 구성(Tool Configuration), 현재 미션(Current Mission), 운영 상태(Operational Status) 등의 속성을 갖는다. 작업 역시 위치, 수행 시간, 마감시간, 우선순위, 적재물, 요구 기술 및 선행 관계(Precedence Relationship)를 포함한다.

기본적인 의사결정 변수(Decision Variable)는 특정 로봇이 특정 작업에 할당되는지를 표현한다. 단순한 이진 정식화(Binary Formulation)에서는 \\(x_{ij}=1\\)이면 로봇 \\(r_i\\)가 작업 \\(t_j\\)를 수행하고, \\(x_{ij}=0\\)이면 수행하지 않는다는 것을 의미한다. 보다 복잡한 시스템에서는 시작 시간(Start Time), 완료 시간(Completion Time), 경로 순서(Route Sequence), 충전 결정(Charging Decision), 자원 예약(Resource Reservation), 협력 작업 할당(Cooperative Assignment)을 위한 추가 변수를 사용할 수 있다.

목적 함수(Objective Function)는 어떠한 작업 할당이 바람직한지를 정의한다. 기본적인 정식화에서는 \\( \\min \\sum_i\\sum_j c_{ij}x_{ij} \\)와 같이 전체 할당 비용(Assignment Cost)을 최소화할 수 있으며, 여기에서 \\(c_{ij}\\)는 로봇 \\(i\\)를 작업 \\(j\\)에 할당하는 비용을 나타낸다. 이 비용은 단순한 물리적 거리만을 의미하지 않으며 예상 이동 시간, 에너지 소비량, 작업 수행 시간, 혼잡 노출도, 지연 페널티(Lateness Penalty), 로봇 마모 등의 요소를 결합할 수 있다.

산업용 플릿(Industrial Fleet)에서 작업 할당은 일반적으로 다목적 의사결정 문제(Multi-Objective Decision Problem)가 된다. 이동 거리 최소화는 로봇 활용률의 균형, 배터리 잔량 보존, 마감시간 준수 또는 처리량(Throughput) 극대화와 충돌할 수 있다. 작업에 가장 가까운 로봇이라도 배터리가 부족하거나 적재 능력이 충분하지 않거나 해당 로봇의 할당으로 다른 영역의 혼잡이 증가한다면 최적의 후보가 아닐 수 있다.

제약조건(Constraint)은 작업 할당 문제에서 가능한 해의 영역(Feasible Region)을 정의한다. 하나의 로봇이 필요한 작업은 일반적으로 정확히 한 번 할당되어야 하며, 개별 로봇은 서로 시간이 중첩되는 작업을 동시에 수행할 수 없다. 능력 제약조건(Capability Constraint)은 필요한 센서, 매니퓰레이터(Manipulator), 적재 능력, 환경 등급 또는 인증을 갖추지 못한 로봇의 할당을 제한한다. 시간 및 공간 제약조건은 작업 시작 가능 시간, 마감시간, 제한 구역, 엘리베이터, 도킹 스테이션(Docking Station) 및 공유 인프라를 표현할 수 있다.

로봇과 작업의 이질성(Heterogeneity)은 문제의 정식화를 근본적으로 변화시킨다. 동종 플릿(Homogeneous Fleet)에서는 로봇들이 대체로 상호 교환 가능하므로 거리, 가용성 또는 작업 대기열 길이를 중심으로 할당할 수 있다. 이종 플릿(Heterogeneous Fleet)에서는 작업 요구사항과 로봇의 명시적인 능력을 일치시켜야 한다. 특히 AMR, 모바일 매니퓰레이터(Mobile Manipulator), 검사 로봇(Inspection Robot), 견인 플랫폼(Towing Platform) 등이 함께 운영되는 경우 이러한 능력 기반 할당이 중요해진다.

MRTA 문제는 하나의 할당에 몇 대의 로봇과 몇 개의 작업이 참여하는지에 따라서도 분류된다. 단일 로봇 작업(Single-Robot Task)은 한 대의 로봇만 필요하지만, 다중 로봇 작업(Multi-Robot Task)은 여러 로봇의 협력 참여를 요구한다. 또한 로봇은 한 번에 하나의 작업을 수행하거나 여러 작업으로 구성된 작업 순서(Task Sequence)를 배정받을 수 있다. 이러한 차이에 따라 문제는 이분 매칭(Bipartite Matching), 스케줄링(Scheduling), 차량 경로 문제(Vehicle Routing), 연합 형성(Coalition Formation) 또는 이들의 복합 문제로 발전한다.

시간(Time)은 MRTA 문제에 또 다른 중요한 차원을 추가한다. 정적 MRTA(Static MRTA)는 최적화를 시작하는 시점에 관련된 로봇과 작업이 모두 알려져 있다고 가정한다. 그러나 실제 플릿 운영은 대부분 동적(Dynamic)이다. 새로운 주문이 도착하고, 우선순위가 변경되며, 로봇은 미션을 완료하고, 배터리는 감소하며, 경로 혼잡이 발생하고, 고장으로 일부 로봇이 운용에서 제외될 수 있다. 따라서 실제 작업 할당은 플릿 상태 변화에 따라 지속적으로 갱신되는 온라인 의사결정 과정(Online Decision Process)이 된다.

효과적인 MRTA 아키텍처(MRTA Architecture)는 문제 정식화(Problem Formulation)와 실제 할당 알고리즘(Allocation Algorithm)을 분리한다. 정식화 계층(Formulation Layer)은 플릿 상태와 미션 요구사항을 로봇, 작업, 비용, 효용(Utility) 및 제약조건으로 변환한다. 이후 할당 솔버(Allocation Solver)가 실행 가능한 할당을 탐색하고, 실행 계층(Execution Layer)이 생성된 미션을 로봇에 전달한다. 로봇의 실행 결과는 다시 플릿 상태를 갱신하며, 실패나 가용성 변화가 발생하면 재할당(Reallocation)을 유발한다.

이러한 분리는 하나의 작업 할당 알고리즘이 모든 상황에서 항상 최적일 수 없기 때문에 중요하다. 탐욕적 할당(Greedy Assignment)은 낮은 계산 비용으로 빠른 결정을 제공하며, 경매 기반 방식(Auction-Based Method)은 유연한 분산형 또는 시장 기반 할당(Market-Based Allocation)을 지원한다. 헝가리안 알고리즘(Hungarian Algorithm)은 구조화된 일대일 할당에 적합하고, 정수 선형 계획법(Integer Linear Programming, ILP)은 더욱 복잡한 목적 함수와 제약조건을 표현할 수 있다.

중앙집중형 MRTA(Centralized MRTA)는 로봇과 작업 상태를 광범위하게 파악할 수 있는 플릿 수준 할당기(Fleet-Level Allocator)를 사용한다. 이를 통해 전역적인 최적화(Global Optimization)와 공유 제약조건의 일관된 적용이 가능하지만, 플릿 규모가 증가할수록 계산량과 통신 부하가 커질 수 있다. 분산형 할당(Distributed Allocation)은 로봇이나 지역 에이전트(Local Agent)가 부분적인 정보를 기반으로 할당을 협상하도록 하여 자율성과 복원력을 높이지만 전역 최적성과 일관성 확보가 어려워질 수 있다.

따라서 확장성(Scalability)은 단순한 구현상의 문제가 아니라 MRTA 문제 정식화 자체에서 고려해야 하는 요소이다. 모든 로봇이 모든 작업을 수행할 수 있다면 플릿과 작업 수가 증가하면서 후보 할당 관계가 빠르게 증가하고, 작업 순서 및 시간적 결정까지 포함하면 탐색 공간(Search Space)은 더욱 급격하게 확대된다. 대규모 플릿에서는 후보 필터링(Candidate Filtering), 공간 분할(Spatial Partitioning), 계층적 할당(Hierarchical Allocation), 롤링 호라이즌 최적화(Rolling-Horizon Optimization), 문제 분해(Decomposition) 등이 필요하다.

불확실성(Uncertainty) 역시 명시적 또는 간접적으로 표현해야 한다. 교통 상황에 따라 이동 시간이 변할 수 있고, 작업 수행 시간이 달라질 수 있으며, 위치 추정 신뢰도(Localization Confidence)가 감소하거나 적재물과 주행 조건에 따라 배터리 소비량이 달라질 수 있다. 명목값(Nominal Value)을 기준으로 최적이었던 할당도 실제 실행 중에는 비효율적으로 변할 수 있다. 따라서 강건한 MRTA(Robust MRTA)는 지속적인 상태 추정, 불확실성 여유, 예측 모델(Prediction Model), 주기적인 재계획(Replanning)을 활용하는 것이 중요하다.

작업 할당(Task Allocation)은 경로 계획(Path Planning)이나 교통 조정(Traffic Coordination)과 구분되어야 한다. MRTA는 기본적으로 어떤 로봇 또는 로봇 그룹이 각 작업을 담당할 것인지를 결정한다. 내비게이션(Navigation)은 할당된 로봇이 목적지에 도달하는 방법을 결정하고, 다중 로봇 조정(Multi-Robot Coordination)은 공유 통로, 교차로, 구역 및 자원에서 발생하는 로봇 간 상호작용을 관리한다. 그러나 실제 할당 비용은 경로 길이, 혼잡도, 예약 상태 및 예상 완료 시간에 영향을 받기 때문에 이들 계층은 서로 밀접하게 연결된다.

실제 운영 환경의 MRTA 시스템은 궁극적으로 폐루프 의사결정 구조(Closed-Loop Decision Structure)로 동작한다. 플릿 상태와 외부 주문이 현재의 문제 인스턴스(Problem Instance)를 정의하고, 할당기는 가능한 로봇-작업 조합을 평가한다. 이후 최적화 알고리즘이나 정책(Policy)이 할당을 선택하고 미션을 로봇에 전달하며, 실행 결과는 새로운 상태 정보로 다시 입력된다. 새로운 작업, 작업 완료, 로봇 고장, 충전 요구 또는 운영 우선순위 변화가 발생할 때마다 이러한 과정이 반복된다.

MRTA 프레임워크(MRTA Framework)의 품질은 개별 할당뿐만 아니라 전체 플릿 수준에서도 평가해야 한다. 주요 평가 지표에는 할당 비용, 작업 완료 시간, 처리량, 마감시간 준수율, 로봇 활용률, 작업 부하 균형, 에너지 소비량, 계산 지연시간(Computational Latency), 외란에 대한 강건성(Robustness)이 포함된다. 수학적으로 낮은 할당 비용을 제공하는 알고리즘이라도 계산 시간이 지나치게 길거나 교통 병목을 유발하고 특정 로봇의 배터리를 반복적으로 소진한다면 실제 운영에서는 좋은 결과를 제공하지 못할 수 있다.

따라서 MRTA는 플릿 관리(Fleet Management)와 자율 실행(Autonomous Execution)을 연결하는 핵심 의사결정 기반(Decision Foundation)으로 이해하는 것이 적절하다. MRTA 정식화는 시스템이 어떤 정보를 고려하고, 어떤 할당을 허용하며, 플릿이 어떤 운영 목표를 최적화할 것인지를 결정한다. 로봇, 작업, 의사결정 변수, 목적 함수, 제약조건, 동적 변화 및 불확실성을 일관된 형태로 표현하면 다양한 할당 방법을 동일한 기반에서 비교하고 플릿 규모, 이질성, 실시간 요구사항 및 산업 운영 조건에 따라 적절한 방법을 선택할 수 있다.

##  

## 02.02 Greedy Auction Based Task Allocation [w/Code]

![](images/image2.png){width="7.268055555555556in" height="7.268055555555556in"}

Greedy and auction-based task allocation provide practical mechanisms for assigning tasks to robots without solving a large global optimization problem every time the fleet state changes. Within the MRTA framework, these methods evaluate candidate robot-task relationships and progressively construct an assignment. They are particularly attractive when decisions must be produced quickly, tasks arrive dynamically, or the computational cost of exact optimization becomes difficult to justify in real-time fleet operation.

A greedy allocation strategy selects the locally best available robot-task pair according to a predefined cost or utility function. For each candidate assignment between robot \\(r_i\\) and task \\(t_j\\), the allocator computes a score such as \\(c_{ij}\\), representing travel time, distance, energy consumption, expected completion time, or a weighted combination of several factors. The pair with the lowest cost, or equivalently the highest utility, is selected first and committed to the current allocation.

After an assignment is committed, the selected robot, task, or both are removed from the corresponding candidate set according to the problem constraints. The allocator then evaluates the remaining combinations and repeatedly chooses the next best candidate until all feasible tasks are assigned or no eligible robots remain. This sequential procedure is computationally simple and easy to implement, making greedy allocation useful for fleets in which rapid response is more important than guaranteed global optimality.

The principal limitation of greedy allocation is that a locally attractive decision can produce a poor global result. Assigning the nearest robot to the first task may prevent that robot from serving another task for which it is uniquely suitable. The outcome therefore depends strongly on task ordering, priority rules, and the design of the cost function. Greedy methods are best viewed as fast heuristics that trade some potential solution quality for low latency and predictable computational behavior.

Priority-aware greedy allocation improves this basic mechanism by processing urgent or operationally important tasks before ordinary tasks. A task score may combine deadline, waiting time, service class, production impact, and safety relevance. Robot candidates can then be ranked separately for each task. This approach allows an industrial fleet to encode operational policy directly into allocation without requiring a complex mathematical optimizer for every dispatch decision.

Auction-based allocation extends the assignment process by treating robots as bidders and tasks as items or contracts. When a task becomes available, an auctioneer announces its requirements to eligible robots. Each robot evaluates the task using its local state and calculates a bid reflecting the cost or utility of performing it. The task is awarded to the robot offering the most favorable bid, after which the winning robot updates its schedule and resource commitments.

A simple bid can be expressed as \\(b_{ij}=f(d_{ij},t_{ij},e_{ij},q_i,p_j)\\), where distance \\(d_{ij}\\), expected execution time \\(t_{ij}\\), energy requirement \\(e_{ij}\\), robot workload \\(q_i\\), and task priority \\(p_j\\) contribute to the bid. Depending on the convention, a lower bid may represent lower cost or a higher bid may represent greater utility. The important requirement is that bids provide a consistent basis for comparing candidate robots.

Auction mechanisms naturally support heterogeneous robot fleets because each robot can determine whether it is capable of executing a task before submitting a bid. A mobile manipulator may bid for a manipulation task, while a transport AMR may ignore it because the required capability is unavailable. Payload capacity, sensors, tools, battery state, access permissions, and environmental ratings can all participate in eligibility filtering and bid calculation before an assignment is accepted.

The auctioneer can be implemented as a centralized fleet-management component, but auction principles also support distributed architectures. In a centralized implementation, the fleet manager broadcasts tasks, collects bids, selects winners, and records assignments. In a distributed implementation, robots or local agents exchange task announcements and bids through communication middleware. Distributed auctions reduce dependence on a single decision node but require mechanisms for synchronization, duplicate prevention, timeout handling, and agreement on auction results.

Single-round auctions are suitable when rapid decisions are required. A task is announced, bids are collected for a short interval, and the best candidate receives the assignment. Multi-round auctions allow robots to revise bids as other assignments become known or as schedules change. Although additional rounds can improve allocation quality, they increase communication traffic and decision latency. The appropriate mechanism therefore depends on fleet size, network conditions, task urgency, and required optimization quality.

Greedy and auction approaches can also be combined. The fleet manager may greedily select the highest-priority unassigned task and then conduct an auction among eligible robots for that task. Alternatively, robots may submit bids for several tasks, after which the allocator greedily accepts the best nonconflicting bids. Such hybrid methods preserve much of the computational simplicity of greedy selection while incorporating robot-specific information and decentralized evaluation through bidding.

Dynamic task arrival makes these methods especially useful in practical fleet systems. When a new order appears, the system does not necessarily need to recompute the entire fleet schedule. Instead, it can identify currently available or interruptible robots, calculate new costs or bids, and allocate the task within a limited decision horizon. Completed missions, robot failures, priority changes, or canceled orders can similarly trigger local reallocation rather than complete global rescheduling.

Battery awareness can be incorporated directly into both greedy costs and auction bids. A robot with insufficient predicted energy to execute a task and reach a charging location can be removed from the candidate set. Robots approaching their charging threshold can receive additional cost penalties, while robots with sufficient energy reserves remain competitive. This prevents apparently efficient short-distance assignments from creating later mission failures or emergency charging events.

Congestion and route conditions should also influence allocation when navigation information is available. The geometrically nearest robot may require a long delay because of occupied corridors, intersections, elevators, or restricted zones. Replacing Euclidean distance with estimated travel time produces more realistic allocation decisions. Fleet systems can further incorporate predicted traffic cost so that several robots are not repeatedly assigned through the same bottleneck simply because their nominal paths appear shortest.

Robust implementations require explicit handling of communication and execution failures. An auction must define bidding deadlines, late-bid policies, acknowledgment procedures, and task ownership states. If the winning robot rejects the assignment, disconnects, or fails before execution, the task should return to the allocation pool. Assignment identifiers and state transitions are important for preventing two robots from simultaneously believing that they own the same task after retries or network disruptions.

Computational complexity is one of the strongest practical advantages of greedy allocation. Rather than exploring a combinatorial space of complete fleet assignments, the algorithm evaluates candidate relationships and makes incremental selections. Auction methods distribute part of this evaluation to individual robots, allowing local information to contribute without constructing a monolithic optimization model. These properties make both approaches attractive for online operation where decisions must often be made within milliseconds or seconds.

However, performance must be evaluated beyond allocation latency alone. Useful metrics include total travel distance, task completion time, throughput, deadline violation rate, robot utilization, workload balance, energy consumption, communication overhead, and the frequency of reassignment. Comparing greedy, auction-based, and globally optimized methods under identical task streams helps determine whether faster decisions compensate for any loss in assignment quality.

Simulation is valuable for tuning the cost function and bidding policy before fleet deployment. Different weights for distance, energy, priority, congestion, and workload can produce substantially different fleet behavior even when the allocation algorithm itself remains unchanged. Stress scenarios involving task bursts, robot failures, charging demand, communication delays, and uneven task distribution reveal whether the policy remains stable under conditions that are difficult to reproduce safely in production.

Greedy and auction-based allocation therefore occupy an important position between simple dispatch rules and computationally expensive global optimization. Greedy selection offers speed, determinism, and implementation simplicity, while auctions introduce flexible competition and robot-specific decision information. When combined with eligibility filtering, dynamic costs, failure recovery, and continuous fleet-state feedback, these methods provide a scalable foundation for real-time task assignment in practical multi-robot systems.

탐욕적 및 경매 기반 작업 할당(Greedy and Auction-Based Task Allocation)은 플릿 상태(Fleet State)가 변경될 때마다 대규모 전역 최적화(Global Optimization) 문제를 해결하지 않고도 로봇에 작업을 할당할 수 있는 실용적인 방법을 제공한다. 다중 로봇 작업 할당(Multi-Robot Task Allocation, MRTA) 프레임워크에서 이러한 방법은 후보 로봇-작업 관계(Candidate Robot-Task Relationship)를 평가하고 점진적으로 할당 결과를 구성한다. 특히 신속한 의사결정이 필요하거나 작업이 동적으로 발생하고, 정확한 최적화의 계산 비용을 실시간 플릿 운영에서 감당하기 어려운 경우에 효과적이다.

탐욕적 할당 전략(Greedy Allocation Strategy)은 미리 정의된 비용 함수(Cost Function) 또는 효용 함수(Utility Function)를 기준으로 현재 이용 가능한 로봇-작업 쌍 가운데 국소적으로 가장 좋은 조합을 선택한다. 로봇 \\(r_i\\)와 작업 \\(t_j\\) 사이의 각 후보 할당에 대해 할당기는 이동 시간, 거리, 에너지 소비량, 예상 완료 시간 또는 여러 요소의 가중 조합을 나타내는 \\(c_{ij}\\)와 같은 점수를 계산한다. 이후 비용이 가장 낮거나 효용이 가장 높은 조합을 먼저 선택하여 현재 할당에 확정한다.

하나의 할당이 확정되면 문제의 제약조건에 따라 선택된 로봇이나 작업 또는 둘 모두가 해당 후보 집합(Candidate Set)에서 제거된다. 이후 할당기는 남아 있는 조합을 다시 평가하고 모든 실행 가능한 작업이 할당되거나 적합한 로봇이 더 이상 남지 않을 때까지 다음 최적 후보를 반복적으로 선택한다. 이러한 순차적 절차는 계산이 단순하고 구현이 용이하므로 전역 최적성(Global Optimality) 보장보다 빠른 대응이 중요한 플릿에 유용하다.

탐욕적 할당의 주요 한계는 국소적으로 유리한 결정이 전체적으로는 좋지 않은 결과를 만들 수 있다는 점이다. 첫 번째 작업에 가장 가까운 로봇을 할당하면 해당 로봇만 수행할 수 있는 다른 작업에 그 로봇을 사용할 수 없게 될 수 있다. 따라서 결과는 작업 처리 순서, 우선순위 규칙(Priority Rule), 비용 함수 설계에 크게 영향을 받는다. 탐욕적 방법은 낮은 지연시간과 예측 가능한 계산 특성을 얻는 대신 잠재적인 해의 품질 일부를 양보하는 고속 휴리스틱(Fast Heuristic)으로 이해하는 것이 적절하다.

우선순위 인식 탐욕적 할당(Priority-Aware Greedy Allocation)은 긴급하거나 운영상 중요한 작업을 일반 작업보다 먼저 처리함으로써 기본적인 탐욕적 메커니즘을 개선한다. 작업 점수(Task Score)는 마감시간, 대기 시간, 서비스 등급, 생산 영향도 및 안전 관련성을 결합할 수 있다. 이후 각 작업에 대해 로봇 후보의 순위를 별도로 결정할 수 있다. 이를 통해 산업용 플릿은 매번 복잡한 수학적 최적화기를 사용하지 않고도 운영 정책(Operational Policy)을 작업 할당 과정에 직접 반영할 수 있다.

경매 기반 할당(Auction-Based Allocation)은 로봇을 입찰자(Bidder), 작업을 경매 대상 또는 계약(Task Contract)으로 간주하여 할당 과정을 확장한다. 새로운 작업이 생성되면 경매자(Auctioneer)가 해당 작업의 요구사항을 수행 가능한 로봇에 알린다. 각 로봇은 자신의 로컬 상태(Local State)를 이용하여 작업을 평가하고 해당 작업을 수행하는 데 필요한 비용 또는 효용을 반영한 입찰값(Bid)을 계산한다. 가장 유리한 입찰을 제시한 로봇이 작업을 할당받으며, 이후 해당 로봇은 자신의 일정과 자원 할당 상태를 갱신한다.

간단한 입찰값은 \\(b_{ij}=f(d_{ij},t_{ij},e_{ij},q_i,p_j)\\)와 같이 표현할 수 있으며, 여기에서 거리 \\(d_{ij}\\), 예상 수행 시간 \\(t_{ij}\\), 에너지 요구량 \\(e_{ij}\\), 로봇 작업 부하 \\(q_i\\), 작업 우선순위 \\(p_j\\)가 입찰값 결정에 사용된다. 정의 방식에 따라 낮은 입찰값이 낮은 비용을 의미할 수도 있고, 높은 입찰값이 높은 효용을 의미할 수도 있다. 중요한 것은 모든 입찰값이 후보 로봇을 일관된 기준으로 비교할 수 있도록 정의되어야 한다는 점이다.

경매 메커니즘(Auction Mechanism)은 각 로봇이 입찰 전에 해당 작업을 수행할 수 있는지를 자체적으로 판단할 수 있기 때문에 이종 로봇 플릿(Heterogeneous Robot Fleet)을 자연스럽게 지원한다. 모바일 매니퓰레이터(Mobile Manipulator)는 조작 작업에 입찰할 수 있지만, 필요한 능력을 갖추지 않은 운송용 AMR은 해당 작업을 무시할 수 있다. 적재 용량, 센서, 도구, 배터리 상태, 접근 권한 및 환경 등급 등을 적격성 필터링(Eligibility Filtering)과 입찰값 계산에 반영할 수 있다.

경매자(Auctioneer)는 중앙집중형 플릿 관리 구성요소(Centralized Fleet Management Component)로 구현할 수 있지만, 경매 원리는 분산형 아키텍처(Distributed Architecture)에서도 활용할 수 있다. 중앙집중형 구현에서는 플릿 관리자가 작업을 방송하고 입찰값을 수집한 후 승자를 선택하고 할당 결과를 기록한다. 분산형 구현에서는 로봇 또는 로컬 에이전트가 통신 미들웨어(Communication Middleware)를 통해 작업 공고와 입찰 정보를 교환한다. 분산 경매는 단일 의사결정 노드에 대한 의존성을 낮추지만 동기화, 중복 방지, 시간 초과 처리 및 경매 결과 합의가 필요하다.

단일 라운드 경매(Single-Round Auction)는 빠른 의사결정이 필요한 경우에 적합하다. 작업이 공고되고 짧은 시간 동안 입찰값을 수집한 다음 가장 적합한 후보에게 작업을 할당한다. 다중 라운드 경매(Multi-Round Auction)는 다른 할당 결과가 알려지거나 일정이 변경될 때 로봇이 자신의 입찰값을 수정할 수 있도록 한다. 추가적인 경매 라운드는 할당 품질을 향상시킬 수 있지만 통신 트래픽과 의사결정 지연시간을 증가시키므로 플릿 규모, 네트워크 상태, 작업 긴급도 및 요구되는 최적화 수준에 따라 적절한 방식을 선택해야 한다.

탐욕적 방식과 경매 방식은 서로 결합할 수도 있다. 플릿 관리자가 할당되지 않은 작업 가운데 우선순위가 가장 높은 작업을 탐욕적으로 선택한 다음, 해당 작업을 수행할 수 있는 로봇들을 대상으로 경매를 진행할 수 있다. 반대로 로봇이 여러 작업에 대한 입찰값을 제출하고, 할당기가 서로 충돌하지 않는 최상의 입찰을 탐욕적으로 선택할 수도 있다. 이러한 하이브리드 방식(Hybrid Method)은 탐욕적 선택의 계산 단순성을 상당 부분 유지하면서 로봇별 상태 정보와 분산 평가의 장점을 함께 활용한다.

동적 작업 도착(Dynamic Task Arrival)은 이러한 방법이 실제 플릿 시스템에서 특히 유용한 이유 중 하나이다. 새로운 주문이 발생하더라도 시스템은 반드시 전체 플릿 일정을 다시 계산할 필요가 없다. 대신 현재 사용 가능하거나 작업을 중단할 수 있는 로봇을 식별하고 새로운 비용 또는 입찰값을 계산하여 제한된 의사결정 범위 내에서 작업을 할당할 수 있다. 미션 완료, 로봇 고장, 우선순위 변경 또는 주문 취소 역시 전체적인 재스케줄링 대신 국소적 재할당(Local Reallocation)을 유발할 수 있다.

배터리 인식(Battery Awareness)은 탐욕적 비용과 경매 입찰값 모두에 직접 포함할 수 있다. 특정 작업을 수행하고 이후 충전 위치까지 이동하는 데 필요한 예상 에너지가 부족한 로봇은 후보 집합에서 제외할 수 있다. 충전 임계값에 가까워지는 로봇에는 추가적인 비용 페널티(Cost Penalty)를 부여하고, 충분한 에너지 여유를 가진 로봇은 경쟁력 있는 후보로 유지할 수 있다. 이를 통해 단거리라는 이유만으로 선택된 할당이 이후 미션 실패나 긴급 충전으로 이어지는 것을 방지할 수 있다.

내비게이션 정보(Navigation Information)를 사용할 수 있다면 혼잡도와 경로 상태 역시 작업 할당에 반영해야 한다. 기하학적으로 가장 가까운 로봇이라도 통로, 교차로, 엘리베이터 또는 제한 구역의 점유로 인해 긴 지연이 발생할 수 있다. 유클리드 거리(Euclidean Distance)를 예상 이동 시간(Estimated Travel Time)으로 대체하면 더욱 현실적인 할당이 가능하다. 또한 예측 교통 비용(Predicted Traffic Cost)을 반영하면 명목상 최단 경로라는 이유로 여러 로봇이 동일한 병목 구간에 반복적으로 할당되는 현상을 줄일 수 있다.

강건한 구현(Robust Implementation)을 위해서는 통신 및 실행 실패를 명시적으로 처리해야 한다. 경매에서는 입찰 마감시간, 지연 입찰 처리 정책, 승인 절차(Acknowledgment Procedure), 작업 소유권 상태(Task Ownership State)를 정의해야 한다. 낙찰된 로봇이 작업을 거부하거나 통신이 끊기거나 실행 전에 고장나는 경우 해당 작업은 다시 할당 풀(Allocation Pool)로 반환되어야 한다. 재시도나 네트워크 장애 이후 두 로봇이 동시에 동일한 작업을 자신이 소유한다고 판단하지 않도록 할당 식별자와 상태 전이(State Transition)를 관리하는 것도 중요하다.

계산 복잡도(Computational Complexity)는 탐욕적 할당이 갖는 가장 중요한 실용적 장점 중 하나이다. 전체 플릿 할당에 대한 조합적 탐색 공간(Combinatorial Search Space)을 탐색하는 대신 후보 관계를 평가하고 점진적으로 선택한다. 경매 방식은 이러한 평가의 일부를 개별 로봇에 분산하여 거대한 단일 최적화 모델을 구성하지 않고도 로컬 정보를 의사결정에 반영할 수 있다. 이러한 특성 때문에 두 방법 모두 밀리초 또는 수 초 이내에 결정을 내려야 하는 온라인 플릿 운영(Online Fleet Operation)에 적합하다.

그러나 성능은 작업 할당 지연시간만으로 평가해서는 안 된다. 유용한 평가 지표에는 전체 이동 거리, 작업 완료 시간, 처리량(Throughput), 마감시간 위반율, 로봇 활용률, 작업 부하 균형, 에너지 소비량, 통신 오버헤드(Communication Overhead), 재할당 빈도 등이 포함된다. 동일한 작업 흐름(Task Stream)에서 탐욕적 방식, 경매 기반 방식, 전역 최적화 방식을 비교하면 빠른 의사결정이 할당 품질의 손실을 어느 정도 보완하는지 평가할 수 있다.

시뮬레이션(Simulation)은 실제 플릿에 배포하기 전에 비용 함수와 입찰 정책(Bidding Policy)을 조정하는 데 유용하다. 거리, 에너지, 우선순위, 혼잡도 및 작업 부하에 서로 다른 가중치를 적용하면 동일한 작업 할당 알고리즘을 사용하더라도 플릿의 동작 특성이 크게 달라질 수 있다. 작업 폭증, 로봇 고장, 충전 수요, 통신 지연 및 불균등한 작업 분포와 같은 스트레스 시나리오(Stress Scenario)를 이용하면 실제 운영 환경에서 안전하게 재현하기 어려운 조건에서도 정책의 안정성을 평가할 수 있다.

따라서 탐욕적 및 경매 기반 할당(Greedy and Auction-Based Allocation)은 단순한 디스패치 규칙(Dispatch Rule)과 계산 비용이 높은 전역 최적화 사이에서 중요한 위치를 차지한다. 탐욕적 선택은 속도, 결정론적 특성(Determinism), 구현 단순성을 제공하며, 경매 방식은 유연한 경쟁 구조와 로봇별 의사결정 정보를 제공한다. 적격성 필터링, 동적 비용, 실패 복구 및 지속적인 플릿 상태 피드백과 결합하면 이러한 방법은 실제 다중 로봇 시스템의 실시간 작업 할당을 위한 확장 가능한 기반을 제공한다.

##  

## 02.03 Hungarian Algorithm Optimal Assignment [w/Code]

![](images/image3.png){width="7.268055555555556in" height="7.268055555555556in"}

The Hungarian Algorithm is a classical optimization method for solving one-to-one assignment problems with minimum total cost. In multi-robot task allocation, it provides a systematic way to assign robots to tasks when the cost of every feasible robot-task combination can be represented in a matrix. Unlike greedy selection, which commits to locally attractive pairs sequentially, the Hungarian method evaluates the assignment structure globally and returns an optimal solution for the defined cost matrix.

Consider a fleet containing robots \\(R=\\{r_1,r_2,\\ldots,r_m\\}\\) and tasks \\(T=\\{t_1,t_2,\\ldots,t_n\\}\\). For each possible robot-task pair, a cost \\(c_{ij}\\) is calculated and stored in a cost matrix \\(C=[c_{ij}]\\). The value may represent distance, predicted travel time, energy consumption, completion cost, or a weighted combination of operational factors. The optimization objective is to choose assignments that minimize the sum of selected costs while preventing conflicting assignments.

For a balanced problem with \\(n\\) robots and \\(n\\) tasks, the binary decision variable \\(x_{ij}\\) indicates whether robot \\(i\\) is assigned to task \\(j\\). The objective can be written as \\( \\min \\sum_i\\sum_j c_{ij}x_{ij} \\), subject to each robot receiving exactly one task and each task being assigned to exactly one robot. The Hungarian Algorithm exploits this structured assignment form and solves it much more efficiently than enumerating every possible permutation of assignments.

The cost matrix is the central representation of the problem. A simple matrix may contain geometric distances between current robot positions and task locations, but practical fleet systems usually benefit from more meaningful costs. Estimated travel time can incorporate the navigation graph and traffic conditions, while energy cost can account for payload and battery state. Penalties can also represent deadlines, restricted areas, capability mismatches, or undesirable workload imbalance.

The algorithm operates by transforming the cost matrix without changing which complete assignment has the minimum total cost. Conceptually, the minimum value in each row is first subtracted from all elements in that row. A similar reduction is then applied to columns. These operations create zero-cost positions that represent candidate assignments in the transformed matrix while preserving the relative optimality of complete assignment solutions.

The next stage attempts to select independent zeros so that no two selected zeros occupy the same row or column. If enough independent zeros exist to construct a complete assignment, the corresponding robot-task pairs define an optimal solution. If this is not possible, the matrix is adjusted using uncovered minimum values, producing additional zeros while preserving the underlying assignment optimum. The selection and adjustment process continues until a complete matching becomes available.

This matrix-reduction interpretation is important because the zeros do not mean that the original robot-task assignments actually have zero physical cost. They are artifacts of the mathematical transformation. Once the optimal zero structure has been identified, the selected row-column relationships are mapped back to the original cost matrix. The actual fleet cost is then calculated from the original travel, energy, time, or composite values associated with those assignments.

Real robot fleets frequently have different numbers of robots and tasks. If the cost matrix is rectangular, dummy robots or dummy tasks can be introduced to produce a square matrix. A dummy assignment may represent an idle robot or an unassigned task, depending on the situation. The associated dummy cost must be chosen carefully because it influences whether the optimizer prefers real assignments, temporary idleness, or deferred work.

Feasibility constraints also require careful treatment. If a robot cannot perform a particular task because of payload, sensor, manipulator, access-zone, or other capability requirements, the corresponding matrix element should not behave like an ordinary candidate. The system can remove the pair before optimization or assign it a sufficiently large penalty cost. Eligibility filtering before matrix construction is often preferable because it prevents physically impossible assignments from entering the optimization process.

Compared with greedy allocation, the Hungarian Algorithm can avoid decisions that appear attractive individually but create poor fleet-wide combinations. A nearby robot may have the lowest cost for one task, yet assigning another robot to that task could allow the nearby robot to serve a second task much more efficiently. By considering the complete matrix structure, the algorithm can select a combination whose total cost is lower even when some individual assignments are not locally minimal.

The major computational advantage is that the Hungarian Algorithm solves the structured assignment problem in polynomial time, commonly characterized as approximately \\(O(n\^3)\\) for an \\(n\\times n\\) problem. This is dramatically more efficient than evaluating all \\(n!\\) possible one-to-one assignments. Consequently, it can be practical for substantial robot-task matrices, although very large fleets or extremely frequent reallocations may still require filtering, partitioning, or hierarchical optimization.

The method is especially appropriate when a reasonably stable snapshot of available robots and tasks can be constructed. For example, a fleet manager can periodically collect waiting tasks and idle robots, build a cost matrix, calculate an optimal matching, and dispatch the resulting assignments. This batch-oriented structure works well when assignments can be reconsidered at defined decision epochs rather than requiring independent decisions immediately whenever every new task arrives.

Dynamic operation can nevertheless be supported through repeated optimization. When tasks arrive, robots finish missions, failures occur, or priorities change, the fleet manager can construct an updated matrix and execute the Hungarian Algorithm again. Reoptimization frequency must be selected carefully because continuously changing assignments can cause instability. Practical systems often protect tasks already being executed while reconsidering only unassigned tasks and robots that remain available for new work.

Assignment stability can be incorporated by adding reassignment penalties. If a robot has already accepted a task but has not started execution, changing that assignment may impose communication, routing, or operational costs. Adding a switching penalty to the relevant matrix entries discourages unnecessary reassignment while still allowing changes when the improvement is sufficiently large. This converts mathematical optimality into behavior that better reflects real fleet operations.

Battery and charging conditions can also be represented through the cost matrix. A robot with a low state of charge may receive a high cost for distant or energy-intensive tasks, while an assignment that leaves the robot near a charging station may receive a lower effective cost. If predicted energy is insufficient to complete the mission safely, that robot-task pair should be considered infeasible rather than merely expensive.

Traffic-aware assignment further improves practical performance. Straight-line distance may poorly represent the actual cost of moving through warehouses, factories, hospitals, or outdoor logistics sites. Estimated path length, reserved-zone delays, elevator waiting time, intersection congestion, and predicted traffic can be incorporated into \\(c_{ij}\\). The assignment optimizer then operates on costs that better approximate the actual consequences of dispatching each robot.

A limitation of the standard Hungarian formulation is that it primarily addresses one-to-one assignment rather than complex scheduling. It does not directly represent long task sequences, multiple robots cooperating on one task, precedence constraints, shared-resource schedules, or detailed charging plans. Such requirements may demand extensions, repeated assignment stages, or more expressive optimization approaches such as integer linear programming, vehicle-routing formulations, or dedicated scheduling methods.

Another important limitation is that optimality is defined only with respect to the supplied cost matrix. If the cost model ignores congestion, battery degradation, deadlines, or robot capability, the algorithm can produce a mathematically optimal but operationally poor assignment. Considerable engineering effort therefore belongs in cost modeling, state estimation, eligibility filtering, and prediction rather than in the assignment solver alone.

Performance evaluation should compare the optimized assignment against practical baselines such as nearest-robot and greedy allocation. Relevant measures include total assignment cost, travel distance, completion time, throughput, deadline satisfaction, utilization balance, energy consumption, optimization latency, and reassignment frequency. Such comparisons reveal when global one-to-one optimization provides meaningful operational improvement and when simpler allocation methods are sufficient.

The Hungarian Algorithm therefore provides an important bridge between heuristic dispatch and more general mathematical optimization within robot task allocation. It offers guaranteed optimal matching for a defined one-to-one cost matrix, predictable polynomial complexity, and a clean interface between fleet-state estimation and mission dispatch. When combined with realistic costs, capability filtering, periodic reoptimization, and execution feedback, it becomes a powerful allocation mechanism for practical multi-robot fleet systems.

헝가리안 알고리즘(Hungarian Algorithm)은 최소 총비용(Minimum Total Cost)을 갖는 일대일 할당 문제(One-to-One Assignment Problem)를 해결하기 위한 고전적인 최적화 방법이다. 다중 로봇 작업 할당(Multi-Robot Task Allocation)에서는 실행 가능한 모든 로봇-작업 조합(Robot-Task Combination)의 비용을 행렬(Matrix)로 표현할 수 있을 때 로봇을 작업에 체계적으로 할당하는 방법을 제공한다. 국소적으로 유리한 조합을 순차적으로 확정하는 탐욕적 선택(Greedy Selection)과 달리 헝가리안 알고리즘은 전체 할당 구조를 전역적으로 평가하고 정의된 비용 행렬(Cost Matrix)에 대한 최적해를 반환한다.

로봇 플릿(Fleet)이 로봇 \\(R=\\{r_1,r_2,\\ldots,r_m\\}\\)과 작업 \\(T=\\{t_1,t_2,\\ldots,t_n\\}\\)으로 구성되어 있다고 가정한다. 가능한 각각의 로봇-작업 쌍에 대해 비용 \\(c_{ij}\\)를 계산하여 비용 행렬 \\(C=[c_{ij}]\\)에 저장한다. 이 값은 거리, 예상 이동 시간, 에너지 소비량, 완료 비용 또는 여러 운영 요소의 가중 조합을 나타낼 수 있다. 최적화의 목적은 서로 충돌하는 할당을 방지하면서 선택된 비용의 합을 최소화하는 할당 조합을 찾는 것이다.

\\(n\\)대의 로봇과 \\(n\\)개의 작업으로 구성된 균형 문제(Balanced Problem)에서 이진 의사결정 변수(Binary Decision Variable) \\(x_{ij}\\)는 로봇 \\(i\\)가 작업 \\(j\\)에 할당되는지를 나타낸다. 목적 함수는 \\( \\min \\sum_i\\sum_j c_{ij}x_{ij} \\)로 표현할 수 있으며, 각 로봇은 정확히 하나의 작업을 받고 각 작업 역시 정확히 하나의 로봇에 할당된다는 제약조건을 갖는다. 헝가리안 알고리즘은 이러한 구조화된 할당 형태를 활용하여 가능한 모든 할당 순열(Permutation)을 열거하는 방식보다 훨씬 효율적으로 문제를 해결한다.

비용 행렬(Cost Matrix)은 문제를 표현하는 핵심 요소이다. 단순한 행렬에서는 현재 로봇 위치와 작업 위치 사이의 기하학적 거리를 사용할 수 있지만, 실제 플릿 시스템에서는 보다 의미 있는 비용을 사용하는 것이 효과적이다. 예상 이동 시간(Estimated Travel Time)은 내비게이션 그래프(Navigation Graph)와 교통 상황을 반영할 수 있으며, 에너지 비용은 적재물과 배터리 상태를 고려할 수 있다. 마감시간, 제한 구역, 능력 불일치 또는 바람직하지 않은 작업 부하 불균형도 페널티(Penalty)로 표현할 수 있다.

알고리즘은 전체 할당 가운데 어느 조합이 최소 총비용을 갖는지를 변경하지 않으면서 비용 행렬을 변환하는 방식으로 동작한다. 개념적으로 먼저 각 행(Row)의 최솟값을 해당 행의 모든 원소에서 뺀다. 이후 각 열(Column)에 대해서도 유사한 축소 과정(Reduction)을 수행한다. 이러한 연산은 완전한 할당해(Complete Assignment Solution)의 상대적인 최적성을 유지하면서 변환된 행렬 안에 후보 할당을 나타내는 0의 위치를 생성한다.

다음 단계에서는 선택된 두 개의 0이 동일한 행이나 열에 위치하지 않도록 독립적인 0(Independent Zero)을 선택한다. 완전한 할당을 구성하기에 충분한 독립적인 0이 존재하면 이에 대응하는 로봇-작업 쌍이 최적해를 정의한다. 충분한 0을 선택할 수 없는 경우에는 덮이지 않은 최소값(Uncovered Minimum Value)을 이용하여 행렬을 조정하고, 기본적인 할당 최적성을 유지하면서 새로운 0을 생성한다. 완전한 매칭(Complete Matching)이 가능해질 때까지 선택과 조정 과정을 반복한다.

이러한 행렬 축소(Matrix Reduction)의 해석에서 0은 원래 로봇-작업 할당의 실제 물리적 비용이 0이라는 의미가 아니라는 점이 중요하다. 0은 수학적인 변환 과정에서 생성된 값이다. 최적의 0 구조가 결정되면 선택된 행-열 관계(Row-Column Relationship)를 원래의 비용 행렬로 다시 대응시킨다. 이후 실제 플릿 비용은 해당 할당과 연관된 원래의 이동, 에너지, 시간 또는 복합 비용 값을 이용하여 계산한다.

실제 로봇 플릿에서는 로봇 수와 작업 수가 서로 다른 경우가 많다. 비용 행렬이 직사각형(Rectangular Matrix)이라면 가상 로봇(Dummy Robot) 또는 가상 작업(Dummy Task)을 추가하여 정사각 행렬(Square Matrix)로 만들 수 있다. 상황에 따라 가상 할당(Dummy Assignment)은 유휴 로봇 또는 할당되지 않은 작업을 의미할 수 있다. 가상 할당의 비용은 최적화기가 실제 할당, 일시적인 유휴 상태 또는 작업 연기 가운데 무엇을 선호하는지에 영향을 주므로 신중하게 설정해야 한다.

실행 가능성 제약조건(Feasibility Constraint) 역시 신중하게 처리해야 한다. 로봇이 적재 용량, 센서, 매니퓰레이터(Manipulator), 접근 구역 또는 기타 능력 요구사항 때문에 특정 작업을 수행할 수 없다면 해당 행렬 원소를 일반적인 후보처럼 처리해서는 안 된다. 최적화 전에 해당 조합을 제거하거나 충분히 큰 페널티 비용을 부여할 수 있다. 물리적으로 불가능한 할당이 최적화 과정에 진입하는 것을 방지할 수 있으므로 행렬 구성 전에 적격성 필터링(Eligibility Filtering)을 수행하는 방식이 일반적으로 더 적절하다.

탐욕적 할당(Greedy Allocation)과 비교하면 헝가리안 알고리즘은 개별적으로는 매력적으로 보이지만 플릿 전체적으로 좋지 않은 조합을 만드는 결정을 방지할 수 있다. 가까운 로봇이 특정 작업에 대해 가장 낮은 비용을 갖더라도 다른 로봇을 해당 작업에 배치함으로써 가까운 로봇이 두 번째 작업을 훨씬 효율적으로 수행할 수 있을 수 있다. 알고리즘은 전체 행렬 구조를 고려하므로 일부 개별 할당이 국소 최소(Local Minimum)가 아니더라도 전체 비용이 더 낮은 조합을 선택할 수 있다.

헝가리안 알고리즘의 중요한 계산적 장점은 구조화된 할당 문제를 다항 시간(Polynomial Time)에 해결한다는 점이며, \\(n\\times n\\) 문제의 경우 일반적으로 약 \\(O(n\^3)\\)의 계산 복잡도(Computational Complexity)로 표현된다. 이는 가능한 \\(n!\\)개의 모든 일대일 할당을 평가하는 것보다 훨씬 효율적이다. 따라서 상당한 크기의 로봇-작업 행렬에도 실용적으로 적용할 수 있지만, 매우 큰 플릿이나 극도로 빈번한 재할당에서는 필터링, 분할(Partitioning) 또는 계층적 최적화(Hierarchical Optimization)가 추가로 필요할 수 있다.

이 방법은 이용 가능한 로봇과 작업에 대해 비교적 안정적인 상태 스냅샷(State Snapshot)을 구성할 수 있는 상황에 특히 적합하다. 예를 들어 플릿 관리자는 주기적으로 대기 중인 작업과 유휴 로봇을 수집하고 비용 행렬을 생성한 다음 최적 매칭(Optimal Matching)을 계산하여 그 결과를 디스패치(Dispatch)할 수 있다. 이러한 배치 지향 구조(Batch-Oriented Structure)는 새로운 작업이 발생할 때마다 즉시 독립적인 결정을 내려야 하는 경우보다 정해진 의사결정 시점(Decision Epoch)에 할당을 재검토할 수 있는 환경에서 효과적이다.

그러나 반복적인 최적화(Repeated Optimization)를 통해 동적 운영(Dynamic Operation)도 지원할 수 있다. 새로운 작업이 도착하거나 로봇이 미션을 완료하고, 고장이 발생하거나 우선순위가 변경되면 플릿 관리자는 갱신된 행렬을 구성하여 헝가리안 알고리즘을 다시 실행할 수 있다. 지속적인 할당 변경은 시스템의 불안정성을 유발할 수 있으므로 재최적화 빈도(Reoptimization Frequency)는 신중하게 선택해야 한다. 실제 시스템에서는 이미 수행 중인 작업은 보호하고, 아직 할당되지 않은 작업과 새로운 작업을 수행할 수 있는 로봇만 재검토하는 경우가 많다.

할당 안정성(Assignment Stability)은 재할당 페널티(Reassignment Penalty)를 추가함으로써 반영할 수 있다. 로봇이 이미 작업을 수락했지만 아직 실행을 시작하지 않은 경우에도 할당을 변경하면 통신, 경로 변경 또는 운영상의 추가 비용이 발생할 수 있다. 관련 행렬 원소에 전환 페널티(Switching Penalty)를 추가하면 불필요한 재할당을 억제하면서 개선 효과가 충분히 큰 경우에는 할당 변경을 허용할 수 있다. 이를 통해 수학적인 최적성을 실제 플릿 운영에 더욱 적합한 동작으로 변환할 수 있다.

배터리 및 충전 조건(Battery and Charging Conditions) 역시 비용 행렬을 통해 표현할 수 있다. 충전 상태(State of Charge)가 낮은 로봇에는 멀리 떨어져 있거나 에너지 소비가 큰 작업에 높은 비용을 부여할 수 있으며, 작업 완료 후 충전소 가까이에 위치하게 되는 할당에는 상대적으로 낮은 유효 비용(Effective Cost)을 부여할 수 있다. 예측 에너지가 미션을 안전하게 완료하기에 부족한 경우에는 해당 로봇-작업 조합을 단순히 비싼 후보가 아니라 실행 불가능한 조합(Infeasible Pair)으로 처리해야 한다.

교통 인식 할당(Traffic-Aware Assignment)을 적용하면 실제 운영 성능을 더욱 향상시킬 수 있다. 직선거리는 창고, 공장, 병원 또는 야외 물류 현장에서 실제 이동 비용을 제대로 표현하지 못할 수 있다. 예상 경로 길이, 예약 구역 지연, 엘리베이터 대기 시간, 교차로 혼잡 및 예측 교통량 등을 \\(c_{ij}\\)에 포함할 수 있다. 이를 통해 할당 최적화기는 각 로봇을 디스패치했을 때 실제로 발생할 결과를 더욱 정확하게 반영한 비용을 기반으로 동작할 수 있다.

표준 헝가리안 정식화(Standard Hungarian Formulation)의 한계는 복잡한 스케줄링보다 일대일 할당을 주로 다룬다는 점이다. 긴 작업 순서, 하나의 작업에 대한 여러 로봇의 협력, 선행 제약조건(Precedence Constraint), 공유 자원 스케줄 또는 세부적인 충전 계획을 직접 표현하지는 않는다. 이러한 요구사항을 처리하려면 확장된 정식화, 반복적인 할당 단계 또는 정수 선형 계획법(Integer Linear Programming), 차량 경로 문제(Vehicle Routing) 정식화, 전용 스케줄링 방법과 같은 보다 표현력이 높은 최적화 방법이 필요할 수 있다.

또 다른 중요한 한계는 최적성(Optimality)이 입력된 비용 행렬을 기준으로만 정의된다는 점이다. 비용 모델이 혼잡, 배터리 열화, 마감시간 또는 로봇 능력을 고려하지 않는다면 알고리즘은 수학적으로는 최적이지만 실제 운영에서는 좋지 않은 할당을 생성할 수 있다. 따라서 실제 엔지니어링에서는 할당 솔버(Assignment Solver) 자체뿐만 아니라 비용 모델링(Cost Modeling), 상태 추정(State Estimation), 적격성 필터링 및 예측에도 상당한 노력이 필요하다.

성능 평가는 최적화된 할당을 최근접 로봇 할당(Nearest-Robot Allocation)이나 탐욕적 할당과 같은 실용적인 기준 방식(Baseline)과 비교해야 한다. 주요 평가 지표에는 총 할당 비용, 이동 거리, 완료 시간, 처리량(Throughput), 마감시간 준수율, 활용률 균형, 에너지 소비량, 최적화 지연시간(Optimization Latency), 재할당 빈도 등이 포함된다. 이러한 비교를 통해 전역 일대일 최적화가 실제 운영에서 의미 있는 개선을 제공하는 경우와 보다 단순한 할당 방식으로 충분한 경우를 판단할 수 있다.

따라서 헝가리안 알고리즘(Hungarian Algorithm)은 로봇 작업 할당에서 휴리스틱 디스패치(Heuristic Dispatch)와 보다 일반적인 수학적 최적화(Mathematical Optimization)를 연결하는 중요한 방법이다. 정의된 일대일 비용 행렬에 대해 최적 매칭(Optimal Matching)을 보장하고, 예측 가능한 다항 계산 복잡도를 제공하며, 플릿 상태 추정과 미션 디스패치 사이에 명확한 인터페이스를 제공한다. 현실적인 비용 모델, 능력 필터링, 주기적인 재최적화 및 실행 피드백과 결합하면 실제 다중 로봇 플릿 시스템을 위한 강력한 작업 할당 메커니즘으로 활용할 수 있다.

##  

## 02.04 Integer Linear Programming ILP for Task Alloc [w/Code]

![](images/image4.png){width="7.268055555555556in" height="7.268055555555556in"}

Integer Linear Programming (ILP) provides a general mathematical framework for robot task allocation when assignment decisions must satisfy multiple operational constraints simultaneously. Unlike specialized matching methods that primarily solve one-to-one assignments, ILP can represent robot capabilities, task priorities, resource limits, deadlines, workload, battery conditions, and other requirements within one optimization model. This flexibility makes ILP particularly useful for structured fleet-planning problems.

The basic formulation begins with binary decision variables such as \\(x_{ij}\\), where \\(x_{ij}=1\\) means robot \\(i\\) is assigned to task \\(j\\), and \\(x_{ij}=0\\) means that assignment is not selected. Additional integer or binary variables can represent task sequencing, charging decisions, resource reservations, robot activation, or assignment alternatives. The optimization solver searches for values of these variables that satisfy every constraint while minimizing or maximizing a defined objective.

A simple objective minimizes total assignment cost and can be expressed as \\( \\min \\sum_i\\sum_j c_{ij}x_{ij} \\). The coefficient \\(c_{ij}\\) describes the cost of assigning robot \\(i\\) to task \\(j\\). In practical fleets, this cost may combine travel distance, expected travel time, execution duration, energy consumption, deadline penalties, workload imbalance, or operational risk. Proper cost design allows the mathematical objective to represent meaningful fleet-level performance rather than distance alone.

Assignment constraints define the fundamental relationship between robots and tasks. If every task must be performed exactly once, the model can impose \\( \\sum_i x_{ij}=1 \\) for every task \\(j\\). If a robot may receive at most one task during the current allocation cycle, \\( \\sum_j x_{ij}\\leq1 \\) can be applied. These equations and inequalities form the foundation on which more detailed industrial constraints can be added.

Robot capability constraints prevent physically invalid assignments. Suppose task \\(j\\) requires a payload capacity, manipulator, sensor, certification, or environmental rating that robot \\(i\\) does not possess. The corresponding variable can be fixed as \\(x_{ij}=0\\), removing that combination from the feasible solution space. Capability matrices can automate this process and allow one ILP model to allocate tasks across heterogeneous fleets containing several different robot classes.

Capacity constraints become important when robots can execute multiple tasks or transport multiple items within a planning horizon. If \\(w_j\\) represents the load associated with task \\(j\\) and \\(W_i\\) represents the capacity of robot \\(i\\), a constraint such as \\( \\sum_j w_jx_{ij}\\leq W_i \\) prevents overload. Similar formulations can represent storage capacity, tool availability, processing limits, or other finite resources associated with each robot.

Time-related requirements can be represented by introducing scheduling variables. A task may have a release time, expected service duration, and deadline, while the robot may need travel time between task locations. Start-time and completion-time variables allow the optimization model to enforce temporal feasibility. Additional binary variables can specify which task occurs before another when two tasks are assigned to the same robot, transforming basic allocation into a combined assignment-and-scheduling problem.

Task precedence is important when missions contain dependent operations. Inspection may need to occur before maintenance, material pickup before delivery, or preparation before manipulation. ILP can represent such relationships using linear constraints between task start or completion variables. This capability distinguishes general mathematical programming from simple matching because the optimizer can select assignments while simultaneously respecting the logical structure of an industrial workflow.

Battery-aware allocation can also be incorporated into the model. Each candidate assignment can have an estimated energy requirement, while each robot has available energy and a required safety reserve. Constraints can prohibit task combinations that exceed the robot\'s usable battery capacity. Charging can be modeled as an explicit decision when necessary, allowing the optimizer to determine whether a robot should continue executing tasks or visit a charging station within the planning horizon.

Shared resources introduce another class of constraints. Multiple robots may require the same elevator, docking station, loading point, inspection device, work cell, or charging station. ILP variables can represent resource occupancy and ordering so that incompatible uses do not occur simultaneously. Although such formulations increase model size, they enable the allocation layer to account for infrastructure limitations that would otherwise produce conflicts during mission execution.

Multi-objective fleet behavior is commonly represented through a weighted objective function. Total travel cost, lateness, energy use, workload imbalance, and unassigned-task penalties can be multiplied by coefficients and combined into one scalar objective. The weights express operational priorities. A warehouse focused on throughput may emphasize completion time, while an energy-constrained inspection fleet may assign greater importance to battery consumption and charging requirements.

Unassigned tasks require explicit modeling when demand can exceed available fleet capacity. A binary variable can indicate whether a task is deferred, and the objective function can assign a penalty according to task priority. High-priority work can receive a large deferral penalty, while low-priority work can be postponed at lower cost. This allows the optimizer to return a feasible operational plan even when completing every task within the current planning horizon is impossible.

The strength of ILP lies in its ability to describe a wide range of requirements precisely, but this flexibility creates computational challenges. Robot-task assignment alone may remain manageable, while sequencing, time windows, shared resources, charging, and routing can dramatically increase the number of variables and constraints. Many practical formulations become mixed-integer linear programs (MILPs), whose solution time can grow rapidly as fleet size and planning horizon increase.

Modern solvers typically use techniques such as branch-and-bound, cutting planes, preprocessing, and heuristics to search the discrete solution space efficiently. The solver maintains bounds on solution quality and can often provide a feasible solution before proving mathematical optimality. This is valuable in robotics because an operationally good assignment delivered within a strict time limit may be more useful than waiting much longer for a formally optimal solution.

Solver time limits therefore become an important engineering parameter. A fleet manager may allow several seconds for strategic batch scheduling but only hundreds of milliseconds for urgent online allocation. When the time limit expires, the best feasible solution found so far can be used if its quality is acceptable. This creates a practical trade-off between optimization quality, computational latency, and responsiveness to changing fleet conditions.

Problem decomposition can improve scalability. Instead of optimizing hundreds of robots and tasks in one monolithic model, the fleet can be divided by geographic zone, robot type, task class, or planning horizon. A higher-level allocator can first partition the workload, after which smaller ILP problems are solved independently. Rolling-horizon optimization similarly solves only a limited future interval and repeats the process as new information becomes available.

Dynamic fleet operation requires repeated model updates. New tasks may arrive, robots may fail, battery states may change, and execution delays may invalidate earlier assumptions. Rather than rebuilding every decision from the beginning, practical systems can preserve tasks already in execution and reoptimize the remaining workload. Warm-start information from a previous solution can also help the solver obtain a high-quality updated assignment more quickly.

The quality of an ILP solution depends directly on the accuracy of its model parameters. Travel times, energy estimates, task durations, and resource availability are often uncertain in real environments. A mathematically optimal plan can therefore perform poorly if its assumptions differ substantially from actual execution. Safety margins, periodic state updates, conservative estimates, and continuous replanning help connect deterministic optimization models with uncertain robot operations.

ILP also provides a useful reference for evaluating simpler task-allocation algorithms. For problem instances small enough to solve near optimality, the ILP result can serve as a benchmark against greedy, auction-based, or learning-based approaches. Differences in total cost, completion time, energy consumption, and computation time reveal how much solution quality is sacrificed when faster or more decentralized methods are used.

In production architectures, the optimization model should remain separated from fleet execution. Fleet state, tasks, capabilities, and infrastructure information are converted into variables, coefficients, and constraints; the solver produces an assignment plan; and the fleet-management layer validates and dispatches the resulting missions. Execution feedback then updates the next optimization cycle. This separation prevents mathematical decisions from bypassing safety and operational controls.

Integer Linear Programming therefore extends robot task allocation from simple matching into constraint-rich fleet optimization. Its main advantage is not merely finding a low-cost assignment, but expressing complex operational rules within a consistent mathematical framework. When combined with realistic cost models, solver time limits, decomposition, rolling-horizon replanning, and execution feedback, ILP becomes a powerful method for planning heterogeneous multi-robot fleets under industrial constraints.

정수 선형 계획법(Integer Linear Programming, ILP)은 작업 할당 결정이 여러 운영 제약조건(Operational Constraint)을 동시에 만족해야 하는 경우 로봇 작업 할당(Robot Task Allocation)을 위한 일반적인 수학적 프레임워크를 제공한다. 주로 일대일 할당(One-to-One Assignment)을 해결하는 특화된 매칭 방법과 달리 ILP는 로봇 능력, 작업 우선순위, 자원 한계, 마감시간, 작업 부하, 배터리 조건 및 기타 요구사항을 하나의 최적화 모델(Optimization Model) 안에서 표현할 수 있다. 이러한 유연성으로 인해 ILP는 구조화된 플릿 계획(Fleet Planning) 문제에 특히 유용하다.

기본적인 정식화(Formulation)는 \\(x_{ij}\\)와 같은 이진 의사결정 변수(Binary Decision Variable)에서 시작한다. 여기에서 \\(x_{ij}=1\\)은 로봇 \\(i\\)가 작업 \\(j\\)에 할당되었음을 의미하고, \\(x_{ij}=0\\)은 해당 할당이 선택되지 않았음을 의미한다. 추가적인 정수 변수(Integer Variable) 또는 이진 변수를 이용하여 작업 순서, 충전 결정, 자원 예약, 로봇 활성화 또는 할당 대안을 표현할 수 있다. 최적화 솔버(Optimization Solver)는 모든 제약조건을 만족하면서 정의된 목적 함수를 최소화하거나 최대화하는 변수값을 탐색한다.

단순한 목적 함수(Objective Function)는 전체 할당 비용을 최소화하며 \\( \\min \\sum_i\\sum_j c_{ij}x_{ij} \\)로 표현할 수 있다. 계수 \\(c_{ij}\\)는 로봇 \\(i\\)를 작업 \\(j\\)에 할당하는 비용을 나타낸다. 실제 플릿에서는 이 비용에 이동 거리, 예상 이동 시간, 작업 수행 시간, 에너지 소비량, 마감시간 페널티, 작업 부하 불균형 또는 운영 위험 등을 결합할 수 있다. 적절한 비용 설계를 통해 수학적 목적 함수가 단순한 거리뿐만 아니라 의미 있는 플릿 수준 성능을 나타내도록 할 수 있다.

할당 제약조건(Assignment Constraint)은 로봇과 작업 사이의 기본적인 관계를 정의한다. 모든 작업을 정확히 한 번씩 수행해야 한다면 각 작업 \\(j\\)에 대해 \\( \\sum_i x_{ij}=1 \\)이라는 조건을 적용할 수 있다. 현재 할당 주기에서 하나의 로봇이 최대 하나의 작업만 받을 수 있다면 \\( \\sum_j x_{ij}\\leq1 \\)을 적용할 수 있다. 이러한 등식과 부등식은 보다 상세한 산업 운영 제약조건을 추가하기 위한 기본 구조를 형성한다.

로봇 능력 제약조건(Robot Capability Constraint)은 물리적으로 불가능한 할당을 방지한다. 작업 \\(j\\)가 특정 적재 용량, 매니퓰레이터(Manipulator), 센서, 인증 또는 환경 등급을 요구하지만 로봇 \\(i\\)가 이를 갖추지 못한 경우 해당 변수는 \\(x_{ij}=0\\)으로 고정하여 그 조합을 실행 가능한 해 공간(Feasible Solution Space)에서 제거할 수 있다. 능력 행렬(Capability Matrix)을 이용하면 이 과정을 자동화하고 여러 종류의 로봇으로 구성된 이종 플릿(Heterogeneous Fleet)을 하나의 ILP 모델로 처리할 수 있다.

용량 제약조건(Capacity Constraint)은 로봇이 하나의 계획 구간(Planning Horizon)에서 여러 작업을 수행하거나 여러 물품을 운송할 수 있는 경우 중요하다. \\(w_j\\)가 작업 \\(j\\)와 관련된 적재량이고 \\(W_i\\)가 로봇 \\(i\\)의 적재 용량이라면 \\( \\sum_j w_jx_{ij}\\leq W_i \\)와 같은 제약조건을 사용하여 과적을 방지할 수 있다. 유사한 정식화를 이용하여 저장 용량, 도구 가용성, 처리 한계 또는 각 로봇과 관련된 기타 유한 자원(Finite Resource)을 표현할 수 있다.

시간 관련 요구사항은 스케줄링 변수(Scheduling Variable)를 도입하여 표현할 수 있다. 작업에는 시작 가능 시간(Release Time), 예상 서비스 시간, 마감시간이 존재할 수 있으며 로봇은 작업 위치 사이를 이동하는 시간도 필요하다. 시작 시간(Start Time)과 완료 시간(Completion Time) 변수를 사용하면 최적화 모델이 시간적 실행 가능성(Temporal Feasibility)을 보장하도록 할 수 있다. 또한 동일한 로봇에 두 작업이 할당될 경우 어떤 작업을 먼저 수행할 것인지를 추가적인 이진 변수로 지정하여 기본적인 할당 문제를 할당 및 스케줄링 결합 문제로 확장할 수 있다.

작업 선행 관계(Task Precedence)는 미션이 서로 의존적인 작업으로 구성된 경우 중요하다. 검사가 유지보수보다 먼저 수행되어야 하거나, 물품 픽업이 배송보다 먼저 이루어져야 하며, 준비 작업이 조작 작업보다 선행되어야 할 수 있다. ILP는 작업의 시작 또는 완료 변수 사이에 선형 제약조건(Linear Constraint)을 설정하여 이러한 관계를 표현할 수 있다. 이러한 기능을 통해 단순 매칭과 달리 산업 워크플로(Industrial Workflow)의 논리적 구조를 준수하면서 작업 할당을 결정할 수 있다.

배터리 인식 할당(Battery-Aware Allocation) 역시 모델에 포함할 수 있다. 각 후보 할당에는 예상 에너지 요구량을 부여하고 각 로봇에는 현재 이용 가능한 에너지와 필요한 안전 여유(Safety Reserve)를 설정할 수 있다. 제약조건을 이용하여 로봇의 사용 가능한 배터리 용량을 초과하는 작업 조합을 금지할 수 있다. 필요한 경우 충전(Charging)을 명시적인 의사결정으로 모델링하여 계획 구간 안에서 로봇이 작업을 계속 수행할지 충전소를 방문할지를 최적화기가 결정하도록 할 수 있다.

공유 자원(Shared Resource)은 또 다른 종류의 제약조건을 발생시킨다. 여러 로봇이 동일한 엘리베이터, 도킹 스테이션(Docking Station), 적재 지점, 검사 장비, 작업 셀(Work Cell) 또는 충전소를 사용해야 할 수 있다. ILP 변수를 이용하여 자원의 점유 상태와 사용 순서를 표현하고 서로 양립할 수 없는 자원 사용이 동시에 발생하지 않도록 할 수 있다. 이러한 정식화는 모델의 크기를 증가시키지만 미션 실행 과정에서 충돌을 일으킬 수 있는 인프라 한계를 작업 할당 단계에서 고려할 수 있도록 한다.

다목적 플릿 동작(Multi-Objective Fleet Behavior)은 일반적으로 가중 목적 함수(Weighted Objective Function)를 통해 표현한다. 전체 이동 비용, 지연 시간, 에너지 사용량, 작업 부하 불균형 및 미할당 작업 페널티에 각각 가중치를 곱하여 하나의 스칼라 목적 함수(Scalar Objective)로 결합할 수 있다. 이러한 가중치는 운영 우선순위를 나타낸다. 처리량을 중요하게 생각하는 창고에서는 완료 시간을 강조할 수 있고, 에너지 제약이 큰 검사 플릿에서는 배터리 소비량과 충전 요구사항에 더 높은 중요도를 부여할 수 있다.

수요가 이용 가능한 플릿 용량을 초과할 수 있는 경우에는 미할당 작업(Unassigned Task)을 명시적으로 모델링해야 한다. 이진 변수를 이용하여 작업이 연기되는지를 표현하고 목적 함수에서는 작업 우선순위에 따라 페널티를 부여할 수 있다. 우선순위가 높은 작업에는 큰 연기 페널티(Deferral Penalty)를 부여하고, 우선순위가 낮은 작업에는 상대적으로 낮은 비용으로 연기를 허용할 수 있다. 이를 통해 현재 계획 구간 안에서 모든 작업을 완료하는 것이 불가능한 상황에서도 최적화기는 실행 가능한 운영 계획을 생성할 수 있다.

ILP의 강점은 다양한 요구사항을 정확하게 표현할 수 있다는 데 있지만 이러한 유연성은 계산상의 어려움도 발생시킨다. 단순한 로봇-작업 할당은 관리 가능한 규모일 수 있지만 작업 순서, 시간 창(Time Window), 공유 자원, 충전 및 경로 계획까지 포함하면 변수와 제약조건의 수가 급격히 증가할 수 있다. 많은 실제 정식화는 혼합 정수 선형 계획법(Mixed-Integer Linear Programming, MILP)으로 확장되며 플릿 규모와 계획 구간이 증가함에 따라 계산 시간이 빠르게 증가할 수 있다.

현대적인 솔버(Solver)는 일반적으로 분기 한정법(Branch-and-Bound), 절단 평면(Cutting Plane), 전처리(Preprocessing), 휴리스틱(Heuristic) 등의 기법을 이용하여 이산 해 공간(Discrete Solution Space)을 효율적으로 탐색한다. 솔버는 해의 품질에 대한 경계값(Bound)을 유지하며 수학적인 최적성을 증명하기 전에 실행 가능한 해(Feasible Solution)를 제공할 수 있다. 로봇 시스템에서는 엄격한 시간 제한 내에 제공되는 운영상 충분히 좋은 할당이 완전한 최적해를 훨씬 오래 기다리는 것보다 유용할 수 있다.

따라서 솔버 시간 제한(Solver Time Limit)은 중요한 엔지니어링 파라미터가 된다. 플릿 관리자는 전략적인 배치 스케줄링(Batch Scheduling)에는 수 초의 계산 시간을 허용할 수 있지만 긴급한 온라인 할당에는 수백 밀리초 정도만 허용할 수 있다. 시간 제한이 만료되면 현재까지 발견된 최상의 실행 가능한 해를 품질이 허용되는 범위에서 사용할 수 있다. 이를 통해 최적화 품질, 계산 지연시간(Computational Latency), 변화하는 플릿 상태에 대한 대응성 사이의 실용적인 절충이 이루어진다.

문제 분해(Problem Decomposition)는 확장성을 향상시킬 수 있다. 수백 대의 로봇과 작업을 하나의 거대한 모델에서 최적화하는 대신 지리적 구역, 로봇 유형, 작업 종류 또는 계획 구간에 따라 플릿을 분할할 수 있다. 상위 수준 할당기(Higher-Level Allocator)가 먼저 작업 부하를 분배한 후 보다 작은 ILP 문제를 독립적으로 해결할 수 있다. 롤링 호라이즌 최적화(Rolling-Horizon Optimization) 역시 제한된 미래 구간만을 최적화하고 새로운 정보가 들어올 때마다 이 과정을 반복한다.

동적 플릿 운영(Dynamic Fleet Operation)에서는 모델을 반복적으로 갱신해야 한다. 새로운 작업이 발생하고, 로봇이 고장나며, 배터리 상태가 변하거나 실행 지연으로 기존 가정이 더 이상 유효하지 않을 수 있다. 모든 의사결정을 처음부터 다시 계산하기보다는 이미 실행 중인 작업을 유지하면서 남아 있는 작업 부하만 재최적화할 수 있다. 이전 해의 웜 스타트(Warm Start) 정보를 활용하면 솔버가 높은 품질의 갱신된 할당을 보다 빠르게 찾는 데 도움이 될 수 있다.

ILP 해의 품질은 모델 파라미터의 정확성에 직접적으로 영향을 받는다. 이동 시간, 에너지 추정값, 작업 수행 시간 및 자원 가용성은 실제 환경에서 불확실한 경우가 많다. 따라서 수학적으로 최적인 계획도 모델의 가정과 실제 실행 상황이 크게 다르면 좋지 않은 결과를 낼 수 있다. 안전 여유, 주기적인 상태 갱신, 보수적인 추정(Conservative Estimate), 지속적인 재계획(Continuous Replanning)은 결정론적 최적화 모델과 불확실한 로봇 운영 환경을 연결하는 데 도움이 된다.

ILP는 보다 단순한 작업 할당 알고리즘을 평가하기 위한 유용한 기준(Reference)도 제공한다. 거의 최적해까지 계산할 수 있는 규모의 문제에서는 ILP 결과를 탐욕적 방식(Greedy), 경매 기반 방식(Auction-Based) 또는 학습 기반 방식(Learning-Based)의 벤치마크(Benchmark)로 사용할 수 있다. 전체 비용, 완료 시간, 에너지 소비량 및 계산 시간의 차이를 비교하면 더 빠르거나 분산된 방법을 사용할 때 어느 정도의 해 품질을 희생하는지 평가할 수 있다.

실제 운영 아키텍처(Production Architecture)에서는 최적화 모델과 플릿 실행(Fleet Execution)을 분리해야 한다. 플릿 상태, 작업, 로봇 능력 및 인프라 정보를 변수, 계수 및 제약조건으로 변환하고, 솔버가 할당 계획을 생성하면 플릿 관리 계층(Fleet-Management Layer)이 결과를 검증한 후 미션을 디스패치한다. 이후 실행 피드백(Execution Feedback)이 다음 최적화 주기의 상태를 갱신한다. 이러한 분리를 통해 수학적 최적화 결과가 안전 및 운영 제어를 우회하여 직접 실행되는 것을 방지할 수 있다.

따라서 정수 선형 계획법(Integer Linear Programming)은 로봇 작업 할당을 단순한 매칭 문제에서 다양한 제약조건을 포함하는 플릿 최적화(Fleet Optimization) 문제로 확장한다. 핵심적인 장점은 단순히 낮은 비용의 할당을 찾는 것이 아니라 복잡한 운영 규칙을 일관된 수학적 프레임워크 안에서 표현할 수 있다는 점이다. 현실적인 비용 모델, 솔버 시간 제한, 문제 분해, 롤링 호라이즌 재계획 및 실행 피드백과 결합하면 ILP는 산업 환경의 제약조건 아래에서 이종 다중 로봇 플릿을 계획하기 위한 강력한 방법이 된다.

##  

## 02.05 Online Task Allocation with Dynamic Arrivals [w/Code]

![](images/image5.png){width="7.268055555555556in" height="7.268055555555556in"}

Online task allocation addresses multi-robot environments in which tasks are not completely known before operation begins but arrive continuously while robots are already executing missions. Unlike static allocation, where a fixed set of robots and tasks can be optimized together, an online allocator must make decisions using the information currently available. New orders, inspection requests, transport missions, emergency jobs, and cancellations can therefore modify the allocation problem at any moment.

The system can be modeled as an event-driven decision process. At time \\(t\\), the fleet has a robot state \\(R(t)\\), a set of waiting tasks \\(Q(t)\\), and a collection of assignments already being executed. When a new task \\(j\\) arrives at time \\(a_j\\), the allocator updates the task queue and determines whether an immediate assignment should be made or whether the task should wait for a future decision epoch. This repeated process transforms task allocation from a one-time optimization problem into continuous fleet control.

Each dynamically arriving task contains information required for allocation, such as location, release time, priority, service duration, deadline, payload, and required capabilities. The fleet state simultaneously changes as robots move, consume energy, complete work, enter charging, or become unavailable. Consequently, the cost \\(c_{ij}(t)\\) of assigning robot \\(i\\) to task \\(j\\) is time dependent rather than fixed and should be recalculated from the latest operational state.

A simple online policy assigns every new task immediately to the best currently available robot. This provides low decision latency and works well when tasks are independent and fleet capacity is abundant. However, immediate commitment can be inefficient when several important tasks arrive close together. A robot assigned to a low-priority request may become unavailable just before a critical task appears, illustrating the fundamental difficulty of making decisions without knowledge of future arrivals.

Queue-based allocation reduces this problem by temporarily collecting unassigned tasks and processing them at defined decision epochs. Instead of reacting independently to every arrival, the allocator may optimize all waiting tasks every few seconds or whenever the queue reaches a threshold. This batching strategy provides more opportunities for globally efficient combinations, although tasks experience additional waiting time. The batch interval therefore creates a trade-off between responsiveness and allocation quality.

Event-triggered allocation provides another approach. Reallocation can be initiated when a new high-priority task arrives, a robot completes a mission, battery state crosses a threshold, a robot fails, or an existing task is canceled. Routine state changes do not necessarily invoke expensive optimization. By associating allocation decisions with meaningful fleet events, the system can reduce computational overhead while maintaining rapid responses to conditions that materially affect mission execution.

Dynamic allocation must distinguish between committed and flexible work. A task already being physically executed should normally remain protected, while a task assigned but not yet started may be reconsidered if conditions change. Unassigned tasks remain fully flexible. Explicit assignment states such as queued, reserved, dispatched, accepted, executing, completed, failed, and canceled prevent the optimizer from treating every task as equally movable during each reallocation cycle.

Reassignment introduces both opportunities and costs. Moving a task from one robot to another can improve travel time or satisfy a newly changed priority, but excessive reassignment creates instability known as assignment thrashing. Robots may repeatedly receive new destinations without completing useful work. Practical online allocators therefore introduce reassignment penalties, minimum commitment periods, hysteresis, or improvement thresholds so that an existing assignment changes only when the expected benefit is significant.

Priority management becomes particularly important under dynamic arrivals. Emergency, safety-critical, or production-blocking tasks may need to preempt ordinary work. Priority can be represented through weighted costs, deadlines, queue ordering, or explicit service classes. Aging mechanisms can gradually increase the priority of tasks that have waited for a long time, preventing low-priority jobs from suffering indefinite starvation when high-priority requests arrive continuously.

Robot availability cannot be represented by a simple idle-or-busy flag. A robot currently executing a mission may soon become available near a newly arriving task, making it a better candidate than an idle robot located far away. Online allocation can therefore use predicted availability time and predicted completion position. This forward-looking state representation improves assignment quality by evaluating where robots are expected to be when they can actually begin the new task.

Battery state creates another dynamic constraint. The allocator should consider not only current state of charge but also predicted energy consumption for the active mission, candidate task, and subsequent movement to a charging location. A robot may be geographically attractive yet operationally unsuitable because accepting another task would violate its reserve threshold. Charging missions can themselves be inserted dynamically when predicted energy becomes insufficient for future work.

Online allocation is closely coupled with navigation and traffic conditions because assignment costs change while robots move. Congestion, blocked corridors, elevator queues, restricted zones, and temporary obstacles can significantly modify estimated travel time. Periodically updating robot-task costs from the navigation layer allows the allocator to respond to the real operational environment rather than relying on static geometric distance.

Several allocation algorithms can operate inside the online framework. Greedy selection provides very fast decisions, auctions allow robots to evaluate dynamically announced tasks, and matching algorithms can optimize batches of currently waiting work. Integer or mixed-integer optimization can be applied over a rolling horizon when richer constraints must be considered. The online architecture therefore describes when and how allocation is updated rather than requiring one specific optimization algorithm.

Rolling-horizon optimization is especially useful when limited future information is available. At each decision epoch, the allocator optimizes tasks known within a finite horizon, commits only near-term decisions, and postpones less urgent choices. When new information arrives, the horizon advances and the problem is solved again. This strategy avoids assuming that a long-term schedule will remain valid in an environment where task demand and robot conditions continually change.

Prediction can further improve online decisions. Historical order patterns, production schedules, traffic statistics, and task arrival models can estimate future demand even though exact tasks are unknown. The allocator may intentionally keep some robots available near locations where high-priority work is likely to appear. Such anticipatory allocation trades immediate efficiency for future responsiveness and forms a bridge between reactive scheduling and predictive fleet optimization.

Communication delay and distributed state consistency must also be considered. A fleet manager may receive robot states several hundred milliseconds after they were generated, while two tasks may arrive almost simultaneously from different external systems. Timestamped events, monotonic task versions, assignment identifiers, acknowledgments, and transactional state transitions help prevent duplicate dispatches or decisions based on obsolete information.

Failure handling is naturally integrated into an online architecture. If a robot disconnects or reports a fault, its unfinished tasks can return to the allocation queue unless execution state requires human intervention. Other robots are then evaluated using the updated fleet state. Similarly, a canceled task releases its reserved robot, while a delayed task can trigger downstream rescheduling. Recovery therefore becomes another allocation event rather than a completely separate mechanism.

Scalability depends strongly on how many candidate relationships are reconsidered after each event. Reoptimizing every robot against every task can become expensive for large fleets. Candidate filtering can restrict consideration to compatible robots, nearby zones, appropriate robot classes, or a limited number of best candidates. Hierarchical allocation can first select a site or zone and then perform detailed assignment locally, reducing both computation and communication requirements.

Performance evaluation must include dynamic metrics rather than only the cost of individual assignments. Important measures include task response time, queue waiting time, completion time, throughput, deadline violation rate, reassignment frequency, robot utilization, energy consumption, starvation rate, and computational latency. Tail behavior is also important because occasional extremely long waits may be unacceptable even when average performance appears good.

Simulation should reproduce realistic arrival processes rather than testing only fixed task sets. Burst demand, priority changes, robot failures, charging events, congestion, communication delays, and cancellations can reveal behavior that static benchmarks cannot expose. Comparing immediate dispatch, periodic batching, event-triggered allocation, and rolling-horizon optimization under identical arrival streams provides a practical basis for selecting an online allocation policy.

Online task allocation with dynamic arrivals therefore converts MRTA into a continuously operating decision loop. The fleet repeatedly observes robot and task states, processes new events, updates costs and constraints, selects or revises assignments, dispatches missions, and incorporates execution feedback. A robust implementation balances rapid response with assignment stability, future uncertainty, energy constraints, computational limits, and operational priorities, enabling multi-robot fleets to remain productive as demand changes in real time.

온라인 작업 할당(Online Task Allocation)은 운영을 시작하기 전에 모든 작업이 완전히 알려져 있지 않고 로봇이 이미 미션을 수행하는 동안에도 새로운 작업이 지속적으로 도착하는 다중 로봇 환경(Multi-Robot Environment)을 다룬다. 고정된 로봇과 작업 집합을 함께 최적화할 수 있는 정적 할당(Static Allocation)과 달리 온라인 할당기(Online Allocator)는 현재 이용 가능한 정보를 기반으로 의사결정을 내려야 한다. 따라서 새로운 주문, 검사 요청, 운송 미션, 긴급 작업 및 작업 취소가 언제든지 할당 문제를 변화시킬 수 있다.

시스템은 이벤트 기반 의사결정 과정(Event-Driven Decision Process)으로 모델링할 수 있다. 시간 \\(t\\)에서 플릿은 로봇 상태 \\(R(t)\\), 대기 중인 작업 집합 \\(Q(t)\\), 그리고 이미 실행 중인 할당 집합을 갖는다. 새로운 작업 \\(j\\)가 시간 \\(a_j\\)에 도착하면 할당기는 작업 대기열(Task Queue)을 갱신하고 즉시 할당할 것인지 또는 다음 의사결정 시점(Decision Epoch)까지 대기시킬 것인지를 결정한다. 이러한 반복 과정은 작업 할당을 일회성 최적화 문제에서 지속적인 플릿 제어(Continuous Fleet Control) 문제로 변화시킨다.

동적으로 도착하는 각 작업에는 위치, 시작 가능 시간(Release Time), 우선순위, 서비스 시간, 마감시간, 적재물 및 요구 능력과 같이 할당에 필요한 정보가 포함된다. 동시에 로봇은 이동하고 에너지를 소비하며 작업을 완료하고 충전을 시작하거나 운용 불가능한 상태가 되면서 플릿 상태 역시 계속 변화한다. 따라서 로봇 \\(i\\)를 작업 \\(j\\)에 할당하는 비용 \\(c_{ij}(t)\\)는 고정된 값이 아니라 시간에 따라 변화하며 최신 운영 상태를 기반으로 다시 계산해야 한다.

단순한 온라인 정책(Online Policy)은 새로운 작업이 도착할 때마다 현재 이용 가능한 로봇 가운데 가장 적합한 로봇에 즉시 할당한다. 이 방법은 의사결정 지연시간(Decision Latency)이 짧으며 작업들이 서로 독립적이고 플릿 용량이 충분할 때 효과적이다. 그러나 여러 중요한 작업이 비슷한 시간에 도착하면 즉각적인 할당이 비효율적일 수 있다. 낮은 우선순위의 작업에 로봇을 배정한 직후 중요한 작업이 발생하면 해당 로봇을 사용할 수 없게 되는데, 이는 미래의 작업 도착을 알 수 없는 상태에서 의사결정을 내려야 하는 온라인 할당의 근본적인 어려움을 보여준다.

대기열 기반 할당(Queue-Based Allocation)은 할당되지 않은 작업을 일시적으로 모아 정해진 의사결정 시점에 처리함으로써 이러한 문제를 완화한다. 모든 작업 도착에 개별적으로 반응하는 대신 몇 초마다 또는 대기열이 특정 임계값에 도달할 때 모든 대기 작업을 함께 최적화할 수 있다. 이러한 배치 전략(Batching Strategy)은 전체적으로 더 효율적인 조합을 찾을 기회를 제공하지만 작업의 대기 시간이 증가한다. 따라서 배치 간격(Batch Interval)은 응답성과 할당 품질 사이의 절충 관계를 형성한다.

이벤트 트리거 할당(Event-Triggered Allocation)은 또 다른 접근 방법을 제공한다. 새로운 고우선순위 작업이 도착하거나 로봇이 미션을 완료하고, 배터리 상태가 임계값을 넘거나, 로봇 고장이 발생하거나, 기존 작업이 취소될 때 재할당(Reallocation)을 시작할 수 있다. 일반적인 상태 변화가 발생할 때마다 반드시 복잡한 최적화를 실행할 필요는 없다. 의미 있는 플릿 이벤트와 작업 할당 결정을 연결하면 계산 부하를 줄이면서 미션 수행에 실질적인 영향을 미치는 상황에는 빠르게 대응할 수 있다.

동적 할당(Dynamic Allocation)에서는 이미 확정된 작업과 변경 가능한 작업을 구분해야 한다. 물리적으로 이미 수행 중인 작업은 일반적으로 보호되어야 하지만, 로봇에 할당되었으나 아직 시작되지 않은 작업은 상황 변화에 따라 재검토할 수 있다. 아직 할당되지 않은 작업은 완전히 유연하게 변경할 수 있다. 대기(Queued), 예약(Reserved), 디스패치(Dispatched), 수락(Accepted), 실행 중(Executing), 완료(Completed), 실패(Failed), 취소(Canceled)와 같은 명시적인 할당 상태를 사용하면 각 재할당 주기에서 모든 작업을 동일하게 이동 가능한 대상으로 처리하는 것을 방지할 수 있다.

재할당(Reassignment)은 새로운 기회를 제공하는 동시에 비용도 발생시킨다. 작업을 한 로봇에서 다른 로봇으로 변경하면 이동 시간을 줄이거나 변경된 우선순위를 만족시킬 수 있지만 지나치게 빈번한 재할당은 할당 스래싱(Assignment Thrashing)이라는 불안정성을 유발한다. 로봇이 실제 작업을 완료하지 못한 채 계속 새로운 목적지를 전달받을 수 있기 때문이다. 실제 온라인 할당기에서는 재할당 페널티(Reassignment Penalty), 최소 확정 기간(Minimum Commitment Period), 히스테리시스(Hysteresis), 개선 임계값(Improvement Threshold)을 적용하여 예상되는 개선 효과가 충분히 큰 경우에만 기존 할당을 변경하도록 한다.

동적 작업 도착 환경에서는 우선순위 관리(Priority Management)가 특히 중요하다. 긴급 작업, 안전 중요 작업(Safety-Critical Task), 생산 중단을 유발하는 작업은 일반 작업보다 우선하여 처리해야 할 수 있다. 우선순위는 가중 비용, 마감시간, 대기열 순서 또는 명시적인 서비스 등급(Service Class)을 통해 표현할 수 있다. 에이징 메커니즘(Aging Mechanism)을 이용하면 오랫동안 대기한 작업의 우선순위를 점진적으로 높여 고우선순위 요청이 지속적으로 도착하는 상황에서도 저우선순위 작업이 무기한 기아 상태(Starvation)에 빠지는 것을 방지할 수 있다.

로봇 가용성(Robot Availability)은 단순한 유휴 또는 작업 중 상태만으로 표현해서는 안 된다. 현재 미션을 수행 중인 로봇이 곧 새로운 작업 위치 근처에서 작업을 완료한다면 멀리 떨어져 있는 유휴 로봇보다 더 적합한 후보가 될 수 있다. 따라서 온라인 할당에서는 예상 가용 시간(Predicted Availability Time)과 예상 작업 완료 위치(Predicted Completion Position)를 활용할 수 있다. 이러한 미래 지향적 상태 표현은 로봇이 실제로 새로운 작업을 시작할 수 있는 시점과 위치를 평가함으로써 할당 품질을 향상시킨다.

배터리 상태(Battery State)는 또 다른 동적 제약조건을 형성한다. 할당기는 현재 충전 상태(State of Charge)뿐만 아니라 현재 미션, 후보 작업 및 이후 충전 위치까지 이동하는 데 필요한 예상 에너지 소비량도 고려해야 한다. 로봇이 지리적으로는 좋은 후보일 수 있지만 추가 작업을 수행할 경우 안전 잔량 임계값(Reserve Threshold)을 위반한다면 운영상 적합하지 않을 수 있다. 미래 작업을 수행하기 위한 예상 에너지가 부족해지면 충전 미션(Charging Mission) 자체를 동적으로 삽입할 수도 있다.

온라인 작업 할당은 로봇이 이동하는 동안 할당 비용이 계속 변하기 때문에 내비게이션(Navigation) 및 교통 상황과 밀접하게 연결된다. 혼잡, 차단된 통로, 엘리베이터 대기열, 제한 구역 및 임시 장애물은 예상 이동 시간을 크게 변화시킬 수 있다. 내비게이션 계층에서 로봇-작업 비용을 주기적으로 갱신하면 할당기가 정적인 기하학적 거리에 의존하지 않고 실제 운영 환경의 상태를 기반으로 의사결정을 내릴 수 있다.

온라인 프레임워크(Online Framework) 내부에서는 다양한 작업 할당 알고리즘을 사용할 수 있다. 탐욕적 선택(Greedy Selection)은 매우 빠른 의사결정을 제공하고, 경매 방식(Auction)은 동적으로 공지된 작업을 각 로봇이 평가하도록 하며, 매칭 알고리즘(Matching Algorithm)은 현재 대기 중인 작업을 배치 단위로 최적화할 수 있다. 보다 복잡한 제약조건을 고려해야 하는 경우에는 롤링 호라이즌(Rolling Horizon) 기반의 정수 또는 혼합 정수 최적화를 적용할 수 있다. 따라서 온라인 아키텍처는 특정 최적화 알고리즘 하나를 요구하는 것이 아니라 언제, 어떻게 할당을 갱신할 것인지를 정의한다.

롤링 호라이즌 최적화(Rolling-Horizon Optimization)는 제한적인 미래 정보를 사용할 수 있을 때 특히 유용하다. 각 의사결정 시점마다 할당기는 유한한 계획 구간(Finite Horizon) 안에서 알려진 작업을 최적화하고 가까운 미래의 결정만 확정하며 덜 긴급한 결정은 이후로 연기한다. 새로운 정보가 도착하면 계획 구간이 앞으로 이동하고 문제를 다시 해결한다. 이러한 전략은 작업 수요와 로봇 상태가 지속적으로 변하는 환경에서 장기 일정이 계속 유효할 것이라고 가정하는 문제를 피할 수 있다.

예측(Prediction)을 활용하면 온라인 의사결정을 더욱 향상시킬 수 있다. 과거 주문 패턴, 생산 일정, 교통 통계 및 작업 도착 모델(Task Arrival Model)을 이용하면 정확한 미래 작업을 알 수 없더라도 미래 수요를 추정할 수 있다. 할당기는 고우선순위 작업이 발생할 가능성이 높은 위치 근처에 일부 로봇을 의도적으로 대기시킬 수 있다. 이러한 선제적 할당(Anticipatory Allocation)은 현재의 효율성 일부를 미래의 응답성을 위해 교환하며 반응형 스케줄링(Reactive Scheduling)과 예측형 플릿 최적화(Predictive Fleet Optimization)를 연결한다.

통신 지연(Communication Delay)과 분산 상태 일관성(Distributed State Consistency) 역시 고려해야 한다. 플릿 관리자가 로봇 상태가 생성된 후 수백 밀리초가 지나서 정보를 받을 수 있으며 서로 다른 외부 시스템에서 두 작업이 거의 동시에 도착할 수도 있다. 타임스탬프가 적용된 이벤트(Timestamped Event), 단조 증가 작업 버전(Monotonic Task Version), 할당 식별자, 승인(Acknowledgment), 트랜잭션 기반 상태 전이(Transactional State Transition)를 이용하면 중복 디스패치나 오래된 정보를 기반으로 한 의사결정을 방지할 수 있다.

실패 처리(Failure Handling)는 온라인 아키텍처에 자연스럽게 통합된다. 로봇의 연결이 끊기거나 고장이 보고되면 사람의 개입이 필요한 실행 상태가 아닌 경우 완료되지 않은 작업을 다시 할당 대기열로 반환할 수 있다. 이후 갱신된 플릿 상태를 기반으로 다른 로봇을 평가한다. 마찬가지로 작업이 취소되면 예약된 로봇이 해제되고, 작업 지연이 발생하면 이후 작업의 재스케줄링(Rescheduling)이 시작될 수 있다. 따라서 복구(Recovery)는 별도의 완전히 독립적인 기능이 아니라 또 하나의 작업 할당 이벤트로 처리된다.

확장성(Scalability)은 각 이벤트 이후 얼마나 많은 후보 관계를 다시 평가하는지에 크게 영향을 받는다. 모든 이벤트마다 모든 로봇과 모든 작업의 조합을 재최적화하면 대규모 플릿에서는 계산 비용이 지나치게 증가할 수 있다. 후보 필터링(Candidate Filtering)을 이용하여 호환 가능한 로봇, 인접 구역의 로봇, 적합한 로봇 클래스 또는 제한된 수의 최상위 후보만 고려할 수 있다. 계층적 할당(Hierarchical Allocation)을 이용하면 먼저 사이트 또는 구역을 선택하고 이후 로컬 영역에서 세부적인 할당을 수행하여 계산량과 통신 요구량을 모두 줄일 수 있다.

성능 평가는 개별 할당의 비용만이 아니라 동적 지표(Dynamic Metric)를 포함해야 한다. 중요한 평가 항목에는 작업 응답 시간, 대기열 대기 시간, 완료 시간, 처리량(Throughput), 마감시간 위반율, 재할당 빈도, 로봇 활용률, 에너지 소비량, 기아 발생률(Starvation Rate), 계산 지연시간(Computational Latency) 등이 포함된다. 평균 성능이 좋아 보이더라도 일부 작업에서 극단적으로 긴 대기 시간이 발생하는 것은 허용되지 않을 수 있으므로 꼬리 구간 성능(Tail Behavior) 역시 중요하다.

시뮬레이션(Simulation)에서는 고정된 작업 집합만 시험하는 것이 아니라 현실적인 작업 도착 과정(Task Arrival Process)을 재현해야 한다. 수요 급증(Burst Demand), 우선순위 변경, 로봇 고장, 충전 이벤트, 혼잡, 통신 지연 및 작업 취소를 포함하면 정적 벤치마크에서 발견하기 어려운 동작을 확인할 수 있다. 동일한 작업 도착 흐름을 이용하여 즉시 디스패치(Immediate Dispatch), 주기적 배치(Periodic Batching), 이벤트 트리거 할당 및 롤링 호라이즌 최적화를 비교하면 적절한 온라인 할당 정책을 선택할 수 있는 실용적인 근거를 마련할 수 있다.

따라서 동적 작업 도착을 고려한 온라인 작업 할당(Online Task Allocation with Dynamic Arrivals)은 MRTA를 지속적으로 동작하는 의사결정 루프(Decision Loop)로 전환한다. 플릿은 로봇과 작업 상태를 반복적으로 관찰하고 새로운 이벤트를 처리하며 비용과 제약조건을 갱신하고, 할당을 선택하거나 수정한 후 미션을 디스패치하고 실행 피드백을 다시 반영한다. 강건한 구현은 빠른 응답성과 할당 안정성, 미래의 불확실성, 에너지 제약, 계산 한계 및 운영 우선순위 사이에서 균형을 유지함으로써 실시간으로 수요가 변화하는 환경에서도 다중 로봇 플릿이 높은 생산성을 유지할 수 있도록 한다.

##  

## 02.06 Multi Skill Task Allocation Heterogeneous Fleet [w/Code]

![](images/image6.png){width="7.268055555555556in" height="7.268055555555556in"}

Multi-skill task allocation extends the conventional Multi-Robot Task Allocation problem to fleets in which robots are not interchangeable. A heterogeneous fleet may contain transport AMRs, mobile manipulators, inspection robots, towing platforms, aerial robots, or specialized service robots. Each platform possesses a different combination of mobility, sensing, manipulation, payload, communication, endurance, and environmental capabilities, so allocation must match task requirements with compatible robot skills.

A useful formulation represents every robot \\(r_i\\) with a capability vector \\(S_i=[s_{i1},s_{i2},\\ldots,s_{ik}]\\). Individual elements may describe payload capacity, manipulation ability, sensing modality, navigation capability, operating environment, certification, or other skills. Each task \\(t_j\\) is similarly associated with a requirement vector \\(Q_j=[q_{j1},q_{j2},\\ldots,q_{jk}]\\), allowing the allocator to compare available capabilities with required capabilities before evaluating assignment cost.

Capability representation can contain both binary and continuous properties. A robot either possesses a thermal camera or does not, which can be represented as a binary skill. Payload capacity, manipulator reach, positioning accuracy, battery endurance, maximum speed, or sensor range are naturally represented numerically. Categorical properties such as indoor, outdoor, clean-room, hazardous-area, or stair-capable operation can be encoded through explicit compatibility rules or capability classes.

Eligibility filtering is normally performed before optimization. If task \\(j\\) requires capabilities that robot \\(i\\) cannot provide, the robot-task pair is declared infeasible and removed from the candidate set. Conceptually, an eligibility function \\(e_{ij}\\in\\{0,1\\}\\) can indicate whether the assignment is permitted. This prevents an optimizer from selecting a physically impossible robot merely because its travel distance or nominal assignment cost is attractive.

Exact capability matching is not always sufficient because robots can possess different performance levels for the same skill. Two inspection robots may both carry cameras, but one may provide higher resolution, thermal sensing, or more accurate localization. The allocator can therefore introduce capability quality or suitability scores. Assignment utility then reflects not only whether a robot can perform the task, but how effectively it is expected to perform it under the current conditions.

Tasks themselves may require multiple skills simultaneously. An inspection mission could require outdoor navigation, high-resolution imaging, thermal sensing, and precise localization, while a material-handling task could require high payload, manipulation, and docking capabilities. A single robot may satisfy the complete requirement set, or the system may need to determine whether several robots can collectively provide the required capabilities.

This distinction introduces single-robot and coalition-based task allocation. In a single-robot assignment, one platform must contain every required skill. In coalition allocation, a group of robots jointly satisfies the task requirement. For example, one robot may provide transportation while another provides manipulation or specialized sensing. Coalition formation greatly expands the decision space because the allocator must evaluate combinations of robots rather than individual candidates.

Skill complementarity is therefore an important concept in heterogeneous fleets. Robots should not be evaluated only by independent capability scores but also by how their skills combine. Two individually unsuitable robots may form a feasible team when their capabilities are complementary. However, coalition tasks also require synchronization, communication, spatial coordination, and compatible execution timing, so the benefit of combining skills must be weighed against additional coordination cost.

The assignment objective can combine capability suitability with conventional operational costs. A generalized cost \\(c_{ij}\\) may include travel time, energy consumption, workload, task priority, and capability mismatch penalties. Alternatively, a utility function can reward higher skill compatibility while penalizing distance and resource consumption. The weighting between capability quality and operational efficiency determines whether the fleet favors the most specialized robot or a sufficiently capable robot that can respond more efficiently.

Resource scarcity strongly influences multi-skill allocation. Some specialized capabilities may exist on only one or two robots within the entire fleet. Assigning such a robot to an ordinary task can make a later specialized mission impossible. Scarcity-aware allocation therefore assigns an opportunity cost to rare skills. General-purpose tasks are preferably given to common robot classes when doing so preserves specialized resources for missions that genuinely require them.

Task priority interacts with capability scarcity. A high-priority task requiring a unique sensor or manipulator may justify reserving the only compatible robot even if that robot is currently performing lower-value work. Conversely, continuously reserving specialized robots for hypothetical future demand can reduce utilization. Practical systems therefore balance current task value, predicted demand, skill scarcity, and the cost of keeping specialized resources available.

Robot state changes can temporarily modify capability availability. A mobile manipulator may technically possess manipulation capability but become unable to accept a manipulation task because its gripper has failed. A sensor may be degraded, payload space may already be occupied, or battery state may prevent outdoor operation over a long route. Capability models should therefore distinguish static platform specifications from dynamic operational capabilities derived from current health and resource state.

Tool-changing and modular robots make the allocation problem more complex. A robot may acquire a required skill by visiting a tool station and attaching a gripper, sensor, or other module. The allocator can treat reconfiguration as an additional action with associated time, energy, and resource costs. A robot that is initially incompatible with a task may become feasible if the benefit of reconfiguration exceeds the cost of preparing another platform.

Heterogeneous fleets also require normalization of performance measures. Travel speed, payload, endurance, sensing quality, and execution time can differ significantly across robot classes, so raw values should not be compared without context. Cost models can convert these characteristics into common operational measures such as predicted completion time, energy expenditure, service quality, or economic cost, enabling meaningful comparisons between fundamentally different platforms.

Centralized allocation is useful when a fleet manager maintains a global capability registry and can compare all robots consistently. Each robot reports its static specifications and dynamic state, while the allocator maintains task requirement profiles. This architecture simplifies fleet-wide optimization and resource reservation. However, the capability model must remain synchronized with actual robot configuration to prevent assignments based on outdated information.

Distributed approaches allow individual robots to evaluate task requirements and submit bids based on their own capabilities. This is particularly attractive when robot types are highly diverse or supplied by different vendors. Each platform can internally determine whether a task is feasible and estimate its execution cost without exposing every implementation detail. A fleet-level auction or negotiation mechanism can then compare standardized bids and select appropriate robots or coalitions.

Interoperability becomes critical when heterogeneous robots use different software stacks, interfaces, and capability descriptions. A common task and capability ontology can define standardized concepts such as transport, inspect, manipulate, tow, dock, charge, or localize. The allocation layer can operate on these abstract skills while robot-specific adapters translate selected tasks into platform-specific commands. This separation reduces dependence on individual hardware implementations.

Multi-skill allocation is closely connected with scheduling because specialized robots can become bottleneck resources. If several tasks require the same rare capability, selecting the correct robot is only part of the problem; the system must also determine execution order and timing. Capability-aware scheduling can reduce idle periods, avoid unnecessary tool changes, and ensure that high-priority missions gain timely access to scarce resources.

Online operation introduces additional complexity because both task demand and available capabilities change dynamically. Newly arriving tasks may require rare skills, robots may fail, modules may be exchanged, and maintenance can remove specialized platforms from service. The allocator must continuously update eligibility, suitability, and scarcity information. Reallocation may be necessary when a previously feasible robot loses a required capability during operation.

Learning methods can support capability estimation when performance cannot be described accurately by fixed specifications. Historical execution data can estimate how long different robot classes take to complete particular task types, how energy consumption varies with payload, or how sensing quality changes with environmental conditions. These learned models can improve cost and suitability predictions while explicit safety and capability constraints continue to define hard feasibility boundaries.

Simulation is especially valuable for heterogeneous fleet design because allocation performance depends on fleet composition as well as algorithm quality. By varying the number of transport robots, manipulators, inspection platforms, and other specialized units, designers can identify capability bottlenecks and underutilized resources. Simulation can therefore support both real-time task allocation policy design and longer-term decisions about which robot types should be added to the fleet.

Evaluation should measure more than total travel distance. Relevant metrics include task completion time, capability utilization, specialized-resource utilization, percentage of tasks successfully matched, coalition formation frequency, deadline satisfaction, energy consumption, reconfiguration overhead, and the number of tasks rejected because required skills are unavailable. These measures reveal whether the fleet has an appropriate capability mix as well as whether the allocator uses it effectively.

Multi-skill task allocation ultimately treats robot capability as a first-class element of fleet intelligence rather than a secondary assignment constraint. By combining capability models, task requirements, eligibility filtering, suitability scoring, scarcity awareness, coalition formation, dynamic robot state, and operational cost, the allocation system can select not merely the nearest available robot but the most appropriate resource for each mission. This capability-aware approach is fundamental to scalable heterogeneous multi-robot fleets.

다중 스킬 작업 할당(Multi-Skill Task Allocation)은 로봇들이 서로 동일하게 대체될 수 없는 플릿(Fleet)을 대상으로 기존의 다중 로봇 작업 할당(Multi-Robot Task Allocation, MRTA) 문제를 확장한 것이다. 이종 플릿(Heterogeneous Fleet)은 운송 AMR, 모바일 매니퓰레이터(Mobile Manipulator), 검사 로봇(Inspection Robot), 견인 플랫폼(Towing Platform), 공중 로봇(Aerial Robot) 또는 특수 서비스 로봇(Specialized Service Robot)으로 구성될 수 있다. 각 플랫폼은 이동, 센싱, 조작, 적재, 통신, 운용 지속시간 및 환경 대응 능력의 조합이 서로 다르므로 작업 할당은 작업 요구사항과 호환되는 로봇 스킬(Robot Skill)을 일치시켜야 한다.

유용한 정식화(Formulation)에서는 각 로봇 \\(r_i\\)를 능력 벡터(Capability Vector) \\(S_i=[s_{i1},s_{i2},\\ldots,s_{ik}]\\)로 표현한다. 개별 요소는 적재 용량, 조작 능력, 센싱 방식, 내비게이션 능력, 운영 환경, 인증 또는 기타 스킬을 나타낼 수 있다. 각 작업 \\(t_j\\) 역시 요구사항 벡터(Requirement Vector) \\(Q_j=[q_{j1},q_{j2},\\ldots,q_{jk}]\\)와 연결할 수 있으며, 이를 통해 할당기는 할당 비용을 평가하기 전에 이용 가능한 능력과 요구되는 능력을 비교할 수 있다.

능력 표현(Capability Representation)은 이진 속성과 연속적인 속성을 모두 포함할 수 있다. 로봇이 열화상 카메라(Thermal Camera)를 보유하는지 여부는 이진 스킬(Binary Skill)로 표현할 수 있다. 적재 용량, 매니퓰레이터 도달거리, 위치 정밀도, 배터리 운용시간, 최대 속도 또는 센서 범위는 수치적으로 표현하는 것이 자연스럽다. 실내, 실외, 클린룸(Clean Room), 위험 구역(Hazardous Area), 계단 주행 가능 여부와 같은 범주형 속성은 명시적인 호환성 규칙 또는 능력 클래스로 표현할 수 있다.

적격성 필터링(Eligibility Filtering)은 일반적으로 최적화를 수행하기 전에 적용된다. 작업 \\(j\\)가 요구하는 능력을 로봇 \\(i\\)가 제공할 수 없다면 해당 로봇-작업 조합은 실행 불가능(Infeasible)한 것으로 판단하여 후보 집합에서 제거한다. 개념적으로 적격성 함수(Eligibility Function) \\(e_{ij}\\in\\{0,1\\}\\)를 사용하여 해당 할당이 허용되는지를 나타낼 수 있다. 이를 통해 이동 거리나 명목 할당 비용이 유리하다는 이유만으로 최적화기가 물리적으로 작업을 수행할 수 없는 로봇을 선택하는 것을 방지한다.

정확한 능력 일치(Exact Capability Matching)만으로는 항상 충분하지 않다. 동일한 스킬을 가진 로봇이라도 성능 수준이 서로 다를 수 있기 때문이다. 두 검사 로봇이 모두 카메라를 탑재하고 있더라도 한 로봇이 더 높은 해상도, 열화상 센싱 또는 더 정확한 위치 추정 능력을 제공할 수 있다. 따라서 할당기는 능력 품질(Capability Quality) 또는 적합도 점수(Suitability Score)를 도입할 수 있다. 이를 통해 로봇이 작업을 수행할 수 있는지뿐만 아니라 현재 조건에서 얼마나 효과적으로 수행할 수 있는지를 할당 효용에 반영할 수 있다.

작업 자체가 동시에 여러 스킬을 요구할 수도 있다. 검사 미션은 실외 내비게이션, 고해상도 영상, 열화상 센싱 및 정밀 위치 추정을 동시에 요구할 수 있으며, 물류 취급 작업은 높은 적재 능력, 조작 및 도킹 능력을 요구할 수 있다. 하나의 로봇이 전체 요구 능력을 만족할 수도 있지만, 경우에 따라 시스템은 여러 로봇이 협력하여 필요한 능력을 제공할 수 있는지를 판단해야 한다.

이러한 차이는 단일 로봇 및 연합 기반 작업 할당(Single-Robot and Coalition-Based Task Allocation)으로 이어진다. 단일 로봇 할당에서는 하나의 플랫폼이 요구되는 모든 스킬을 보유해야 한다. 연합 할당(Coalition Allocation)에서는 여러 로봇으로 구성된 그룹이 공동으로 작업 요구사항을 만족한다. 예를 들어 한 로봇은 운송을 담당하고 다른 로봇은 조작 또는 특수 센싱을 담당할 수 있다. 연합 형성(Coalition Formation)은 개별 로봇이 아니라 로봇 조합까지 평가해야 하므로 의사결정 공간을 크게 확장한다.

따라서 스킬 상보성(Skill Complementarity)은 이종 플릿에서 중요한 개념이다. 로봇을 독립적인 능력 점수만으로 평가해서는 안 되며 각 로봇의 스킬이 서로 어떻게 결합되는지도 고려해야 한다. 개별적으로는 적합하지 않은 두 로봇이라도 서로의 능력이 상호 보완적이라면 실행 가능한 팀을 구성할 수 있다. 그러나 연합 작업은 동기화, 통신, 공간적 조정 및 실행 시간의 호환성도 요구하므로 스킬 결합의 이점과 추가적인 조정 비용(Coordination Cost)을 함께 평가해야 한다.

할당 목적 함수(Assignment Objective)는 능력 적합도와 기존의 운영 비용을 결합할 수 있다. 일반화된 비용 \\(c_{ij}\\)에는 이동 시간, 에너지 소비량, 작업 부하, 작업 우선순위 및 능력 불일치 페널티를 포함할 수 있다. 반대로 효용 함수(Utility Function)를 사용하여 높은 스킬 호환성에 보상을 제공하면서 거리와 자원 소비를 페널티로 부과할 수도 있다. 능력 품질과 운영 효율성 사이의 가중치에 따라 플릿이 가장 전문화된 로봇을 선택할지 또는 충분한 능력을 갖추면서 더 효율적으로 대응할 수 있는 로봇을 선택할지가 결정된다.

자원 희소성(Resource Scarcity)은 다중 스킬 할당에 큰 영향을 미친다. 일부 특수 능력은 전체 플릿에서 한두 대의 로봇만 보유하고 있을 수 있다. 이러한 로봇을 일반 작업에 할당하면 이후 특수 미션을 수행할 수 없게 될 수 있다. 따라서 희소성 인식 할당(Scarcity-Aware Allocation)은 희귀 스킬에 기회비용(Opportunity Cost)을 부여한다. 특수 자원을 실제로 필요로 하는 미션을 위해 보존할 수 있다면 일반 작업은 가능한 한 일반적인 로봇 클래스에 할당하는 것이 바람직하다.

작업 우선순위(Task Priority)는 능력 희소성과 상호작용한다. 고유한 센서나 매니퓰레이터를 요구하는 고우선순위 작업의 경우 해당 능력을 가진 유일한 로봇이 현재 낮은 가치의 작업을 수행하고 있더라도 그 로봇을 예약하는 것이 정당화될 수 있다. 반대로 발생 여부가 불확실한 미래 작업을 위해 특수 로봇을 계속 예약하면 활용률이 낮아질 수 있다. 따라서 실제 시스템은 현재 작업 가치, 예상 수요, 스킬 희소성 및 특수 자원을 가용 상태로 유지하는 비용 사이에서 균형을 유지해야 한다.

로봇 상태(Robot State)의 변화는 능력 가용성(Capability Availability)을 일시적으로 변경할 수 있다. 모바일 매니퓰레이터가 기술적으로 조작 능력을 보유하고 있더라도 그리퍼(Gripper)가 고장나면 조작 작업을 수행할 수 없다. 센서 성능이 저하되거나 적재 공간이 이미 사용 중일 수도 있으며 배터리 상태 때문에 장거리 실외 작업을 수행할 수 없을 수도 있다. 따라서 능력 모델은 정적인 플랫폼 사양(Static Platform Specification)과 현재의 상태 및 자원을 기반으로 결정되는 동적 운영 능력(Dynamic Operational Capability)을 구분해야 한다.

도구 교환(Tool Changing) 및 모듈형 로봇(Modular Robot)은 할당 문제를 더욱 복잡하게 만든다. 로봇이 도구 스테이션(Tool Station)을 방문하여 그리퍼, 센서 또는 다른 모듈을 장착함으로써 필요한 스킬을 획득할 수 있다. 할당기는 재구성(Reconfiguration)을 시간, 에너지 및 자원 비용이 수반되는 추가 행동으로 처리할 수 있다. 처음에는 작업과 호환되지 않았던 로봇이라도 재구성 비용이 다른 플랫폼을 준비하는 비용보다 낮다면 실행 가능한 후보가 될 수 있다.

이종 플릿에서는 성능 지표의 정규화(Normalization)도 필요하다. 이동 속도, 적재 능력, 운용 지속시간, 센싱 품질 및 작업 수행 시간은 로봇 클래스마다 크게 다를 수 있으므로 원시값(Raw Value)을 맥락 없이 직접 비교해서는 안 된다. 비용 모델은 이러한 특성을 예상 완료 시간, 에너지 소비량, 서비스 품질 또는 경제적 비용과 같은 공통 운영 지표로 변환하여 근본적으로 서로 다른 플랫폼을 의미 있게 비교할 수 있도록 한다.

중앙집중형 할당(Centralized Allocation)은 플릿 관리자가 전역 능력 레지스트리(Global Capability Registry)를 유지하면서 모든 로봇을 일관된 기준으로 비교할 수 있는 경우 유용하다. 각 로봇은 정적 사양과 동적 상태를 보고하고 할당기는 작업 요구사항 프로파일(Task Requirement Profile)을 유지한다. 이러한 아키텍처는 플릿 전체 최적화와 자원 예약을 단순화한다. 그러나 실제 로봇 구성과 능력 모델이 지속적으로 동기화되어야 오래된 정보를 기반으로 작업이 할당되는 것을 방지할 수 있다.

분산형 접근 방법(Distributed Approach)에서는 개별 로봇이 작업 요구사항을 평가하고 자신의 능력을 기반으로 입찰값(Bid)을 제출할 수 있다. 이는 로봇 유형이 매우 다양하거나 여러 공급업체(Vendor)의 플랫폼으로 구성된 경우 특히 유용하다. 각 플랫폼은 모든 내부 구현 정보를 공개하지 않고도 자체적으로 작업 실행 가능성을 판단하고 수행 비용을 추정할 수 있다. 이후 플릿 수준의 경매(Auction) 또는 협상 메커니즘(Negotiation Mechanism)이 표준화된 입찰값을 비교하여 적합한 로봇 또는 로봇 연합을 선택할 수 있다.

이종 로봇이 서로 다른 소프트웨어 스택(Software Stack), 인터페이스 및 능력 표현 방식을 사용할 경우 상호운용성(Interoperability)이 매우 중요해진다. 공통 작업 및 능력 온톨로지(Common Task and Capability Ontology)를 이용하여 운송, 검사, 조작, 견인, 도킹, 충전, 위치 추정과 같은 표준화된 개념을 정의할 수 있다. 할당 계층은 이러한 추상화된 스킬을 기반으로 동작하고 로봇별 어댑터(Robot-Specific Adapter)가 선택된 작업을 플랫폼별 명령으로 변환한다. 이러한 분리를 통해 특정 하드웨어 구현에 대한 의존성을 줄일 수 있다.

다중 스킬 할당은 특수 로봇이 병목 자원(Bottleneck Resource)이 될 수 있기 때문에 스케줄링(Scheduling)과도 밀접하게 연결된다. 여러 작업이 동일한 희귀 능력을 요구하는 경우 올바른 로봇을 선택하는 것만으로는 충분하지 않으며 작업의 실행 순서와 시점도 결정해야 한다. 능력 인식 스케줄링(Capability-Aware Scheduling)을 적용하면 유휴 시간을 줄이고 불필요한 도구 교환을 방지하며 고우선순위 미션이 희소 자원에 적시에 접근할 수 있도록 할 수 있다.

온라인 운영(Online Operation)은 작업 수요와 이용 가능한 능력이 모두 동적으로 변화하기 때문에 추가적인 복잡성을 발생시킨다. 새롭게 도착하는 작업이 희귀 스킬을 요구할 수 있고, 로봇이 고장나거나 모듈이 교체되며 유지보수로 특수 플랫폼이 운용에서 제외될 수 있다. 따라서 할당기는 적격성, 적합도 및 희소성 정보를 지속적으로 갱신해야 한다. 이전에는 실행 가능했던 로봇이 운영 중 필요한 능력을 상실하면 재할당(Reallocation)이 필요할 수 있다.

성능을 고정된 사양만으로 정확하게 설명하기 어려운 경우 학습 방법(Learning Method)을 활용하여 능력을 추정할 수 있다. 과거 실행 데이터를 이용하면 서로 다른 로봇 클래스가 특정 작업 유형을 완료하는 데 필요한 시간, 적재물에 따른 에너지 소비 변화 또는 환경 조건에 따른 센싱 품질 변화를 추정할 수 있다. 이러한 학습 모델은 비용 및 적합도 예측을 개선할 수 있으며, 명시적인 안전 및 능력 제약조건은 계속해서 반드시 지켜야 하는 실행 가능성 경계(Hard Feasibility Boundary)를 정의한다.

시뮬레이션(Simulation)은 할당 성능이 알고리즘 품질뿐만 아니라 플릿 구성(Fleet Composition)에도 영향을 받기 때문에 이종 플릿 설계에서 특히 중요하다. 운송 로봇, 매니퓰레이터, 검사 플랫폼 및 기타 특수 장비의 수를 변화시키면서 능력 병목(Capability Bottleneck)과 활용률이 낮은 자원을 식별할 수 있다. 따라서 시뮬레이션은 실시간 작업 할당 정책 설계뿐만 아니라 장기적으로 어떤 종류의 로봇을 플릿에 추가해야 하는지를 결정하는 데도 활용할 수 있다.

평가에서는 전체 이동 거리만을 측정해서는 안 된다. 주요 지표에는 작업 완료 시간, 능력 활용률(Capability Utilization), 특수 자원 활용률, 성공적으로 매칭된 작업의 비율, 연합 형성 빈도, 마감시간 준수율, 에너지 소비량, 재구성 오버헤드(Reconfiguration Overhead), 필요한 스킬을 사용할 수 없어 거부된 작업 수 등이 포함된다. 이러한 지표를 통해 플릿이 적절한 능력 조합을 갖추고 있는지뿐만 아니라 할당기가 이러한 능력을 효과적으로 활용하고 있는지도 평가할 수 있다.

궁극적으로 다중 스킬 작업 할당(Multi-Skill Task Allocation)은 로봇 능력을 단순한 부가적인 할당 제약조건이 아니라 플릿 지능(Fleet Intelligence)의 핵심 요소로 취급한다. 능력 모델, 작업 요구사항, 적격성 필터링, 적합도 평가, 희소성 인식, 연합 형성, 동적 로봇 상태 및 운영 비용을 결합함으로써 할당 시스템은 단순히 가장 가까운 가용 로봇이 아니라 각 미션에 가장 적합한 자원을 선택할 수 있다. 이러한 능력 인식 접근 방법(Capability-Aware Approach)은 확장 가능한 이종 다중 로봇 플릿(Scalable Heterogeneous Multi-Robot Fleet)을 구현하기 위한 핵심 기반이다.

##  

## 02.07 Battery Aware Task Allocation and Charging Plan [w/Code]

![](images/image7.png){width="7.268055555555556in" height="7.268055555555556in"}

Battery-aware task allocation integrates energy management directly into Multi-Robot Task Allocation rather than treating charging as an independent maintenance activity. Every assignment changes not only robot position and workload but also the energy available for future missions. A fleet allocator must therefore determine whether a robot can safely complete a candidate task, preserve an operational reserve, reach a charging resource when necessary, and remain productive over the planning horizon.

The fundamental state variable is the robot State of Charge (SoC), usually expressed as a percentage or normalized energy level. For robot \\(r_i\\), the allocator maintains an estimate \\(SoC_i(t)\\) together with battery capacity, minimum reserve threshold, charging status, and predicted consumption. Because measured SoC can contain estimation error, practical systems should distinguish nominal remaining energy from energy that can safely be committed to future tasks.

Task energy cost depends on more than travel distance. A candidate mission may include travel to the task, payload transport, manipulation or sensing, waiting, communication, auxiliary computing, and movement after task completion. A useful prediction therefore considers \\(E_{ij}=E_{travel}+E_{task}+E_{aux}+E_{reserve}\\). Terrain, velocity, payload, temperature, stopping frequency, and robot type can further modify the energy required for the same nominal mission.

Energy feasibility should be checked before a robot becomes an assignment candidate. If the predicted energy required to reach task \\(j\\), execute it, and subsequently reach a safe charging location exceeds the robot\'s usable energy, the robot-task pair should be rejected. This is stronger than simply applying a high cost to a low-battery robot because it establishes a hard feasibility boundary that prevents assignments likely to strand a robot during operation.

Battery information can also enter the allocation objective as a soft cost. Two robots may both have enough energy to execute a task, but assigning the robot with a critically reduced reserve may create future scheduling problems. A battery penalty can therefore increase as SoC approaches a defined threshold. The allocator can prefer robots with healthier reserves while still permitting low-energy robots to perform short or urgent tasks when operational conditions justify it.

Charging can be represented as a fleet task rather than as an external process. A charging mission contains a charger destination, expected travel time, charging duration, target SoC, and resource availability. Once charging is modeled in the same planning framework as productive work, the allocator can decide when a robot should stop accepting tasks, which charger it should use, and how much energy it should recover before returning to service.

Simple charging policies rely on fixed thresholds. For example, a robot may enter charging mode when SoC falls below a lower threshold and return to operation after reaching an upper threshold. This hysteresis prevents rapid switching between work and charging states. Although threshold policies are easy to implement, they can cause many robots to request charging simultaneously when their batteries have experienced similar duty cycles.

Opportunity charging provides a more flexible strategy. Instead of waiting until the battery becomes low, a robot can recharge during naturally occurring idle periods, production breaks, queue delays, or when it passes near an available charger. Short charging sessions can reduce the probability of long future interruptions. However, excessive opportunity charging may occupy chargers unnecessarily, so charging benefit must be compared with expected task demand and resource contention.

Charger assignment creates a resource-allocation problem of its own. A fleet may contain multiple chargers with different locations, power levels, connector types, or robot compatibility. Selecting the geographically closest charger is not always optimal if that charger is occupied or has a long queue. The planner should consider travel time, expected waiting time, charging rate, compatibility, and the robot\'s future task location when selecting a charging station.

Charging-station capacity must be explicitly considered when many robots share limited infrastructure. If several robots are scheduled to charge simultaneously at a station with only a few charging ports, queues can develop and reduce fleet availability. Reservation systems can allocate charger time windows before robots arrive. This converts charging from an uncontrolled reaction to low SoC into a coordinated resource-scheduling process integrated with fleet operations.

Task allocation and charging planning are tightly coupled. Assigning a distant task consumes additional energy and may force an earlier charging stop, while assigning a task near a charger can create an efficient transition into charging. The cost of an assignment should therefore include its downstream energy consequences. A locally inexpensive task may be globally undesirable if it causes a long detour to recharge immediately afterward.

Battery-aware allocation can also balance energy consumption across the fleet. Repeatedly selecting the same highly efficient or conveniently located robots may cause their batteries to cycle more frequently than others. Introducing workload and battery-usage balancing terms distributes missions more evenly. This can improve fleet availability and may reduce uneven battery aging, although utilization balancing should not override urgent operational requirements.

Battery State of Health (SoH) adds a longer-term dimension to the problem. Two robots with the same SoC may have different usable capacities because their batteries have aged differently. Energy prediction should therefore use effective battery capacity rather than nominal capacity whenever reliable SoH information is available. Aging-aware allocation can also avoid repeatedly imposing high-power or deep-discharge cycles on already degraded batteries.

Dynamic task arrivals require continuous revision of the energy plan. A robot scheduled to charge may be temporarily reassigned to an urgent task if sufficient reserve exists, while unexpected task bursts may require postponing nonessential charging. Conversely, slower-than-expected execution or increased energy consumption may force an earlier charging decision. Online allocation therefore updates predicted energy trajectories whenever meaningful fleet events occur.

Prediction over a planning horizon improves charging decisions beyond simple thresholds. If a robot has 45 percent SoC but several energy-intensive tasks are expected soon, charging now may be preferable to waiting until the battery reaches 20 percent. Conversely, a robot at relatively low SoC may continue working if upcoming demand is light and an available charger is nearby. Predictive planning connects present battery state with expected future workload.

Rolling-horizon optimization is well suited to this problem because both task demand and battery state evolve continuously. At each planning cycle, the system considers available robots, waiting tasks, charger states, predicted energy consumption, and a limited future horizon. It commits near-term task and charging decisions while leaving later choices flexible. The optimization is repeated as robots move, tasks arrive, and charging conditions change.

Energy uncertainty must be treated conservatively. Predicted consumption can differ from actual consumption because of congestion, payload variation, terrain, temperature, detours, or battery-model error. A safety reserve prevents the planner from consuming all theoretically available energy. The required reserve may vary by operating environment, with larger margins appropriate when chargers are distant or mission interruption carries significant risk.

Failures in charging infrastructure must also be considered. A charger may become unavailable, communication with a station may fail, or docking may not succeed. Robots should maintain sufficient reserve to reach an alternative charger whenever practical. Charger health and reservation status should therefore form part of fleet state, and failed charging attempts should trigger replanning rather than allowing the robot to continue consuming energy without a recovery strategy.

Different robot classes require different energy models in heterogeneous fleets. A transport AMR, mobile manipulator, towing robot, and inspection platform can have substantially different battery capacities and consumption profiles. Payload and manipulation may dominate one platform\'s energy use while locomotion dominates another. Battery-aware allocation should therefore use robot-specific models rather than applying a uniform percentage-based policy across the entire fleet.

Simulation provides an effective environment for tuning battery and charging policies. Task intensity, charger count, charging power, battery capacity, reserve thresholds, and opportunity-charging rules can be varied systematically. Stress scenarios involving task bursts, charger failures, long queues, degraded batteries, or high-energy missions reveal whether the fleet can maintain operation without excessive charging congestion or mission rejection.

Evaluation should consider fleet productivity together with energy performance. Relevant metrics include task throughput, mission completion rate, average and minimum SoC, charger utilization, charging queue time, energy consumed per task, time spent charging, number of energy-infeasible assignments, emergency charging events, and fleet availability. Battery degradation indicators can also be monitored when long-term lifecycle performance is important.

Battery-aware task allocation and charging planning therefore form a unified energy-management problem. The allocator must connect task demand, robot capability, predicted energy consumption, SoC and SoH, charging infrastructure, safety reserves, and future workload within one decision loop. By treating energy as a continuously managed fleet resource, multi-robot systems can avoid stranded robots, reduce charging bottlenecks, maintain higher availability, and sustain productive operation over long missions.

배터리 인식 작업 할당(Battery-Aware Task Allocation)은 충전을 독립적인 유지보수 활동으로 취급하는 대신 에너지 관리(Energy Management)를 다중 로봇 작업 할당(Multi-Robot Task Allocation)에 직접 통합한다. 모든 작업 할당은 로봇의 위치와 작업 부하뿐만 아니라 향후 미션에 사용할 수 있는 에너지에도 영향을 미친다. 따라서 플릿 할당기(Fleet Allocator)는 로봇이 후보 작업을 안전하게 완료할 수 있는지, 운영 예비 에너지(Operational Reserve)를 유지할 수 있는지, 필요할 때 충전 자원에 도달할 수 있는지, 그리고 계획 구간(Planning Horizon) 동안 생산성을 유지할 수 있는지를 판단해야 한다.

기본적인 상태 변수는 일반적으로 백분율 또는 정규화된 에너지 수준으로 표현되는 충전 상태(State of Charge, SoC)이다. 로봇 \\(r_i\\)에 대해 할당기는 배터리 용량, 최소 예비 임계값, 충전 상태 및 예상 소비량과 함께 \\(SoC_i(t)\\)를 추정하여 관리한다. 측정된 SoC에는 추정 오차가 포함될 수 있으므로 실제 시스템에서는 명목 잔여 에너지(Nominal Remaining Energy)와 향후 작업에 안전하게 사용할 수 있는 에너지(Safely Committable Energy)를 구분하는 것이 바람직하다.

작업의 에너지 비용(Task Energy Cost)은 단순한 이동 거리만으로 결정되지 않는다. 후보 미션에는 작업 위치까지의 이동, 적재물 운송, 조작 또는 센싱, 대기, 통신, 보조 컴퓨팅 및 작업 완료 이후의 이동이 포함될 수 있다. 따라서 유용한 예측 모델은 \\(E_{ij}=E_{travel}+E_{task}+E_{aux}+E_{reserve}\\)와 같이 구성할 수 있다. 지형, 속도, 적재량, 온도, 정지 빈도 및 로봇 유형 역시 동일한 명목 미션에 필요한 에너지를 변화시킬 수 있다.

로봇이 작업 할당 후보가 되기 전에 에너지 실행 가능성(Energy Feasibility)을 확인해야 한다. 작업 \\(j\\)까지 이동하고 작업을 수행한 후 안전한 충전 위치까지 도달하는 데 필요한 예상 에너지가 로봇의 사용 가능한 에너지를 초과한다면 해당 로봇-작업 조합을 제외해야 한다. 이는 배터리가 부족한 로봇에 단순히 높은 비용을 부여하는 것보다 강력한 조건으로, 운영 중 로봇이 에너지 부족으로 고립될 가능성이 있는 할당을 방지하는 명확한 실행 가능성 경계(Hard Feasibility Boundary)를 설정한다.

배터리 정보는 할당 목적 함수(Allocation Objective)에 연성 비용(Soft Cost)으로도 포함할 수 있다. 두 로봇 모두 작업을 수행할 충분한 에너지를 가지고 있더라도 예비 에너지가 위험 수준까지 감소한 로봇을 선택하면 향후 스케줄링 문제가 발생할 수 있다. 따라서 SoC가 정의된 임계값에 가까워질수록 배터리 페널티(Battery Penalty)를 증가시킬 수 있다. 이를 통해 할당기는 에너지 여유가 충분한 로봇을 선호하면서도 운영상 필요한 경우 저에너지 로봇이 짧거나 긴급한 작업을 수행하도록 허용할 수 있다.

충전(Charging)은 외부 프로세스가 아니라 플릿 작업(Fleet Task)의 하나로 표현할 수 있다. 충전 미션(Charging Mission)은 충전기 목적지, 예상 이동 시간, 충전 시간, 목표 SoC 및 자원 가용성(Resource Availability)을 포함한다. 충전을 생산 작업과 동일한 계획 프레임워크 안에서 모델링하면 할당기가 언제 로봇의 추가 작업 수락을 중단할지, 어떤 충전기를 사용할지, 그리고 서비스에 복귀하기 전에 어느 정도까지 에너지를 회복할지를 결정할 수 있다.

단순한 충전 정책은 고정 임계값(Fixed Threshold)에 의존한다. 예를 들어 SoC가 하한 임계값보다 낮아지면 로봇이 충전 모드로 진입하고 상한 임계값까지 충전된 후 다시 운영에 복귀하도록 설정할 수 있다. 이러한 히스테리시스(Hysteresis)는 작업 상태와 충전 상태 사이의 빈번한 전환을 방지한다. 임계값 기반 정책은 구현이 간단하지만 여러 로봇이 유사한 작업 주기(Duty Cycle)를 경험하면 동시에 충전을 요청하는 문제가 발생할 수 있다.

기회 충전(Opportunity Charging)은 보다 유연한 전략을 제공한다. 배터리가 낮아질 때까지 기다리는 대신 자연스럽게 발생하는 유휴 시간, 생산 휴식 시간, 대기열 지연 또는 가용 충전기 근처를 지나갈 때 로봇을 충전할 수 있다. 짧은 충전 세션은 이후 장시간의 운영 중단 가능성을 줄일 수 있다. 그러나 지나친 기회 충전은 충전기를 불필요하게 점유할 수 있으므로 충전의 이점을 예상 작업 수요 및 자원 경합(Resource Contention)과 비교해야 한다.

충전기 할당(Charger Assignment)은 그 자체로 하나의 자원 할당 문제를 형성한다. 플릿에는 서로 다른 위치, 충전 전력, 커넥터 유형 또는 로봇 호환성을 가진 여러 충전기가 존재할 수 있다. 지리적으로 가장 가까운 충전기가 이미 사용 중이거나 긴 대기열을 가지고 있다면 해당 충전기를 선택하는 것이 최적이 아닐 수 있다. 따라서 계획기는 충전소를 선택할 때 이동 시간, 예상 대기 시간, 충전 속도, 호환성 및 로봇의 향후 작업 위치를 고려해야 한다.

많은 로봇이 제한된 충전 인프라를 공유하는 경우 충전소 용량(Charging-Station Capacity)을 명시적으로 고려해야 한다. 여러 로봇이 소수의 충전 포트만 존재하는 충전소에서 동시에 충전하도록 계획되면 대기열이 발생하여 플릿 가용성(Fleet Availability)이 감소할 수 있다. 예약 시스템(Reservation System)을 이용하면 로봇이 도착하기 전에 충전 시간 구간을 할당할 수 있다. 이를 통해 충전을 낮은 SoC에 대한 비계획적인 대응에서 플릿 운영과 통합된 조정형 자원 스케줄링(Coordinated Resource Scheduling) 과정으로 전환할 수 있다.

작업 할당과 충전 계획(Charging Planning)은 밀접하게 결합되어 있다. 멀리 떨어진 작업을 할당하면 추가 에너지가 소비되어 더 빠른 충전이 필요할 수 있으며, 충전기 근처의 작업을 할당하면 작업 완료 후 효율적으로 충전으로 전환할 수 있다. 따라서 작업 할당 비용에는 이후 발생할 에너지 영향(Downstream Energy Consequence)을 포함해야 한다. 국소적으로는 비용이 낮은 작업이라도 완료 직후 충전을 위해 긴 우회 이동이 필요하다면 전체적으로는 바람직하지 않을 수 있다.

배터리 인식 할당은 플릿 전체의 에너지 소비 균형(Energy Consumption Balance)을 조정하는 데도 사용할 수 있다. 효율이 높거나 편리한 위치에 있는 동일한 로봇을 반복적으로 선택하면 다른 로봇보다 배터리 사이클이 훨씬 빈번해질 수 있다. 작업 부하와 배터리 사용량의 균형 항목을 도입하면 미션을 보다 균등하게 분배할 수 있다. 이를 통해 플릿 가용성을 향상시키고 불균등한 배터리 노화(Battery Aging)를 완화할 수 있지만, 활용률 균형이 긴급한 운영 요구사항보다 우선되어서는 안 된다.

배터리 건강 상태(State of Health, SoH)는 문제에 장기적인 차원을 추가한다. 동일한 SoC를 가진 두 로봇이라도 배터리 노화 정도가 다르면 실제 사용 가능한 용량이 서로 다를 수 있다. 신뢰할 수 있는 SoH 정보를 사용할 수 있다면 에너지 예측에서는 명목 배터리 용량이 아니라 유효 배터리 용량(Effective Battery Capacity)을 사용하는 것이 바람직하다. 노화 인식 할당(Aging-Aware Allocation)은 이미 열화된 배터리에 고출력 또는 심방전(Deep Discharge) 사이클이 반복적으로 가해지는 것도 줄일 수 있다.

동적 작업 도착(Dynamic Task Arrival)은 에너지 계획을 지속적으로 수정하도록 요구한다. 충분한 예비 에너지가 있다면 충전 예정이었던 로봇을 긴급 작업에 일시적으로 재할당할 수 있으며, 예상하지 못한 작업 폭증(Task Burst)이 발생하면 중요도가 낮은 충전을 연기해야 할 수도 있다. 반대로 예상보다 작업 수행 시간이 길어지거나 에너지 소비가 증가하면 더 빠른 충전 결정이 필요할 수 있다. 따라서 온라인 할당(Online Allocation)은 의미 있는 플릿 이벤트가 발생할 때마다 예상 에너지 궤적(Predicted Energy Trajectory)을 갱신한다.

계획 구간을 고려한 예측(Prediction over a Planning Horizon)은 단순한 임계값 방식보다 향상된 충전 결정을 가능하게 한다. 로봇의 SoC가 45%라고 하더라도 곧 여러 개의 에너지 집약적 작업이 예정되어 있다면 20%까지 감소하기를 기다리는 것보다 현재 충전하는 것이 유리할 수 있다. 반대로 SoC가 상대적으로 낮더라도 향후 수요가 적고 가까운 곳에 가용 충전기가 있다면 작업을 계속 수행할 수 있다. 예측형 계획(Predictive Planning)은 현재 배터리 상태와 예상 미래 작업 부하를 연결한다.

롤링 호라이즌 최적화(Rolling-Horizon Optimization)는 작업 수요와 배터리 상태가 모두 지속적으로 변화하기 때문에 이러한 문제에 적합하다. 각 계획 주기에서 시스템은 가용 로봇, 대기 작업, 충전기 상태, 예상 에너지 소비량 및 제한된 미래 계획 구간을 함께 고려한다. 가까운 시점의 작업 및 충전 결정은 확정하고 이후의 결정은 유연하게 유지한다. 로봇이 이동하고 새로운 작업이 도착하며 충전 조건이 변화하면 최적화를 반복한다.

에너지 불확실성(Energy Uncertainty)은 보수적으로 처리해야 한다. 혼잡, 적재량 변화, 지형, 온도, 우회 이동 또는 배터리 모델 오차로 인해 예상 소비량과 실제 소비량이 달라질 수 있다. 안전 예비량(Safety Reserve)을 설정하면 계획기가 이론적으로 사용할 수 있는 모든 에너지를 소진하는 것을 방지할 수 있다. 필요한 예비량은 운영 환경에 따라 달라질 수 있으며 충전기가 멀리 떨어져 있거나 미션 중단 위험이 큰 환경에서는 더 큰 안전 여유를 적용하는 것이 적절하다.

충전 인프라의 고장(Failure)도 고려해야 한다. 충전기가 사용 불가능해지거나 충전소와의 통신이 실패하거나 도킹(Docking)이 정상적으로 이루어지지 않을 수 있다. 가능한 경우 로봇은 대체 충전기(Alternative Charger)까지 이동할 수 있는 충분한 예비 에너지를 유지해야 한다. 따라서 충전기의 상태와 예약 정보도 플릿 상태의 일부로 관리해야 하며 충전 실패가 발생하면 복구 전략 없이 에너지를 계속 소비하도록 하는 대신 재계획(Replanning)을 시작해야 한다.

이종 플릿(Heterogeneous Fleet)에서는 로봇 클래스마다 서로 다른 에너지 모델(Energy Model)이 필요하다. 운송 AMR, 모바일 매니퓰레이터(Mobile Manipulator), 견인 로봇(Towing Robot), 검사 플랫폼(Inspection Platform)은 배터리 용량과 에너지 소비 특성이 크게 다를 수 있다. 한 플랫폼에서는 적재 및 조작이 에너지 소비의 대부분을 차지하고 다른 플랫폼에서는 이동이 지배적일 수 있다. 따라서 배터리 인식 할당에서는 전체 플릿에 동일한 백분율 기반 정책을 적용하기보다 로봇별 에너지 모델(Robot-Specific Energy Model)을 사용해야 한다.

시뮬레이션(Simulation)은 배터리 및 충전 정책을 조정하는 효과적인 환경을 제공한다. 작업 강도, 충전기 수, 충전 전력, 배터리 용량, 예비 임계값 및 기회 충전 규칙을 체계적으로 변화시키면서 평가할 수 있다. 작업 폭증, 충전기 고장, 긴 충전 대기열, 열화된 배터리 또는 고에너지 미션을 포함한 스트레스 시나리오(Stress Scenario)를 통해 과도한 충전 혼잡이나 미션 거부 없이 플릿 운영을 유지할 수 있는지를 검증할 수 있다.

평가에서는 에너지 성능과 함께 플릿 생산성(Fleet Productivity)을 고려해야 한다. 주요 지표에는 작업 처리량(Task Throughput), 미션 완료율, 평균 및 최소 SoC, 충전기 활용률, 충전 대기 시간, 작업당 에너지 소비량, 충전에 사용된 시간, 에너지 부족으로 실행 불가능한 할당 수, 긴급 충전 이벤트 및 플릿 가용성이 포함된다. 장기적인 수명주기 성능(Lifecycle Performance)이 중요한 경우에는 배터리 열화 지표(Battery Degradation Indicator)도 함께 모니터링할 수 있다.

따라서 배터리 인식 작업 할당 및 충전 계획(Battery-Aware Task Allocation and Charging Planning)은 하나의 통합된 에너지 관리 문제(Unified Energy-Management Problem)를 형성한다. 할당기는 작업 수요, 로봇 능력, 예상 에너지 소비량, 충전 상태(SoC)와 건강 상태(SoH), 충전 인프라, 안전 예비량 및 미래 작업 부하를 하나의 의사결정 루프(Decision Loop) 안에서 연결해야 한다. 에너지를 지속적으로 관리되는 플릿 자원(Fleet Resource)으로 취급하면 다중 로봇 시스템은 에너지 부족으로 고립되는 로봇을 방지하고 충전 병목을 줄이며 높은 가용성을 유지하면서 장시간의 미션에서도 지속적인 생산성을 확보할 수 있다.

##  

## 02.08 RL Based Task Allocation Policy [w/Code]

![](images/image8.png){width="7.268055555555556in" height="7.268055555555556in"}

Reinforcement Learning (RL)-based task allocation treats robot-task assignment as a sequential decision problem in which an allocation policy learns how to select actions from repeated interaction with a fleet environment. Unlike optimization methods that explicitly solve a mathematical model at every decision point, RL attempts to learn a policy that maps observed fleet states directly to allocation decisions. This approach is particularly attractive when task arrivals, congestion, energy use, and future consequences make analytical cost models difficult to construct.

The allocation problem can be formulated as a Markov Decision Process (MDP) consisting of states, actions, transition dynamics, rewards, and a discount factor. At decision time \\(t\\), the fleet state \\(s_t\\) describes relevant information about robots, tasks, infrastructure, and the operating environment. The policy \\(\\pi(a_t\|s_t)\\) selects an allocation action \\(a_t\\), after which the environment transitions to a new state \\(s_{t+1}\\) and returns reward \\(r_t\\).

A useful state representation may include robot position, velocity, current task, availability, battery State of Charge (SoC), payload, capability, predicted completion time, and health status. Task information can include location, priority, waiting time, deadline, required skill, expected service duration, and energy demand. Charger availability, traffic conditions, queue lengths, blocked regions, and shared-resource states can also be included when they influence future allocation quality.

The action space defines what allocation decisions the learning agent can make. A simple action may select one robot for one waiting task, while a larger action can represent several assignments simultaneously. Other actions may defer a task, send a robot to charge, preserve a robot for future demand, or reassign previously reserved work. Action-space design is critical because the number of possible robot-task combinations grows rapidly as fleet size increases.

Invalid actions should normally be removed before policy selection rather than learned entirely through negative rewards. A robot without sufficient payload, sensing capability, access permission, battery reserve, or required tool should not be allowed to receive an incompatible task. Action masking can set such choices as unavailable while the RL policy chooses among feasible alternatives. This combines explicit engineering constraints with learned decision-making and improves both training efficiency and operational safety.

Reward design determines what behavior the policy learns. A task-allocation reward may positively value completed tasks and high throughput while penalizing travel time, energy consumption, deadline violations, queue waiting, charger congestion, or unassigned high-priority work. A simplified reward can be expressed as \\(r_t=w_1R_{complete}-w_2C_{travel}-w_3C_{delay}-w_4C_{energy}\\), with additional terms introduced for operational objectives.

Reward shaping must be performed carefully because poorly chosen rewards can produce unintended strategies. If only task completion is rewarded, the agent may ignore workload balance or excessive travel. If energy consumption is penalized too strongly, it may avoid useful missions. Sparse rewards can also slow learning when meaningful feedback occurs only after long missions. Intermediate rewards can provide learning signals while preserving the desired long-term objective.

The key advantage of RL is its ability to optimize long-term return rather than only immediate assignment cost. A robot that is currently closest to a task may not be the best choice if using it leaves an important region uncovered or causes an imminent charging interruption. Through repeated training, the policy can learn that some apparently suboptimal short-term assignments create better future fleet states and improve cumulative performance over time.

Value-based methods estimate the expected future return associated with states or state-action pairs. Deep Q-Network (DQN) approaches can be applied when the action space is discrete and reasonably bounded. However, directly representing every robot-task combination as an independent action becomes difficult as fleet size increases. Factorized actions, candidate filtering, hierarchical decisions, or alternative policy architectures are therefore often required for practical multi-robot systems.

Policy-gradient methods learn a parameterized policy directly and can support stochastic decision-making. Actor-Critic methods combine a policy-producing actor with a critic that estimates expected return and guides policy updates. Algorithms such as Proximal Policy Optimization (PPO) are commonly attractive for complex simulated environments because they provide a relatively stable training process and can accommodate richer state and action representations than simple tabular approaches.

Multi-Agent Reinforcement Learning (MARL) provides another formulation in which individual robots act as learning agents. Each robot may observe local state and select tasks, bids, movements, or coordination actions. This architecture can improve decentralization and scalability, but learning becomes more difficult because each agent experiences an environment that changes as the policies of other agents evolve. Coordination and credit assignment therefore become central challenges.

Centralized Training with Decentralized Execution (CTDE) addresses part of this difficulty. During training, a centralized critic can access broader fleet information to evaluate joint behavior, while individual robot policies learn to act using only observations available during deployment. This approach can exploit global information during learning without requiring every robot to access the entire fleet state at execution time.

Graph Neural Networks (GNNs) are well suited to RL-based task allocation because fleets naturally form relational structures. Robots and tasks can be represented as graph nodes, while candidate assignments, spatial relationships, communication links, or resource conflicts form edges. A graph-based policy can aggregate information across these relationships and produce allocation scores while supporting variable numbers of robots and tasks more naturally than fixed-size vector inputs.

Attention mechanisms provide another way to handle changing fleet dimensions. Instead of concatenating all robot and task states into one fixed vector, an attention-based policy can evaluate relevant relationships among robots, tasks, chargers, and infrastructure. This allows the policy to focus on the most important candidates at each decision point and can improve generalization across different task distributions or fleet sizes.

Training generally requires simulation because a task-allocation policy may need millions of interactions before becoming reliable. A simulator can generate task arrivals, robot motion, charging behavior, failures, congestion, and resource conflicts much faster and more safely than a physical fleet. Domain randomization can vary task rates, travel times, battery consumption, robot failures, and environmental conditions so that the learned policy does not overfit to one nominal scenario.

Curriculum learning can improve training efficiency by gradually increasing problem difficulty. Initial training may use a small number of robots, simple task distributions, and no failures. Later stages can introduce larger fleets, heterogeneous capabilities, charging constraints, dynamic arrivals, congestion, and communication delays. The policy therefore learns basic assignment behavior before confronting the full complexity of realistic fleet operations.

Offline Reinforcement Learning offers an alternative when historical fleet data are available but unrestricted online exploration is unacceptable. Logged task assignments, robot states, execution outcomes, and energy records can form an offline dataset from which a policy is trained. The major challenge is distribution shift: the learned policy may propose actions that are poorly represented in the historical data, making reliable value estimation difficult.

Imitation Learning can provide an effective initialization for RL. Demonstrations generated by human dispatchers, heuristic policies, the Hungarian Algorithm, or Integer Linear Programming can teach the policy reasonable initial behavior. Reinforcement learning can then improve beyond the demonstrations through simulated interaction. This hybrid approach reduces the amount of unsafe or inefficient exploration required during early training.

Safety constraints should remain outside the learned reward whenever violations are unacceptable. Collision avoidance, prohibited-zone access, payload limits, minimum battery reserve, emergency-stop conditions, and mandatory capability requirements should be enforced through deterministic safety layers, action masks, or constrained optimization. RL should optimize among safe alternatives rather than learn through experience that dangerous actions are undesirable.

A practical deployment architecture can therefore use RL as a policy recommendation layer rather than an unrestricted fleet controller. The policy receives validated fleet state, ranks feasible robot-task actions, and proposes an allocation. A rule-based or optimization-based supervisory layer verifies hard constraints before dispatch. If the learned policy produces an invalid, uncertain, or unsupported decision, the system can fall back to a conventional allocator.

Online adaptation may improve performance when operational conditions differ from training, but uncontrolled learning on a production fleet creates risk. A safer strategy collects execution experience, evaluates policy updates offline or in a digital twin, and deploys only validated versions. Policy versioning, rollback capability, performance monitoring, and comparison against a stable baseline are important elements of an operational RL lifecycle.

Generalization is one of the most important evaluation criteria. A policy that performs well only with the exact number of robots and task distribution used during training has limited fleet value. Testing should vary fleet size, robot capability combinations, arrival rates, charger availability, map topology, congestion, and failure patterns. Graph-based representations, attention, randomization, and diverse training scenarios can improve robustness to these changes.

RL policies should be compared with strong non-learning baselines rather than only simple random or nearest-robot strategies. Greedy allocation, auction-based methods, Hungarian matching, and ILP or MILP solutions provide useful references. Evaluation should include throughput, task waiting time, completion time, deadline violations, travel distance, energy consumption, charger congestion, utilization balance, computation latency, and performance under unexpected disturbances.

RL-based task allocation is therefore most valuable when allocation decisions have long-term consequences that are difficult to capture with manually designed instantaneous costs. It can learn predictive and anticipatory behavior from repeated interaction, but its flexibility introduces challenges in reward design, scalability, generalization, explainability, and safety assurance. Combining learned policies with explicit feasibility constraints, simulation, strong baselines, and supervisory control provides a practical path toward intelligent task allocation for dynamic multi-robot fleets.

강화학습 기반 작업 할당(Reinforcement Learning-Based Task Allocation)은 로봇-작업 할당(Robot-Task Assignment)을 순차적 의사결정 문제(Sequential Decision Problem)로 다루며, 할당 정책(Allocation Policy)이 플릿 환경(Fleet Environment)과의 반복적인 상호작용을 통해 행동을 선택하는 방법을 학습하도록 한다. 각 의사결정 시점마다 명시적인 수학적 모델을 풀어야 하는 최적화 방법과 달리 강화학습(Reinforcement Learning, RL)은 관측된 플릿 상태를 직접 작업 할당 결정으로 매핑하는 정책을 학습한다. 이러한 접근법은 작업 도착, 혼잡, 에너지 소비 및 미래 결과 때문에 분석적인 비용 모델을 구성하기 어려운 환경에서 특히 유용하다.

작업 할당 문제는 상태(State), 행동(Action), 상태 전이 동역학(Transition Dynamics), 보상(Reward), 할인율(Discount Factor)로 구성되는 마르코프 의사결정 과정(Markov Decision Process, MDP)으로 정식화할 수 있다. 의사결정 시점 \\(t\\)에서 플릿 상태 \\(s_t\\)는 로봇, 작업, 인프라 및 운영 환경에 관한 관련 정보를 나타낸다. 정책 \\(\\pi(a_t\|s_t)\\)는 할당 행동 \\(a_t\\)를 선택하고, 이후 환경은 새로운 상태 \\(s_{t+1}\\)로 전이하면서 보상 \\(r_t\\)를 반환한다.

유용한 상태 표현(State Representation)에는 로봇의 위치, 속도, 현재 작업, 가용성, 배터리 충전 상태(State of Charge, SoC), 적재물, 능력, 예상 완료 시간 및 건전성 상태(Health Status)가 포함될 수 있다. 작업 정보에는 위치, 우선순위, 대기 시간, 마감시간, 요구 스킬, 예상 서비스 시간 및 에너지 요구량이 포함될 수 있다. 충전기 가용성, 교통 상황, 대기열 길이, 차단 구역 및 공유 자원 상태도 향후 할당 품질에 영향을 미친다면 상태 정보에 포함할 수 있다.

행동 공간(Action Space)은 학습 에이전트(Learning Agent)가 수행할 수 있는 할당 결정을 정의한다. 단순한 행동은 하나의 대기 작업에 하나의 로봇을 선택하는 것이며, 보다 큰 행동은 여러 개의 할당을 동시에 나타낼 수 있다. 작업을 연기하거나 로봇을 충전하도록 보내고, 미래 수요에 대비해 로봇을 유지하거나, 이전에 예약된 작업을 재할당하는 것도 행동에 포함할 수 있다. 플릿 규모가 증가하면 가능한 로봇-작업 조합의 수가 빠르게 증가하므로 행동 공간 설계는 매우 중요하다.

유효하지 않은 행동(Invalid Action)은 전적으로 음의 보상(Negative Reward)을 통해 학습시키기보다 정책이 행동을 선택하기 전에 제거하는 것이 일반적으로 바람직하다. 충분한 적재 능력, 센싱 능력, 접근 권한, 배터리 예비량 또는 필요한 도구를 갖추지 않은 로봇에는 호환되지 않는 작업을 할당해서는 안 된다. 행동 마스킹(Action Masking)을 사용하면 이러한 선택을 불가능한 상태로 설정하고 RL 정책이 실행 가능한 대안 가운데 하나를 선택하도록 할 수 있다. 이는 명시적인 엔지니어링 제약조건과 학습 기반 의사결정을 결합하여 학습 효율성과 운영 안전성을 모두 향상시킨다.

보상 설계(Reward Design)는 정책이 어떤 행동을 학습하는지를 결정한다. 작업 할당 보상은 완료된 작업과 높은 처리량(Throughput)에 양의 가치를 부여하면서 이동 시간, 에너지 소비, 마감시간 위반, 대기열 대기, 충전기 혼잡 또는 할당되지 않은 고우선순위 작업에 페널티를 부여할 수 있다. 단순화된 보상은 \\(r_t=w_1R_{complete}-w_2C_{travel}-w_3C_{delay}-w_4C_{energy}\\)로 표현할 수 있으며, 운영 목적에 따라 추가적인 항을 도입할 수 있다.

보상 형성(Reward Shaping)은 잘못 설계된 보상이 의도하지 않은 전략을 만들어낼 수 있으므로 신중하게 수행해야 한다. 작업 완료에만 보상을 제공하면 에이전트가 작업 부하 균형이나 과도한 이동을 무시할 수 있다. 에너지 소비에 지나치게 큰 페널티를 부여하면 유용한 미션 수행 자체를 회피할 수 있다. 의미 있는 피드백이 긴 미션이 완료된 후에만 발생하는 희소 보상(Sparse Reward) 역시 학습 속도를 저하시킬 수 있다. 중간 보상(Intermediate Reward)을 활용하면 원하는 장기 목표를 유지하면서 효과적인 학습 신호를 제공할 수 있다.

RL의 핵심적인 장점은 즉각적인 할당 비용만이 아니라 장기 누적 보상(Long-Term Return)을 최적화할 수 있다는 점이다. 현재 특정 작업에 가장 가까운 로봇이라도 해당 로봇을 사용함으로써 중요한 구역이 비게 되거나 곧 충전 중단이 발생한다면 최적의 선택이 아닐 수 있다. 반복적인 학습을 통해 정책은 단기적으로는 최적이 아닌 것처럼 보이는 일부 할당이 더 좋은 미래 플릿 상태를 만들고 장기적인 누적 성능을 향상시킨다는 것을 학습할 수 있다.

가치 기반 방법(Value-Based Method)은 상태 또는 상태-행동 쌍(State-Action Pair)에 대응하는 예상 미래 누적 보상을 추정한다. 행동 공간이 이산적이고 적절한 크기로 제한되는 경우 심층 Q-네트워크(Deep Q-Network, DQN)를 적용할 수 있다. 그러나 모든 로봇-작업 조합을 각각 독립적인 행동으로 직접 표현하면 플릿 규모가 증가할수록 처리하기 어려워진다. 따라서 실제 다중 로봇 시스템에서는 분해된 행동(Factorized Action), 후보 필터링(Candidate Filtering), 계층적 의사결정(Hierarchical Decision) 또는 대안적인 정책 아키텍처가 필요하다.

정책 경사법(Policy-Gradient Method)은 매개변수화된 정책(Parameterized Policy)을 직접 학습하며 확률적 의사결정(Stochastic Decision-Making)을 지원할 수 있다. 액터-크리틱(Actor-Critic) 방법은 정책을 생성하는 액터(Actor)와 예상 누적 보상을 추정하여 정책 갱신을 안내하는 크리틱(Critic)을 결합한다. 근위 정책 최적화(Proximal Policy Optimization, PPO)와 같은 알고리즘은 비교적 안정적인 학습 과정을 제공하고 단순한 테이블 기반 접근법보다 풍부한 상태 및 행동 표현을 처리할 수 있어 복잡한 시뮬레이션 환경에 적용하기 적합하다.

다중 에이전트 강화학습(Multi-Agent Reinforcement Learning, MARL)은 개별 로봇을 각각 학습 에이전트로 취급하는 또 다른 정식화를 제공한다. 각 로봇은 로컬 상태를 관측하고 작업, 입찰, 이동 또는 협력 행동을 선택할 수 있다. 이러한 아키텍처는 분산화(Decentralization)와 확장성(Scalability)을 향상시킬 수 있지만 다른 에이전트의 정책이 변화함에 따라 각 에이전트가 경험하는 환경도 변화하기 때문에 학습이 더욱 어려워진다. 따라서 협력(Coordination)과 기여도 할당(Credit Assignment)이 핵심적인 과제가 된다.

중앙집중형 학습과 분산형 실행(Centralized Training with Decentralized Execution, CTDE)은 이러한 어려움의 일부를 해결한다. 학습 과정에서는 중앙집중형 크리틱(Centralized Critic)이 보다 광범위한 플릿 정보에 접근하여 공동 행동을 평가할 수 있으며, 개별 로봇 정책은 실제 배포 환경에서 이용 가능한 관측 정보만을 사용하여 행동하도록 학습할 수 있다. 이를 통해 실제 실행 시 모든 로봇이 전체 플릿 상태에 접근하지 않아도 학습 단계에서는 전역 정보를 활용할 수 있다.

그래프 신경망(Graph Neural Network, GNN)은 플릿이 본질적으로 관계 구조(Relational Structure)를 형성하기 때문에 RL 기반 작업 할당에 적합하다. 로봇과 작업을 그래프 노드(Graph Node)로 표현하고 후보 할당, 공간적 관계, 통신 링크 또는 자원 충돌을 엣지(Edge)로 표현할 수 있다. 그래프 기반 정책(Graph-Based Policy)은 이러한 관계를 따라 정보를 집계하고 할당 점수를 생성할 수 있으며, 고정 크기의 벡터 입력보다 변화하는 로봇 및 작업 수를 자연스럽게 처리할 수 있다.

어텐션 메커니즘(Attention Mechanism)은 변화하는 플릿 규모를 처리하기 위한 또 다른 방법이다. 모든 로봇과 작업 상태를 하나의 고정된 벡터에 연결하는 대신 어텐션 기반 정책(Attention-Based Policy)은 로봇, 작업, 충전기 및 인프라 사이의 중요한 관계를 평가할 수 있다. 이를 통해 정책은 각 의사결정 시점에서 가장 중요한 후보에 집중할 수 있으며 서로 다른 작업 분포 또는 플릿 규모에 대한 일반화(Generalization)를 향상시킬 수 있다.

작업 할당 정책이 신뢰할 수 있는 수준에 도달하기까지 수백만 번의 상호작용이 필요할 수 있기 때문에 일반적으로 시뮬레이션(Simulation)을 통한 학습이 필요하다. 시뮬레이터는 실제 플릿보다 훨씬 빠르고 안전하게 작업 도착, 로봇 이동, 충전 동작, 고장, 혼잡 및 자원 충돌을 생성할 수 있다. 도메인 랜덤화(Domain Randomization)를 사용하면 작업 발생률, 이동 시간, 배터리 소비, 로봇 고장 및 환경 조건을 다양하게 변화시켜 학습된 정책이 하나의 명목 시나리오에 과적합(Overfitting)되는 것을 방지할 수 있다.

커리큘럼 학습(Curriculum Learning)은 문제의 난이도를 점진적으로 증가시켜 학습 효율성을 높일 수 있다. 초기 학습에서는 적은 수의 로봇, 단순한 작업 분포 및 고장이 없는 환경을 사용할 수 있다. 이후 단계에서는 더 큰 플릿, 이종 로봇 능력, 충전 제약조건, 동적 작업 도착, 혼잡 및 통신 지연을 도입할 수 있다. 이를 통해 정책은 현실적인 플릿 운영의 전체 복잡성을 처리하기 전에 기본적인 작업 할당 동작을 먼저 학습할 수 있다.

오프라인 강화학습(Offline Reinforcement Learning)은 과거 플릿 데이터를 사용할 수 있지만 제한 없는 온라인 탐색이 허용되지 않는 경우 대안을 제공한다. 기록된 작업 할당, 로봇 상태, 실행 결과 및 에너지 기록을 오프라인 데이터셋(Offline Dataset)으로 구성하여 정책을 학습할 수 있다. 주요 과제는 분포 이동(Distribution Shift)으로, 학습된 정책이 과거 데이터에 충분히 포함되지 않은 행동을 제안할 경우 신뢰할 수 있는 가치 추정(Value Estimation)이 어려워질 수 있다.

모방학습(Imitation Learning)은 RL을 위한 효과적인 초기화 방법을 제공할 수 있다. 사람 디스패처(Human Dispatcher), 휴리스틱 정책(Heuristic Policy), 헝가리안 알고리즘(Hungarian Algorithm) 또는 정수 선형 계획법(Integer Linear Programming, ILP)이 생성한 시범 데이터(Demonstration)를 이용하여 정책에 합리적인 초기 행동을 학습시킬 수 있다. 이후 강화학습을 통해 시뮬레이션 상호작용으로 시범 수준을 넘어 성능을 향상시킬 수 있다. 이러한 하이브리드 접근법(Hybrid Approach)은 초기 학습 단계에서 필요한 비효율적이거나 위험한 탐색을 줄일 수 있다.

허용할 수 없는 위반 사항에 대해서는 안전 제약조건(Safety Constraint)을 학습된 보상 체계 외부에 유지해야 한다. 충돌 회피, 금지 구역 접근, 적재 한계, 최소 배터리 예비량, 비상 정지 조건 및 필수 능력 요구사항은 결정론적 안전 계층(Deterministic Safety Layer), 행동 마스크 또는 제약 최적화를 통해 강제해야 한다. RL은 위험한 행동이 바람직하지 않다는 사실을 경험을 통해 학습하도록 하는 것이 아니라 안전한 대안 가운데 최적의 행동을 선택하도록 사용해야 한다.

따라서 실제 배포 아키텍처(Deployment Architecture)에서는 RL을 제한 없는 플릿 제어기가 아니라 정책 추천 계층(Policy Recommendation Layer)으로 사용할 수 있다. 정책은 검증된 플릿 상태를 입력받아 실행 가능한 로봇-작업 행동의 순위를 계산하고 할당을 제안한다. 이후 규칙 기반 또는 최적화 기반 감독 계층(Supervisory Layer)이 디스패치 전에 하드 제약조건(Hard Constraint)을 검증한다. 학습된 정책이 유효하지 않거나 불확실하거나 지원되지 않는 결정을 생성하면 시스템은 기존의 전통적인 할당기(Conventional Allocator)로 폴백(Fallback)할 수 있다.

온라인 적응(Online Adaptation)은 실제 운영 조건이 학습 환경과 다를 때 성능을 향상시킬 수 있지만 생산 플릿에서 통제되지 않은 학습을 수행하는 것은 위험을 발생시킨다. 보다 안전한 전략은 실행 경험을 수집하고 정책 업데이트를 오프라인 또는 디지털 트윈(Digital Twin)에서 평가한 다음 검증된 버전만 배포하는 것이다. 정책 버전 관리(Policy Versioning), 롤백(Rollback) 기능, 성능 모니터링 및 안정적인 기준 정책(Baseline)과의 비교는 운영 RL 수명주기(Operational RL Lifecycle)의 중요한 요소이다.

일반화(Generalization)는 가장 중요한 평가 기준 가운데 하나이다. 학습에 사용된 정확한 로봇 수와 작업 분포에서만 좋은 성능을 보이는 정책은 실제 플릿에서 활용 가치가 제한적이다. 테스트에서는 플릿 규모, 로봇 능력 조합, 작업 도착률, 충전기 가용성, 지도 토폴로지(Map Topology), 혼잡 및 고장 패턴을 다양하게 변화시켜야 한다. 그래프 기반 표현, 어텐션, 랜덤화 및 다양한 학습 시나리오는 이러한 변화에 대한 강건성(Robustness)을 향상시킬 수 있다.

RL 정책은 단순한 무작위 또는 최근접 로봇 전략뿐만 아니라 강력한 비학습 기준 방법(Non-Learning Baseline)과 비교해야 한다. 탐욕적 할당(Greedy Allocation), 경매 기반 방법(Auction-Based Method), 헝가리안 매칭(Hungarian Matching), ILP 또는 혼합 정수 선형 계획법(Mixed-Integer Linear Programming, MILP)의 해가 유용한 비교 기준을 제공한다. 평가는 처리량, 작업 대기 시간, 완료 시간, 마감시간 위반, 이동 거리, 에너지 소비량, 충전기 혼잡, 활용률 균형, 계산 지연시간 및 예상하지 못한 장애 상황에서의 성능을 포함해야 한다.

따라서 RL 기반 작업 할당(RL-Based Task Allocation)은 수작업으로 설계된 순간적인 비용 함수만으로 표현하기 어려운 장기적인 결과가 작업 할당 결정에 존재할 때 가장 큰 가치를 제공한다. 반복적인 상호작용을 통해 예측적이고 선제적인 행동(Predictive and Anticipatory Behavior)을 학습할 수 있지만, 이러한 유연성은 보상 설계, 확장성, 일반화, 설명 가능성(Explainability) 및 안전성 보증(Safety Assurance)이라는 과제를 함께 발생시킨다. 학습 정책을 명시적인 실행 가능성 제약조건, 시뮬레이션, 강력한 기준 알고리즘 및 감독 제어(Supervisory Control)와 결합하는 것은 동적 다중 로봇 플릿을 위한 지능형 작업 할당을 구현하는 실용적인 접근법을 제공한다.

##  

## 02.09 Task Allocation Benchmark and Performance Metrics

![](images/image9.png){width="7.268055555555556in" height="7.268055555555556in"}

Task allocation benchmarks provide a systematic basis for evaluating how effectively Multi-Robot Task Allocation algorithms convert fleet resources into completed missions. Because different allocation methods optimize different objectives, comparing algorithms only by whether tasks are successfully assigned is insufficient. A useful benchmark must evaluate operational efficiency, solution quality, computational cost, robustness, scalability, fairness, energy behavior, and responsiveness under controlled and repeatable scenarios.

A benchmark begins by defining a reproducible problem instance containing robots, tasks, environment conditions, and operational constraints. Robot information may include initial position, mobility class, payload, capabilities, battery state, and availability. Tasks may specify location, release time, priority, deadline, required skills, service duration, and energy demand. Using identical instances ensures that competing algorithms are evaluated against the same workload and fleet conditions.

Static benchmarks evaluate a fixed set of tasks known before allocation begins. They are useful for comparing assignment quality because every algorithm receives identical information and can be measured against an optimal or near-optimal reference. Dynamic benchmarks introduce tasks during execution and better represent warehouses, factories, hospitals, inspection systems, and service fleets where new requests arrive continuously and future demand is not completely known.

Benchmark scenarios should vary fleet size and task density to expose scalability limits. A small scenario may contain only a few robots and tasks, while progressively larger cases can include tens, hundreds, or potentially thousands of allocation candidates. Increasing the robot-task ratio, task arrival rate, or planning horizon reveals how computation time and solution quality change as the allocation problem becomes more complex.

Heterogeneous fleet benchmarks should explicitly represent capability differences. Tasks can require payload capacity, manipulation, sensing, towing, environmental protection, or specialized tools, while only subsets of robots satisfy those requirements. Such scenarios evaluate whether an allocator correctly handles eligibility, capability scarcity, and specialized-resource utilization instead of assuming that every robot can perform every task.

Total assignment cost is one of the most fundamental performance measures. If \\(c_{ij}\\) represents the cost of assigning robot \\(i\\) to task \\(j\\), the resulting solution can be evaluated using \\(J=\\sum_i\\sum_j c_{ij}x_{ij}\\). Depending on the benchmark, cost may represent travel distance, execution time, energy, economic cost, or a weighted combination. The exact definition must remain identical across compared algorithms.

Solution optimality can be measured when an optimal reference solution is available. An optimality gap compares the cost produced by an algorithm with the known optimum, commonly expressed as a relative percentage difference. This is particularly useful when comparing greedy, auction-based, learning-based, or time-limited optimization methods against Hungarian, ILP, or MILP solutions on problem sizes where an exact or high-quality reference can be obtained.

Task completion time measures how long individual missions require from assignment or release until completion. Makespan measures the time required to complete the entire set of tasks within a benchmark episode. An allocator that minimizes travel distance does not necessarily minimize makespan because poor workload distribution can leave some robots overloaded while others become idle. Both local completion time and fleet-wide finishing time should therefore be considered.

Throughput measures the number of successfully completed tasks per unit time and is especially important for continuously operating fleets. Warehouse transport, production logistics, and service robots are often evaluated primarily by sustained throughput rather than by the cost of one isolated assignment. Throughput should be measured after sufficient simulation time so that initialization effects do not dominate the result.

Task response time and queue waiting time are essential for dynamic allocation. Response time measures how quickly the system reacts after a task becomes available, while queue waiting time measures how long the task remains unserved before execution begins. Average values are useful, but percentile statistics such as the 95th or 99th percentile reveal rare but operationally serious delays that averages can hide.

Deadline performance should distinguish successful completion from timely completion. Deadline violation rate measures the fraction of tasks completed after their required deadline, while tardiness measures the amount of delay beyond the deadline. Priority-weighted tardiness can assign greater penalties to emergency or production-critical tasks. These metrics reveal whether an allocator preserves service quality under high workload.

Robot utilization describes the fraction of operational time spent performing productive work. Utilization should be interpreted together with workload balance because maximizing average utilization can still overload a subset of robots. Metrics such as variance in task count, working time, traveled distance, or energy use across robots indicate whether work is distributed fairly and whether particular platforms become persistent bottlenecks.

Travel efficiency is commonly measured using total distance, empty travel distance, and travel time. Empty travel is particularly important in logistics because movement without carrying a payload consumes fleet capacity without directly completing productive work. Comparing productive and nonproductive motion helps determine whether the allocator creates geographically coherent task sequences or repeatedly sends robots across the operating area.

Energy metrics are increasingly important for battery-powered fleets. Evaluation can include total energy consumption, energy per completed task, minimum SoC, charging frequency, charging time, and the number of energy-infeasible assignments. For battery-aware allocators, charger utilization and charging queue time should also be measured because an apparently energy-efficient policy may create infrastructure congestion.

Computational latency measures the time required to produce an allocation decision. Average latency alone is insufficient for real-time systems because occasional extreme delays can interrupt fleet operation. Median, maximum, and high-percentile latency should therefore be recorded. Algorithms should also be evaluated using equivalent hardware and implementation conditions whenever computational performance is compared.

Scalability analysis examines how computational time, memory use, communication traffic, and solution quality change as the number of robots and tasks increases. An algorithm that produces excellent assignments for ten robots may become impractical for hundreds. Scaling curves provide more information than a single benchmark size and help identify the fleet dimensions at which decomposition, hierarchy, approximation, or distributed allocation becomes necessary.

Communication overhead is especially relevant for auction-based and distributed methods. Useful measures include the number of messages, transmitted data volume, bidding rounds, synchronization events, and communication latency per allocation cycle. A distributed algorithm should not be considered scalable solely because computation is decentralized if communication requirements increase excessively with fleet size.

Robustness benchmarks introduce disturbances that were not present in nominal scenarios. Robot failures, communication loss, blocked routes, charger failures, task cancellations, execution delays, and sudden priority changes can be injected during operation. Recovery time, task loss, reassignment count, throughput degradation, and service continuity then indicate how effectively the allocator responds when assumptions are violated.

Reassignment frequency provides an important measure of allocation stability. Dynamic optimization may continuously discover slightly better solutions, but repeatedly changing robot missions can create routing overhead and operational confusion. Benchmarks should record how often assignments are changed, how much improvement those changes produce, and whether robots experience assignment thrashing before useful work is completed.

Fairness and starvation metrics are relevant when tasks or robots compete for limited resources. Maximum task waiting time, starvation rate, priority compliance, and distribution of workload across robots can reveal undesirable behavior hidden by aggregate throughput. A policy that achieves high productivity by indefinitely postponing low-priority tasks may be unacceptable even when its average performance appears strong.

Learning-based allocators require additional evaluation. Training reward alone should never be treated as sufficient evidence of performance. Policies should be tested on unseen task streams, maps, fleet sizes, capability combinations, congestion levels, and failure patterns. Generalization gap, inference latency, constraint-violation rate, and performance relative to non-learning baselines provide more meaningful measures of deployment readiness.

Statistical methodology is necessary because dynamic fleet simulations contain randomness. Each configuration should be evaluated over multiple independent runs using controlled random seeds. Mean, standard deviation, confidence intervals, and relevant percentile statistics allow differences between algorithms to be distinguished from random variation. The number of runs and scenario parameters should be reported so results can be reproduced.

Benchmarking should include strong and diverse baseline algorithms. Nearest-robot dispatch provides a simple operational reference, while greedy and auction-based methods represent practical heuristics. Hungarian matching provides a structured optimal assignment reference for suitable one-to-one problems, and ILP or MILP can provide high-quality solutions for constraint-rich instances. RL-based methods should demonstrate measurable benefits against these established approaches.

No single metric can identify the best task-allocation algorithm for every fleet. Improving throughput may increase energy consumption, minimizing travel may reduce workload fairness, and maximizing solution quality may increase computation latency. Benchmark results should therefore be interpreted as a multi-dimensional performance profile rather than compressed into one score unless the application provides a clearly justified weighting of objectives.

A rigorous task-allocation benchmark ultimately connects algorithmic quality with fleet-level operational value. Reproducible scenarios, realistic constraints, strong baselines, statistical evaluation, and metrics covering assignment cost, throughput, latency, energy, robustness, scalability, and fairness make meaningful comparison possible. Such benchmarking allows designers to determine not merely which algorithm is mathematically sophisticated, but which allocation policy delivers reliable performance under the actual conditions expected in multi-robot fleet operation.

작업 할당 벤치마크(Task Allocation Benchmark)는 다중 로봇 작업 할당(Multi-Robot Task Allocation) 알고리즘이 플릿 자원(Fleet Resource)을 완료된 미션으로 얼마나 효과적으로 전환하는지를 평가하기 위한 체계적인 기준을 제공한다. 서로 다른 할당 방법은 서로 다른 목적을 최적화하므로 단순히 작업이 성공적으로 할당되었는지만 비교하는 것은 충분하지 않다. 유용한 벤치마크는 통제되고 반복 가능한 시나리오에서 운영 효율성, 해의 품질, 계산 비용, 강건성(Robustness), 확장성(Scalability), 공정성(Fairness), 에너지 특성 및 응답성을 평가해야 한다.

벤치마크는 로봇, 작업, 환경 조건 및 운영 제약조건을 포함하는 재현 가능한 문제 인스턴스(Reproducible Problem Instance)를 정의하는 것에서 시작한다. 로봇 정보에는 초기 위치, 이동 클래스, 적재 능력, 기능, 배터리 상태 및 가용성이 포함될 수 있다. 작업에는 위치, 시작 가능 시간(Release Time), 우선순위, 마감시간, 요구 스킬, 서비스 시간 및 에너지 요구량을 지정할 수 있다. 동일한 인스턴스를 사용하면 경쟁 알고리즘을 동일한 작업 부하와 플릿 조건에서 평가할 수 있다.

정적 벤치마크(Static Benchmark)는 할당이 시작되기 전에 알려진 고정된 작업 집합을 평가한다. 모든 알고리즘이 동일한 정보를 제공받고 최적 또는 준최적 기준해와 비교될 수 있으므로 할당 품질을 평가하는 데 유용하다. 동적 벤치마크(Dynamic Benchmark)는 실행 중 새로운 작업을 발생시키며, 미래 수요를 완전히 알 수 없는 창고, 공장, 병원, 검사 시스템 및 서비스 플릿의 실제 운영 환경을 보다 잘 표현한다.

벤치마크 시나리오에서는 플릿 규모와 작업 밀도(Task Density)를 변화시켜 확장성 한계를 확인해야 한다. 소규모 시나리오는 소수의 로봇과 작업만 포함할 수 있지만, 점진적으로 더 큰 사례에서는 수십, 수백 또는 잠재적으로 수천 개의 할당 후보를 포함할 수 있다. 로봇-작업 비율, 작업 도착률 또는 계획 구간(Planning Horizon)을 증가시키면 할당 문제가 복잡해질수록 계산 시간과 해의 품질이 어떻게 변화하는지를 확인할 수 있다.

이종 플릿 벤치마크(Heterogeneous Fleet Benchmark)는 능력 차이를 명시적으로 표현해야 한다. 작업은 적재 능력, 조작, 센싱, 견인, 환경 보호 또는 특수 도구를 요구할 수 있으며, 이러한 요구조건을 만족하는 로봇은 일부에 불과할 수 있다. 이러한 시나리오는 모든 로봇이 모든 작업을 수행할 수 있다고 가정하는 대신 할당기가 적격성(Eligibility), 능력 희소성(Capability Scarcity), 특수 자원 활용을 올바르게 처리하는지를 평가한다.

총 할당 비용(Total Assignment Cost)은 가장 기본적인 성능 지표 중 하나이다. \\(c_{ij}\\)가 로봇 \\(i\\)를 작업 \\(j\\)에 할당하는 비용을 나타낸다면 결과 해는 \\(J=\\sum_i\\sum_j c_{ij}x_{ij}\\)를 이용하여 평가할 수 있다. 벤치마크에 따라 비용은 이동 거리, 실행 시간, 에너지, 경제적 비용 또는 이들의 가중 조합을 나타낼 수 있다. 비교되는 모든 알고리즘에서는 비용의 정확한 정의를 동일하게 유지해야 한다.

최적 기준해(Optimal Reference Solution)를 사용할 수 있는 경우 해의 최적성(Solution Optimality)을 측정할 수 있다. 최적성 격차(Optimality Gap)는 알고리즘이 생성한 비용과 알려진 최적 비용의 차이를 비교하며 일반적으로 상대적인 백분율 차이로 표현된다. 이는 정확하거나 높은 품질의 기준해를 얻을 수 있는 문제 규모에서 탐욕적, 경매 기반, 학습 기반 또는 시간 제한 최적화 방법을 헝가리안 알고리즘(Hungarian Algorithm), ILP 또는 MILP 해와 비교할 때 특히 유용하다.

작업 완료 시간(Task Completion Time)은 개별 미션이 할당 또는 작업 발생 시점부터 완료될 때까지 필요한 시간을 측정한다. 메이크스팬(Makespan)은 하나의 벤치마크 에피소드(Benchmark Episode)에서 전체 작업 집합을 완료하는 데 필요한 시간을 나타낸다. 이동 거리를 최소화하는 할당기가 반드시 메이크스팬을 최소화하는 것은 아니며, 작업 부하가 불균형하게 분배되면 일부 로봇은 과부하 상태가 되고 다른 로봇은 유휴 상태가 될 수 있다. 따라서 개별 완료 시간과 플릿 전체 완료 시간을 모두 고려해야 한다.

처리량(Throughput)은 단위 시간당 성공적으로 완료된 작업의 수를 측정하며 지속적으로 운영되는 플릿에서 특히 중요하다. 창고 운송, 생산 물류 및 서비스 로봇은 하나의 개별 할당 비용보다 지속적인 처리량을 중심으로 평가되는 경우가 많다. 초기화 과정의 영향이 결과를 지배하지 않도록 충분한 시뮬레이션 시간이 경과한 이후의 처리량을 측정하는 것이 바람직하다.

작업 응답 시간(Task Response Time)과 대기열 대기 시간(Queue Waiting Time)은 동적 작업 할당에서 핵심적인 지표이다. 응답 시간은 작업이 이용 가능해진 후 시스템이 얼마나 빠르게 대응하는지를 나타내며, 대기열 대기 시간은 실행이 시작되기 전에 작업이 서비스되지 않은 상태로 얼마나 오래 대기하는지를 측정한다. 평균값도 유용하지만 95번째 또는 99번째 백분위수(Percentile)와 같은 통계는 평균값으로는 드러나지 않는 드물지만 운영상 심각한 지연을 보여준다.

마감시간 성능(Deadline Performance)은 성공적인 작업 완료와 적시 완료를 구분해야 한다. 마감시간 위반율(Deadline Violation Rate)은 요구된 마감시간 이후 완료된 작업의 비율을 나타내며, 지각 시간(Tardiness)은 마감시간을 초과한 지연량을 측정한다. 우선순위 가중 지각 시간(Priority-Weighted Tardiness)을 사용하면 긴급 작업 또는 생산에 중요한 작업에 더 큰 페널티를 부여할 수 있다. 이러한 지표를 통해 높은 작업 부하에서도 할당기가 서비스 품질을 유지하는지를 평가할 수 있다.

로봇 활용률(Robot Utilization)은 전체 운영 시간 중 생산적인 작업을 수행하는 시간의 비율을 나타낸다. 평균 활용률을 최대화하더라도 일부 로봇에만 작업이 집중될 수 있으므로 활용률은 작업 부하 균형(Workload Balance)과 함께 해석해야 한다. 로봇별 작업 수, 작업 시간, 이동 거리 또는 에너지 사용량의 분산(Variance)과 같은 지표를 통해 작업이 공정하게 분배되는지, 특정 플랫폼이 지속적인 병목 자원(Bottleneck Resource)이 되는지를 확인할 수 있다.

이동 효율성(Travel Efficiency)은 일반적으로 총 이동 거리, 공차 이동 거리(Empty Travel Distance) 및 이동 시간을 이용하여 측정한다. 공차 이동은 적재물을 운반하지 않는 이동이 플릿 자원을 소비하면서 직접적인 생산 작업을 완료하지 않기 때문에 물류 시스템에서 특히 중요하다. 생산적인 이동과 비생산적인 이동을 비교하면 할당기가 지리적으로 일관된 작업 순서를 구성하는지 또는 로봇을 작업 영역 전체에 반복적으로 이동시키는지를 판단할 수 있다.

에너지 지표(Energy Metric)는 배터리 기반 플릿에서 점점 더 중요해지고 있다. 평가 항목에는 총 에너지 소비량, 완료 작업당 에너지, 최소 충전 상태(State of Charge, SoC), 충전 빈도, 충전 시간 및 에너지 부족으로 실행 불가능한 할당 수가 포함될 수 있다. 배터리 인식 할당기(Battery-Aware Allocator)의 경우 충전기 활용률과 충전 대기 시간도 측정해야 한다. 겉으로는 에너지 효율적인 정책이라도 충전 인프라의 혼잡을 발생시킬 수 있기 때문이다.

계산 지연시간(Computational Latency)은 할당 결정을 생성하는 데 필요한 시간을 측정한다. 실시간 시스템에서는 간헐적으로 발생하는 극단적인 지연이 플릿 운영을 중단시킬 수 있으므로 평균 지연시간만으로는 충분하지 않다. 따라서 중앙값(Median), 최댓값 및 높은 백분위수 지연시간도 기록해야 한다. 계산 성능을 비교하는 경우 가능한 한 동일한 하드웨어와 구현 조건에서 알고리즘을 평가해야 한다.

확장성 분석(Scalability Analysis)은 로봇과 작업의 수가 증가할 때 계산 시간, 메모리 사용량, 통신 트래픽 및 해의 품질이 어떻게 변화하는지를 평가한다. 10대의 로봇에서는 뛰어난 할당을 생성하는 알고리즘도 수백 대 규모에서는 실용적이지 않을 수 있다. 하나의 벤치마크 규모만 평가하는 것보다 스케일링 곡선(Scaling Curve)을 분석하면 문제 분해, 계층화, 근사화 또는 분산형 할당이 필요한 플릿 규모를 파악할 수 있다.

통신 오버헤드(Communication Overhead)는 경매 기반 및 분산형 방법에서 특히 중요하다. 유용한 측정 지표에는 메시지 수, 전송 데이터량, 입찰 라운드(Bidding Round), 동기화 이벤트 및 할당 주기당 통신 지연시간이 포함된다. 계산이 분산되어 있다는 이유만으로 분산 알고리즘을 확장 가능하다고 평가해서는 안 되며, 플릿 규모 증가에 따라 통신 요구량이 지나치게 증가하지 않는지도 확인해야 한다.

강건성 벤치마크(Robustness Benchmark)는 정상적인 시나리오에는 존재하지 않았던 장애 상황을 도입한다. 로봇 고장, 통신 손실, 경로 차단, 충전기 고장, 작업 취소, 실행 지연 및 갑작스러운 우선순위 변경 등을 운영 중에 발생시킬 수 있다. 이후 복구 시간(Recovery Time), 작업 손실, 재할당 횟수, 처리량 감소 및 서비스 연속성을 측정하여 기존 가정이 깨졌을 때 할당기가 얼마나 효과적으로 대응하는지를 평가한다.

재할당 빈도(Reassignment Frequency)는 할당 안정성(Allocation Stability)을 평가하는 중요한 지표이다. 동적 최적화는 지속적으로 조금 더 나은 해를 발견할 수 있지만 로봇의 미션을 반복적으로 변경하면 경로 변경 오버헤드와 운영 혼란을 발생시킬 수 있다. 벤치마크에서는 할당이 얼마나 자주 변경되는지, 변경으로 어느 정도의 성능 개선이 발생하는지, 그리고 로봇이 유용한 작업을 완료하기 전에 할당 스래싱(Assignment Thrashing)을 경험하는지를 기록해야 한다.

공정성(Fairness)과 기아 상태(Starvation) 지표는 작업이나 로봇이 제한된 자원을 놓고 경쟁하는 환경에서 중요하다. 최대 작업 대기 시간, 기아 발생률(Starvation Rate), 우선순위 준수율 및 로봇 간 작업 부하 분포를 이용하면 전체 처리량만으로는 드러나지 않는 바람직하지 않은 동작을 확인할 수 있다. 저우선순위 작업을 무기한 연기하여 높은 생산성을 달성하는 정책은 평균 성능이 우수하더라도 실제 운영에서는 허용되지 않을 수 있다.

학습 기반 할당기(Learning-Based Allocator)는 추가적인 평가가 필요하다. 학습 보상(Training Reward)만을 성능의 충분한 증거로 사용해서는 안 된다. 정책은 학습에 사용하지 않은 작업 흐름, 지도, 플릿 규모, 능력 조합, 혼잡 수준 및 고장 패턴을 대상으로 시험해야 한다. 일반화 격차(Generalization Gap), 추론 지연시간(Inference Latency), 제약조건 위반율 및 비학습 기준 알고리즘 대비 성능은 실제 배포 준비 수준을 판단하는 보다 의미 있는 지표를 제공한다.

동적 플릿 시뮬레이션에는 무작위성이 포함되므로 통계적 방법론(Statistical Methodology)이 필요하다. 각 구성은 통제된 난수 시드(Random Seed)를 사용하여 여러 번 독립적으로 실행하고 평가해야 한다. 평균, 표준편차(Standard Deviation), 신뢰구간(Confidence Interval) 및 관련 백분위수 통계를 이용하면 알고리즘 사이의 차이와 무작위 변동을 구분할 수 있다. 결과를 재현할 수 있도록 실행 횟수와 시나리오 파라미터도 함께 보고해야 한다.

벤치마킹에는 강력하면서도 다양한 기준 알고리즘(Baseline Algorithm)이 포함되어야 한다. 최근접 로봇 디스패치(Nearest-Robot Dispatch)는 단순한 운영 기준을 제공하고, 탐욕적 및 경매 기반 방법은 실용적인 휴리스틱(Heuristic)을 대표한다. 헝가리안 매칭(Hungarian Matching)은 적합한 일대일 문제에 대해 구조화된 최적 할당 기준을 제공하며, ILP 또는 MILP는 다양한 제약조건을 포함하는 문제에 대해 높은 품질의 해를 제공할 수 있다. RL 기반 방법은 이러한 기존 접근법과 비교하여 측정 가능한 이점을 입증해야 한다.

어떠한 단일 지표도 모든 플릿에서 가장 좋은 작업 할당 알고리즘을 결정할 수는 없다. 처리량을 향상시키면 에너지 소비가 증가할 수 있고, 이동 거리를 최소화하면 작업 부하 공정성이 감소할 수 있으며, 해의 품질을 최대화하면 계산 지연시간이 증가할 수 있다. 따라서 애플리케이션에서 명확하게 정당화된 목적 가중치를 제공하지 않는 한 벤치마크 결과를 하나의 점수로 압축하기보다 다차원 성능 프로파일(Multi-Dimensional Performance Profile)로 해석해야 한다.

엄격한 작업 할당 벤치마크는 궁극적으로 알고리즘의 품질과 플릿 수준의 운영 가치(Fleet-Level Operational Value)를 연결한다. 재현 가능한 시나리오, 현실적인 제약조건, 강력한 기준 알고리즘, 통계적 평가와 함께 할당 비용, 처리량, 지연시간, 에너지, 강건성, 확장성 및 공정성을 포괄하는 지표를 사용하면 의미 있는 비교가 가능하다. 이러한 벤치마킹을 통해 설계자는 단순히 어떤 알고리즘이 수학적으로 정교한지를 판단하는 것이 아니라 실제 다중 로봇 플릿 운영에서 예상되는 조건 아래 어떤 할당 정책이 신뢰할 수 있는 성능을 제공하는지를 판단할 수 있다.

##  

## 02.10 Warehouse Dynamic Order Task Allocation Case

![](images/image10.png){width="7.268055555555556in" height="7.268055555555556in"}

A warehouse dynamic order allocation system must continuously transform incoming customer orders, replenishment requests, inventory movements, and operational events into executable robot missions. Unlike static warehouse planning, where all transport jobs are known before execution, real fulfillment centers receive orders throughout the operating period. The fleet manager must therefore allocate tasks while robots are moving, charging, waiting, loading, unloading, or completing previously assigned missions.

The operational environment can be represented as a network of storage locations, picking stations, packing stations, replenishment zones, charging stations, elevators, and traffic intersections. Autonomous Mobile Robots (AMRs) move containers, racks, pallets, or individual goods between these resources. Every new order creates one or more transport requirements whose execution depends on inventory location, workstation demand, robot availability, congestion, and current warehouse priorities.

Incoming orders are first decomposed into robot-executable tasks. A customer order containing several stock keeping units may generate retrieval tasks from multiple storage locations, while a replenishment request may require movement from receiving or buffer areas to storage. The warehouse management layer determines what material must move, and the fleet allocation layer determines which robot should perform each physical movement and when it should be executed.

Dynamic arrival makes task priority time dependent. Standard orders may initially receive normal priority, while express orders, production shortages, or workstation starvation events require immediate service. Tasks approaching shipping cut-off times can gradually increase in urgency. The allocator should therefore use continuously updated priority values rather than assuming that the priority assigned when an order first entered the system remains unchanged throughout execution.

At each decision epoch, the fleet state contains idle robots, robots executing tasks, robots expected to become available soon, queued missions, battery states, charger conditions, and traffic information. The allocator evaluates candidate robot-task relationships using this current state. A robot that is slightly farther from a pickup location may still be preferable if its current trajectory ends nearby or if assigning another robot would create a future resource shortage.

Travel distance alone is insufficient for warehouse allocation. The effective assignment cost should consider estimated travel time, pickup and delivery service time, congestion, queue delay, battery consumption, workload, and task urgency. A simplified cost can combine these factors as \\(c_{ij}=w_dD_{ij}+w_tT_{ij}+w_eE_{ij}+w_qQ_j-w_pP_j\\), where the weighting terms reflect the warehouse\'s operational objectives.

Candidate filtering can significantly reduce computational load. Robots that cannot handle the required payload, container type, docking interface, operating zone, or task-specific equipment are removed before optimization. Robots with insufficient battery reserve or those that cannot reach the pickup location within a required time window can also be excluded. The allocator then compares only feasible candidates instead of evaluating every robot against every waiting task.

Immediate dispatch is useful when order volume is moderate and response time is critical. As soon as a task arrives, the system selects an appropriate robot and dispatches it. This minimizes allocation latency but may sacrifice global efficiency because the allocator commits resources without seeing tasks that will arrive moments later. A sequence of locally reasonable decisions can therefore produce unnecessary travel or uneven robot utilization during high-demand periods.

Periodic batching offers an alternative for dense order streams. Newly arriving tasks can be accumulated for a short interval and optimized together using greedy matching, auction methods, the Hungarian Algorithm, or mathematical optimization. Batch allocation can produce more efficient robot-task combinations but increases waiting time before dispatch. The batch duration must therefore balance order responsiveness against the benefit of considering multiple tasks simultaneously.

A practical warehouse system can combine immediate and batch allocation. Emergency or high-priority orders can trigger immediate assignment, while normal orders enter a short batching window. This hybrid policy prevents urgent work from waiting for the next optimization cycle while allowing routine tasks to benefit from coordinated matching. Event-triggered replanning can additionally occur after robot failures, major congestion changes, task cancellations, or workstation starvation.

Robot availability should include predicted completion state rather than only current idle status. Suppose Robot A is idle but far from a pickup point, while Robot B is completing a delivery close to that location. Reserving the next task for Robot B may reduce total empty travel even though Robot A is immediately available. Predicted completion time and position therefore provide important information for dynamic warehouse assignment.

Task chaining can further improve transport efficiency. Instead of evaluating every mission independently, the allocator can consider whether a robot finishing one delivery is well positioned for the pickup of another task. Effective chaining reduces empty travel and creates geographically coherent mission sequences. However, excessive chaining should not cause one robot to accumulate a long task queue while nearby robots remain underutilized.

Workstation demand introduces another important allocation signal. Picking and packing stations depend on a continuous supply of required inventory. If a station is close to becoming starved, tasks supplying that station should receive increased priority even when other orders have waited longer. Conversely, sending too many robots to the same station can create queues. Allocation should therefore consider both workstation starvation risk and station-side congestion.

Traffic congestion couples task allocation with fleet navigation. A geometrically short route may cross a heavily congested aisle, while a slightly longer assignment may use a less crowded region and finish earlier. Travel-time estimates should therefore incorporate current or predicted traffic conditions. Fleet-level congestion penalties can also discourage the allocator from sending too many robots toward the same narrow corridor or intersection simultaneously.

Battery management must operate together with order allocation. A robot should have enough energy to reach the pickup location, complete delivery, preserve a safety reserve, and reach a charger afterward. Low-energy robots may be assigned short missions near charging infrastructure, while robots with larger reserves handle distant work. Charging tasks can be inserted into the same queue so that productive work and energy recovery are coordinated.

Warehouse demand commonly exhibits bursts rather than a uniform arrival rate. Order releases, shipping deadlines, shift changes, production events, and promotional demand can suddenly increase the task queue. During a burst, the allocator should prioritize throughput and critical deadlines while avoiding excessive reassignment. Once demand decreases, the system can recover workload balance, reposition robots, and perform opportunity charging.

Repositioning idle robots can improve response to future orders. Historical demand or short-term prediction may indicate that certain storage zones or workstations will soon generate many tasks. Instead of leaving idle robots where their previous missions ended, the fleet manager can move selected robots toward anticipated demand regions. Repositioning consumes energy and traffic capacity, so it should be used only when expected future benefits justify the movement.

Order cancellation and inventory changes require online recovery. If an order is canceled before pickup, the associated robot task can be removed and the robot returned to the candidate pool. If inventory is unavailable at the expected location, the warehouse system may generate a replacement retrieval task from another location. The allocator must process these events without allowing obsolete missions to continue through the execution pipeline.

Robot failures are handled similarly through dynamic reassignment. When a robot becomes unavailable, tasks that have not physically begun can return to the waiting queue. Tasks involving already loaded material may require recovery procedures, another robot, or human intervention depending on warehouse design. Explicit task states prevent the allocator from automatically reassigning work whose physical execution has already changed the state of inventory.

Large warehouses benefit from hierarchical allocation. The facility can be divided into zones, floors, or functional regions, with a higher-level allocator distributing demand among robot groups and local allocators performing detailed assignments. This reduces the number of candidate robot-task pairs considered at each decision point. It can also limit unnecessary cross-zone traffic while preserving the ability to rebalance robots when demand shifts between regions.

Rolling-horizon planning provides a practical compromise between reactive dispatch and long-term optimization. The allocator optimizes currently known orders and near-term predicted demand over a limited horizon, commits immediate missions, and leaves later assignments flexible. After new orders arrive or robot states change, the horizon advances and the allocation is recalculated. This allows planning to adapt without assuming that a fixed warehouse schedule will remain valid.

A representative evaluation scenario should reproduce realistic order arrival patterns, robot movement, workstation service times, charging behavior, congestion, and disturbances. Allocation policies can then be compared under identical demand streams. Low-load, nominal-load, peak-load, and overload conditions are particularly useful because an algorithm that performs well under normal demand may degrade sharply as utilization approaches fleet capacity.

Key performance indicators include order throughput, task response time, queue waiting time, order completion time, shipping deadline violations, robot utilization, empty travel distance, energy consumption, charger utilization, and allocation computation latency. High-percentile waiting and completion times are also important because a small number of severely delayed orders can affect service-level agreements even when average performance remains acceptable.

The warehouse case demonstrates that dynamic task allocation is not simply a nearest-robot selection problem. Effective operation requires continuous integration of order arrivals, inventory movement, task priority, predicted robot availability, traffic, workstation demand, battery state, charging resources, and execution feedback. By repeatedly observing, allocating, dispatching, monitoring, and replanning, the fleet manager can convert rapidly changing warehouse demand into coordinated robot activity while maintaining throughput, responsiveness, and operational stability.

창고 동적 주문 할당 시스템(Warehouse Dynamic Order Allocation System)은 지속적으로 유입되는 고객 주문, 보충 요청, 재고 이동 및 운영 이벤트를 실행 가능한 로봇 미션(Robot Mission)으로 지속적으로 변환해야 한다. 모든 운송 작업이 실행 전에 알려지는 정적 창고 계획(Static Warehouse Planning)과 달리 실제 풀필먼트 센터(Fulfillment Center)에서는 운영 시간 동안 주문이 계속 유입된다. 따라서 플릿 관리자(Fleet Manager)는 로봇이 이동, 충전, 대기, 적재, 하역 또는 기존 미션을 수행하는 동안에도 작업을 할당해야 한다.

운영 환경은 저장 위치, 피킹 스테이션(Picking Station), 패킹 스테이션(Packing Station), 보충 구역, 충전 스테이션, 엘리베이터 및 교통 교차로로 구성된 네트워크로 표현할 수 있다. 자율 이동 로봇(Autonomous Mobile Robot, AMR)은 이러한 자원 사이에서 컨테이너, 랙, 팔레트 또는 개별 상품을 이동시킨다. 새로운 주문이 발생할 때마다 하나 이상의 운송 요구가 생성되며, 실행 여부와 방식은 재고 위치, 작업 스테이션 수요, 로봇 가용성, 혼잡 및 현재 창고의 우선순위에 따라 결정된다.

유입된 주문은 먼저 로봇이 실행할 수 있는 작업(Robot-Executable Task)으로 분해된다. 여러 재고 관리 단위(Stock Keeping Unit, SKU)를 포함하는 고객 주문은 여러 저장 위치에서 회수 작업을 생성할 수 있으며, 보충 요청은 입고 또는 버퍼 구역에서 저장 구역으로 상품을 이동하도록 요구할 수 있다. 창고 관리 계층(Warehouse Management Layer)은 어떤 자재를 이동해야 하는지를 결정하고, 플릿 할당 계층(Fleet Allocation Layer)은 각 물리적 이동을 어떤 로봇이 언제 수행할지를 결정한다.

동적 작업 도착(Dynamic Arrival)은 작업 우선순위를 시간에 따라 변화하도록 만든다. 일반 주문은 처음에는 정상 우선순위를 가질 수 있지만, 특급 주문, 생산 자재 부족 또는 작업 스테이션 고갈(Workstation Starvation) 이벤트는 즉각적인 서비스를 요구할 수 있다. 출하 마감시간(Shipping Cut-Off Time)에 가까워지는 작업은 점진적으로 긴급도가 증가할 수 있다. 따라서 할당기는 주문이 시스템에 처음 입력되었을 때 지정된 우선순위가 실행 과정 전체에서 그대로 유지된다고 가정하지 않고 지속적으로 갱신되는 우선순위 값을 사용해야 한다.

각 의사결정 시점(Decision Epoch)에서 플릿 상태에는 유휴 로봇, 작업을 수행 중인 로봇, 곧 가용 상태가 될 것으로 예상되는 로봇, 대기 중인 미션, 배터리 상태, 충전기 상태 및 교통 정보가 포함된다. 할당기는 이러한 현재 상태를 이용하여 후보 로봇-작업 관계를 평가한다. 픽업 위치에서 약간 더 멀리 떨어진 로봇이라도 현재 이동 경로가 해당 위치 근처에서 종료되거나 다른 로봇을 할당할 경우 미래의 자원 부족이 발생한다면 더 좋은 선택이 될 수 있다.

창고 작업 할당에서는 이동 거리만으로 충분하지 않다. 실질적인 할당 비용(Effective Assignment Cost)은 예상 이동 시간, 픽업 및 배송 서비스 시간, 혼잡, 대기열 지연, 배터리 소비량, 작업 부하 및 작업 긴급도를 고려해야 한다. 단순화된 비용은 \\(c_{ij}=w_dD_{ij}+w_tT_{ij}+w_eE_{ij}+w_qQ_j-w_pP_j\\)와 같이 이러한 요소를 결합할 수 있으며, 각 가중치 항은 창고의 운영 목표를 반영한다.

후보 필터링(Candidate Filtering)은 계산 부하를 크게 줄일 수 있다. 요구되는 적재량, 컨테이너 유형, 도킹 인터페이스(Docking Interface), 운영 구역 또는 작업별 장비를 처리할 수 없는 로봇은 최적화 전에 제거된다. 배터리 예비량이 부족하거나 요구된 시간 범위 안에 픽업 위치까지 도달할 수 없는 로봇 역시 제외할 수 있다. 이를 통해 할당기는 모든 로봇과 모든 대기 작업을 비교하는 대신 실행 가능한 후보만 평가한다.

즉시 디스패치(Immediate Dispatch)는 주문량이 중간 수준이고 응답 시간이 중요한 경우 유용하다. 작업이 도착하는 즉시 시스템이 적합한 로봇을 선택하여 디스패치한다. 이 방식은 할당 지연시간(Allocation Latency)을 최소화하지만 잠시 후 도착할 작업을 알지 못한 상태에서 자원을 확정하기 때문에 전체 효율성을 희생할 수 있다. 따라서 개별적으로는 합리적인 일련의 결정이 높은 수요 상황에서는 불필요한 이동이나 불균등한 로봇 활용을 발생시킬 수 있다.

주기적 배치(Periodic Batching)는 밀집된 주문 흐름에 대한 대안을 제공한다. 새롭게 도착하는 작업을 짧은 시간 동안 누적한 후 탐욕적 매칭(Greedy Matching), 경매 방식(Auction Method), 헝가리안 알고리즘(Hungarian Algorithm) 또는 수학적 최적화(Mathematical Optimization)를 이용하여 함께 최적화할 수 있다. 배치 할당(Batch Allocation)은 보다 효율적인 로봇-작업 조합을 생성할 수 있지만 디스패치 전 대기 시간을 증가시킨다. 따라서 배치 시간은 주문 응답성과 여러 작업을 동시에 고려함으로써 얻는 이점 사이에서 균형을 이루어야 한다.

실제 창고 시스템에서는 즉시 할당과 배치 할당을 결합할 수 있다. 긴급 또는 고우선순위 주문은 즉각적인 할당을 트리거하고 일반 주문은 짧은 배치 구간(Batching Window)에 입력할 수 있다. 이러한 하이브리드 정책(Hybrid Policy)은 긴급 작업이 다음 최적화 주기까지 기다리는 것을 방지하면서 일반 작업은 조정된 매칭의 이점을 활용하도록 한다. 또한 로봇 고장, 심각한 혼잡 변화, 작업 취소 또는 작업 스테이션 고갈이 발생하면 이벤트 트리거 재계획(Event-Triggered Replanning)을 수행할 수 있다.

로봇 가용성(Robot Availability)은 현재의 유휴 상태뿐만 아니라 예상 작업 완료 상태(Predicted Completion State)를 포함해야 한다. 예를 들어 로봇 A는 유휴 상태이지만 픽업 위치에서 멀리 떨어져 있고, 로봇 B는 해당 위치 근처에서 배송을 완료하고 있다고 가정할 수 있다. 이 경우 다음 작업을 로봇 B에 예약하면 로봇 A가 즉시 사용 가능하더라도 전체 공차 이동(Empty Travel)을 줄일 수 있다. 따라서 예상 완료 시간과 예상 완료 위치는 동적 창고 작업 할당에서 중요한 정보가 된다.

작업 체이닝(Task Chaining)을 이용하면 운송 효율성을 더욱 향상시킬 수 있다. 각 미션을 독립적으로 평가하는 대신 하나의 배송을 완료한 로봇이 다음 작업의 픽업 위치에 적절하게 배치되는지를 고려할 수 있다. 효과적인 작업 체이닝은 공차 이동을 줄이고 지리적으로 일관된 미션 순서를 형성한다. 그러나 과도한 체이닝으로 인해 한 로봇에 긴 작업 대기열이 누적되는 동안 주변의 다른 로봇이 유휴 상태로 남지 않도록 해야 한다.

작업 스테이션 수요(Workstation Demand)는 또 다른 중요한 할당 신호를 제공한다. 피킹 및 패킹 스테이션은 필요한 재고가 지속적으로 공급되어야 한다. 특정 스테이션에서 필요한 재고가 곧 부족해질 가능성이 있다면 해당 스테이션에 공급하는 작업은 다른 주문보다 대기 시간이 짧더라도 우선순위를 높여야 한다. 반대로 동일한 스테이션으로 지나치게 많은 로봇을 보내면 대기열이 발생할 수 있다. 따라서 할당에서는 작업 스테이션 고갈 위험과 스테이션 측 혼잡을 함께 고려해야 한다.

교통 혼잡(Traffic Congestion)은 작업 할당과 플릿 내비게이션(Fleet Navigation)을 서로 연결한다. 기하학적으로 짧은 경로가 심하게 혼잡한 통로를 통과할 수 있는 반면 약간 더 긴 경로를 이용하는 작업 할당이 혼잡하지 않은 영역을 통과하여 더 빨리 완료될 수 있다. 따라서 이동 시간 추정에는 현재 또는 예상 교통 상황을 반영해야 한다. 또한 플릿 수준의 혼잡 페널티(Congestion Penalty)를 적용하여 너무 많은 로봇이 동일한 좁은 통로나 교차로로 동시에 이동하는 것을 억제할 수 있다.

배터리 관리(Battery Management)는 주문 할당과 함께 동작해야 한다. 로봇은 픽업 위치까지 이동하고 배송을 완료한 후 안전 예비량(Safety Reserve)을 유지하면서 충전기까지 도달할 수 있는 충분한 에너지를 보유해야 한다. 에너지가 부족한 로봇에는 충전 인프라 근처의 짧은 미션을 할당하고, 에너지 여유가 큰 로봇에는 원거리 작업을 할당할 수 있다. 충전 작업(Charging Task) 자체를 동일한 대기열에 삽입하여 생산 작업과 에너지 회복을 함께 조정할 수 있다.

창고 수요는 일반적으로 일정한 도착률보다는 수요 폭증(Burst)을 나타낸다. 주문 릴리스(Order Release), 출하 마감, 교대 시간 변경, 생산 이벤트 및 프로모션 수요로 인해 작업 대기열이 갑자기 증가할 수 있다. 수요 폭증 기간에는 할당기가 과도한 재할당을 피하면서 처리량과 중요한 마감시간을 우선해야 한다. 수요가 감소하면 작업 부하 균형을 회복하고 로봇을 재배치하며 기회 충전(Opportunity Charging)을 수행할 수 있다.

유휴 로봇 재배치(Repositioning)는 향후 주문에 대한 응답성을 향상시킬 수 있다. 과거 수요 또는 단기 예측을 통해 특정 저장 구역이나 작업 스테이션에서 곧 많은 작업이 발생할 것으로 예상할 수 있다. 유휴 로봇을 이전 미션이 종료된 위치에 그대로 두는 대신 일부 로봇을 예상 수요 지역으로 이동시킬 수 있다. 그러나 재배치는 에너지와 교통 용량을 소비하므로 예상되는 미래 이점이 이동 비용을 정당화할 수 있는 경우에만 적용해야 한다.

주문 취소(Order Cancellation)와 재고 변경은 온라인 복구(Online Recovery)를 필요로 한다. 픽업 전에 주문이 취소되면 관련 로봇 작업을 제거하고 로봇을 다시 후보 풀(Candidate Pool)로 반환할 수 있다. 예상 위치에서 재고를 사용할 수 없다면 창고 시스템이 다른 위치에서 새로운 회수 작업을 생성할 수 있다. 할당기는 이러한 이벤트를 처리하면서 더 이상 유효하지 않은 미션이 실행 파이프라인을 통해 계속 진행되지 않도록 해야 한다.

로봇 고장(Robot Failure) 역시 동적 재할당(Dynamic Reassignment)을 통해 처리한다. 로봇이 운용 불가능한 상태가 되면 물리적인 실행이 아직 시작되지 않은 작업을 대기열로 반환할 수 있다. 이미 적재된 물품과 관련된 작업은 창고 설계에 따라 복구 절차, 다른 로봇 또는 사람의 개입이 필요할 수 있다. 명확한 작업 상태(Task State)를 사용하면 물리적인 실행으로 이미 재고 상태가 변경된 작업을 할당기가 자동으로 다시 할당하는 것을 방지할 수 있다.

대규모 창고에서는 계층적 할당(Hierarchical Allocation)이 유용하다. 시설을 구역, 층 또는 기능 영역으로 분할하고 상위 수준 할당기(Higher-Level Allocator)가 로봇 그룹 사이에 수요를 분배한 후 로컬 할당기(Local Allocator)가 세부 작업을 할당할 수 있다. 이를 통해 각 의사결정 시점에서 고려해야 하는 후보 로봇-작업 조합의 수를 줄일 수 있다. 또한 구역 간 수요 변화에 따라 로봇을 재균형화하면서 불필요한 구역 간 이동을 제한할 수 있다.

롤링 호라이즌 계획(Rolling-Horizon Planning)은 반응형 디스패치(Reactive Dispatch)와 장기 최적화 사이의 실용적인 절충안을 제공한다. 할당기는 현재 알려진 주문과 제한된 계획 구간 안의 단기 예상 수요를 최적화하고 즉시 수행해야 하는 미션은 확정하면서 이후 할당은 유연하게 유지한다. 새로운 주문이 도착하거나 로봇 상태가 변화하면 계획 구간을 앞으로 이동시키고 할당을 다시 계산한다. 이를 통해 고정된 창고 일정이 계속 유효할 것이라고 가정하지 않고 변화에 적응할 수 있다.

대표적인 평가 시나리오(Evaluation Scenario)는 현실적인 주문 도착 패턴, 로봇 이동, 작업 스테이션 서비스 시간, 충전 동작, 혼잡 및 장애 상황을 재현해야 한다. 이후 동일한 수요 흐름을 이용하여 여러 작업 할당 정책을 비교할 수 있다. 저부하(Low-Load), 정상 부하(Nominal-Load), 최대 부하(Peak-Load) 및 과부하(Overload) 조건은 특히 중요하다. 정상적인 수요에서는 좋은 성능을 보이는 알고리즘도 플릿 활용률이 최대 용량에 가까워지면 성능이 급격하게 저하될 수 있기 때문이다.

핵심 성능 지표(Key Performance Indicator, KPI)에는 주문 처리량(Order Throughput), 작업 응답 시간, 대기열 대기 시간, 주문 완료 시간, 출하 마감시간 위반, 로봇 활용률, 공차 이동 거리, 에너지 소비량, 충전기 활용률 및 할당 계산 지연시간(Allocation Computation Latency)이 포함된다. 높은 백분위수(High-Percentile)의 대기 시간과 완료 시간도 중요하다. 평균 성능이 양호하더라도 소수의 주문에서 심각한 지연이 발생하면 서비스 수준 협약(Service-Level Agreement, SLA)에 영향을 줄 수 있기 때문이다.

이 창고 사례는 동적 작업 할당(Dynamic Task Allocation)이 단순히 가장 가까운 로봇을 선택하는 문제가 아니라는 것을 보여준다. 효과적인 운영을 위해서는 주문 도착, 재고 이동, 작업 우선순위, 예상 로봇 가용성, 교통 상황, 작업 스테이션 수요, 배터리 상태, 충전 자원 및 실행 피드백(Execution Feedback)을 지속적으로 통합해야 한다. 플릿 관리자가 관측, 할당, 디스패치, 모니터링 및 재계획을 반복적으로 수행하면 빠르게 변화하는 창고 수요를 조정된 로봇 활동으로 전환하면서 높은 처리량, 응답성 및 운영 안정성을 유지할 수 있다.
