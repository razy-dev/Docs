# Software

##
* Service

> 서비스라는 용어는 소프트웨어 기능 또는 일련의 소프트웨어 기능 (예 : 지정된 정보 검색 또는 일련의 작업 실행)을 목적으로 사용합니다. 
> 다른 클라이언트는 용도를 제어해야하는 정책 (예 : 서비스를 요청하는 클라이언트의 ID를 기반으로 함)과 함께 다른 용도로 재사용 할 수 있습니다.

> OASIS는 서비스를 "규정 된 인터페이스를 사용하여 제공되는 하나 이상의 기능에 액세스 할 수있는 메커니즘으로 정의하고 서비스 설명에 지정된 제약 조건 및 정책에 따라 수행됩니다.

> 서비스는 좀 덜 구체적이지만, "엔터프라이즈 애플리케이션 아키텍처 패턴"의 서비스 계층 패턴을 기반으로 구현하는 것이 좋습니다. 기본적으로 컨트롤러가 더 특정 플랫폼 (예 : HTTP를 통한 전송 및 하이퍼 텍스트 렌더링, 일반적으로 웹 기반 컨트롤러 용 HTML) 인 서비스는 누가이를 사용하고 어떻게 사용 하는지를 알 필요가 없습니다. 당신은 방금 예를 들어 차례로 사용할 수있는 균일 한 인터페이스를 제공하고 있습니다. 웹 컨트롤러.
https://stackoverflow.com/questions/8403535/when-do-i-call-my-class-controller-manager-or-service

* Controller
> 제어

> controller 라는 것은 현재 운용되고 있는 시스템이나 자원의 상태를 제어가 목적일 때 사용이 됩니다.

> 일반적으로 '컨트롤러'는 사용자 인터페이스 구성 요소와 모델 (예 : 구매) 간의 인터페이스입니다. 컨트롤러는 얇은 클래스 여야하며, 사용자 인터페이스 이벤트를 모델 함수에 매핑하는 것 이상의 효과가 있습니다.
https://softwareengineering.stackexchange.com/questions/82262/difference-between-handler-manager-and-controller

> 컨트롤러는 Model-View-Controller 디자인 패턴을 기반으로하므로이 디자인 패턴을 기반으로 컨트롤러 기능을 구현하는 클래스에 명시 적으로 사용해야합니다. 예 : Spring MVC를 사용하고 컨트롤러 클래스 중 하나에서 확장하는 경우.
https://stackoverflow.com/questions/8403535/when-do-i-call-my-class-controller-manager-or-service


* Manager
> 관리

> manager는 시스템과 자원 등의 생성 반환 운용 등의 모든 것을 관리한다는 포괄적인 의미가 있습니다.
대표적인 것이 운영체제인데 OS는 컴퓨터 자원을 관리하는 Manager이다. 라 할 수 있습니다.
자원의 관리(생성,반환,운용,처리)

> '관리자'는 코드 냄새입니다. 구매는 자체적으로 관리해야하거나 공급 업체 또는 구매자와 같은 소유 클래스에서 관리 할 수 있습니다.
https://softwareengineering.stackexchange.com/questions/82262/difference-between-handler-manager-and-controller

> 관리자는 잘 관리합니다. 연결, 응용 프로그램 컨텍스트, 세션; 일반적으로 응용 프로그램의 모든 구성 요소가 대화 할 수있는 중앙 위치입니다.
https://stackoverflow.com/questions/8403535/when-do-i-call-my-class-controller-manager-or-service

* Executor

* Broker

* Worker

* Labor

* Resolver

* handler
> 처리

> Handler는 할당 받은 자원을 운용 또는 처리가 목적일 때 사용이 됩니다.

> 'Handler'는 일반적으로 객체에 래핑 된 단일 함수입니다. 이러한 기능은 일류 기능없이 레거시 언어로 프로그래밍 할 때 필요합니다.
https://softwareengineering.stackexchange.com/questions/82262/difference-between-handler-manager-and-controller

---
> The action executor merely waits for the next action in the schedule to be ready for execution. At this point it sends a signal to the worker nodes to begin their work. ... work in [16], but is discussed here to assist understanding of the broker.