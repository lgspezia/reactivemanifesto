리액티브 선언문 (The Reactive Manifesto)
-----------------------

다른 분야에서 활동하는 조직들은 유사한 소프트웨어를 구축하기 위한 패턴들을 독립적으로 발견하고 있습니다. 이러한 시스템은 보다 견고하고, 탄력적이며, 유연하며 최신의 요구사항을 반영하기 쉽습니다.

최근 몇 년간 애플리케이션의 요구사항이 급격하게 변화했기 때문에 이러한 변화가 발생하고 있습니다. 불과 몇 년 전까지만 해도 거대한 애플리케이션은 수십 개의 서버로 구성되어, 몇 초의 응답 시간과 몇 시간의 오프라인 유지보수를 허용하고, 기가 바이트 데이터를 담고 있었습니다. 오늘날의 애플리케이션은 모바일 기기에서 부터 수천 개의 멀티 코어 프로세서에서 동작하는 클라우드 기반의 클러스터까지, 모든 기기에 배포되고 있습니다. 사용자는 밀리초의 응답 시간과 100%의 가동률을 기대합니다. 데이터는 페타 바이트 단위로 측정됩니다. 이전의 소프트웨어 아키텍처는 오늘날의 요구사항에 쉽게 부응하지 못합니다.

우리는 시스템 아키텍처에 대한 일관성 있는 접근이 필요하며, 필요한 모든 측면은 이미 개별적으로 인식되고 있다고 생각합니다. 즉, 응답이 잘 되고, 탄력적이며 유연하고 메시지 기반으로 동작하는 시스템 입니다. 우리는 이것을 리액티브 시스템(Reactive Systems)라고 부릅니다.

리액티브 시스템으로 구축된 시스템은 보다 유연하고, 느슨한 결합을 갖고, [확장성](/glossary#Scalability)이 있습니다. 이로 인해 개발이 더 쉬워지고 변경 사항을 적용하기 쉬워집니다. 이 시스템은 [장애](/glossary#Failure)에 대해 더 강한 내성을 지니며, 비록 장애가 발생 하더라도, 재난이 일어나기 보다는 간결한 방식으로 해결합니다. 리액티브 시스템은 높은 응답성을 가지며 [사용자](/glossary#User)에게 효과적인 상호적 피드백을 제공합니다.

*리액티브 시스템은:*

* <a name="Responsive"></a>**응답성(Responsive)**: [시스템](/glossary#System)이 가능한 한 즉각적으로 응답하는 것을 응답성이 있다고 합니다. 응답성은 사용자의 편의성과 유용성의 기초가 되지만, 그것뿐만 아니라 문제를 신속하게 탐지하고 효과적으로 대처할 수 있는 것을 의미합니다. 응답성 있는 시스템은 신속하고 일관성 있는 응답 시간을 제공하고, 신뢰할 수 있는 상한선을 설정하여 일관된 서비스 품질을 제공합니다. 이러한 일관된 동작은 오류 처리를 단순화하고, 일반 사용자에게 신뢰를 조성하고, 새로운 상호작용을 촉진합니다.
* <a name="Resilient"></a>**탄력성(Resilient)**: 시스템이 [장애](/glossary#Failure)에 직면하더라도 응답성을 유지 하는 것을 탄력성이 있다고 합니다. 탄력성은 고가용성 시스템, 미션 크리티컬 시스템에만 적용되지 않습니다. 탄력성이 없는 시스템은 장애가 발생할 경우 응답성을 잃게 됩니다. 탄력성은 [복제](/glossary#Replication), 봉쇄, [격리](/glossary#Isolation), [위임](/glossary#Delegation)에 의해 실현됩니다. 장애는 각각의 [구성 요소](/glossary#Component)에 포함되며 구성 요소들은 서로 분리되어 있기 때문에 이는 시스템이 부분적으로 고장이 나더라도, 전체 시스템을 위험하게 하지 않고 복구 할 수 있도록 보장합니다. 각 구성 요소의 복구 프로세스는 다른(외부의) 구성 요소에 위임되며 필요한 경우 복제를 통해 고가용성이 보장됩니다. 구성 요소의 클라이언트는 장애를 처리하는데에 압박을 받지 않습니다.
* <a name="Elastic"></a>**유연성(Elastic)**: 시스템이 작업량이 변화하더라도 응답성을 유지하는 것을 유연성이라고 합니다. 리액티브 시스템은 입력 속도의 변화에 따라 이러한 입력에 할당된 [자원](/glossary#Resource)을 증가시키거나 감소키면서 변화에 대응합니다. 이것은 시스템에서 경쟁하는 지점이나 중앙 집중적인 병목 현상이 존재하지 않도록 설계하여, 구성 요소를 샤딩하거나 복제하여 입력을 분산시키는 것을 의미합니다. 리액티브 시스템은 실시간 성능을 측정하는 도구를 제공하여 응답성 있고 예측 가능한 규모 확장 알고리즘을 지원합니다. 이 시스템은 하드웨어 상품 및 소프트웨어 플랫폼에 비용 효율이 높은 방식으로 [유연성](/glossary#Elasticity)을 제공합니다.
* <a name="Message-Driven"></a>**메시지 구동(Message Driven)**: 리액티브 시스템은 [비동기](/glossary#Asynchronous) [메시지 전달](/glossary#Message-Driven)에 의존하여 구성 요소 사이에서 느슨한 결합, 격리, [위치 투명성](/glossary#Location-Transparency)을 보장하는 경계를 형성합니다. 이 경계는 [장애](/glossary#Failure)를 메시지로 지정하는 수단을 제공합니다. 명시적인 메시지 전달은 시스템에 메시지 큐를 생성하고, 모니터링하며 필요시 [배압](/glossary#Back-Pressure)을 적용함으로써 유연성을 부여하고, 부하 관리와 흐름제어를 가능하게 합니다. 위치 투명 메시징을 통신 수단으로 사용하면 단일 호스트든 클러스터를 가로지르든 동일한 구성과 의미를 갖고 장애를 관리할 수 있습니다. [논블로킹](/glossary#Non-Blocking) 통신은 수신자가 활성화가 되어 있을 때만 [자원](/glossary#Resource)을 소비할 수 있기 때문에 시스템 부하를 억제할 수 있습니다.

큰 시스템은 더 작은 규모의 시스템들로 구성되어 있기 때문에 구성 요소의 리액티브 특성에 의존합니다. 즉, 리액티브 시스템은 설계 원칙을 적용하고, 이 특성을 모든 규모에 적용하여, 그 구성 요소를 합성 할 수 있게 하는 것을 의미합니다. 세계에서 가장 거대한 시스템은 이러한 특성에 기반을 둔 아키텍처에 의존하여 매일 수십억명의 요구를 처리합니다. 이러한 설계 원칙을 매번 재발견하는 것을 그만두고 처음부터 의식하여 적용할 때 입니다.

[선언문에 서명](http://www.reactivemanifesto.org/#sign-button)