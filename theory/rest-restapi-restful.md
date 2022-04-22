# REST, REST API, RESTful API?

프론트 엔드 개발을 진행하면서, 백엔드 개발자와 협업을 진행하기 위해서는 REST의 개념에 대해서 알아야 할 필요가 있습니다. 오늘은 REST와 REST API, RESTful API에 대해서 알아보겠습니다.

## 목표
- `REST`의 개념 및 특징을 이해한다
- `REST API`의 개념 및 규칙을 이해한다
- `RESTful`의 개념을 이해한다

![https://blog.kakaocdn.net/dn/ceQC0K/btrzL93TV8q/2mHfnQ6lupjkLjSifNlug0/img.png](https://blog.kakaocdn.net/dn/ceQC0K/btrzL93TV8q/2mHfnQ6lupjkLjSifNlug0/img.png)

## **REST의 정의**

먼저 `REST`는 ‘Representational State Transfer’의 약자로 자원을 이름으로 구분하여 자원의 상태를 주고받는 모든 것을 의미합니다.

## **REST의 개념**

`REST`는 HTTP URI(Uniform Resource Identifier)를 통해 **자원(Resource)을** 명시합니다. **HTTP Method**(GET, POST, PUT, PATCH, DELETE)를 통해 해당 자원에 대한 CRUD 요청을 수행하고, 요청을 위한 자원은 **특정한 형태(Representation of Resource)** 로 표현됩니다.

→ 즉, `REST`는 자원 기반의 구조(ROA, Resource Oriented Architecture) 설계의 중심에 Resource가 있고, HTTP Method를 통해 Resource를 처리하도록 설계된 아키텍처를 의미합니다.

### **URI(Uniform Resource Identifier)란?**

URI는 특정 리소스를 식별하는 **통합 자원 식별자(Uniform Resource Identifier)** 를 의미합니다. 여기서 주목해야 할 부분은 **식별자**라는 부분입니다. 가장 많이 헷갈리는 것이 URL(Uniform Resource Locator)와의 차이인데, 간단하게 설명하면 아래와 같이 설명할 수 있습니다.

- [https://aosjehdgus.tistory.com](https://aosjehdgus.tistory.com/)는 URI 이면서 URL입니다.
- [https://aosjehdgus.tistory.com/141는](https://aosjehdgus.tistory.com/141) URI이지만 URL은 아닙니다.

같은 URL을 공유하고 있지만, **다른 주소임을 식별**할 수 있게 해 줄 수 있는가의 차이로 구분할 수 있습니다.

## **REST 구성 요소**

`REST`의 구성 요소는 다음과 같습니다.

**1. 자원(Resource)**

- 모든 자원에 고유한 HTTP URI가 존재하고, 이 자원은 서버에 존재합니다.
- 클라이언트는 이 URI를 통해서 서버에 정보를 요청합니다.

**2. 행위(Verb)**

- HTTP 프로토콜의 HTTP Method를 사용합니다.
- HTTP 프로토콜의 GET, POST, PUT, PATCH, DELETE의 메소드를 제공합니다.

| Method | Action |  |
| --- | --- | --- |
| GET | Read | 보통 리소스를 조회할 때 사용하며, 서버에 전달하고 싶은 데이터는 query를 통해서 전달합니다. GET을 사용하는 요청은 오직 데이터를 받기만 합니다. |
| POST | Create | 바디를 통해 서버로 데이터를 전달합니다. 주로 신규 리소스를 등록하거나 프로세스 처리에 사용됩니다. |
| PUT | Update | 리소스 전체를 업데이트 합니다. 리소스가 있으면 대체하고 리소스가 없으면 생성합니다. 쉽게 말해 데이터를 덮어쓰게 됩니다. |
| PATCH | Update | PUT과 마찬가지로 리소스를 수정할 때 사용하지만, 리소스 일부를 업데이트 합니다. |
| DELETE | Delete | DELETE 메서드는 특정 리소스를 삭제합니다. |
- HTTP 응답 상태의 코드는 다음과 같습니다.
  - **1xx (정보)**: 요청을 받았으며 프로세스를 계속한다
  - **2xx (성공)**: 요청을 성공적으로 받았으며 인식했고 수용하였다
  - **3xx (리다이렉션)**: 요청 완료를 위해 추가 작업 조치가 필요하다
  - **4xx (클라이언트 오류)**: 요청의 문법이 잘못되었거나 요청을 처리할 수 없다
  - **5xx (서버 오류)**: 서버가 명백히 유효한 요청에 대해 충족을 실패했다

**3. 표현(Representation of Resource)**

- Client와 Server가 데이터를 주고받는 형태로 JSON, XML, TEXT, RSS 등이 있습니다.
- JSON, XML을 통해 데이터를 주고받는 것이 일반적입니다.

## **REST 특징**

`REST`의 특징에 대해서 알아보겠습니다.

**1. Server-Client(서버-클라이언트 구조)**

- REST 클라이언트는 데이터 요청과 요청한 데이터의 핸들링, REST 서버는 요청받은 데이터에 대한 응답을 해줍니다. 각각의 역할이 확실히 구분되기 때문에 클라이언트와 서버에서 개발해야 할 내용이 명확해지고 서로 간 의존성이 줄어들게 됩니다.

**2. Stateless(무상태)**

- HTTP 프로토콜은 Stateless Protocol 이므로 REST 역시 무상태성을 갖습니다.
- 서버는 클라이언트가 만든 최신 HTTP 요청에 대해 아무것도 저장하지 않습니다. 모든 요청을 새것으로 처리합니다.
- 클라이언트는 필요한 정보를 항상 다 담아서 서버에 요청하기 때문에, 꼭 처음에 요청했던 서버가 아니더라도 응답을 받을 수 있는 것을 말합니다.

**3. Cacheable(캐시 처리 가능)**

- 부하를 감소시킬 수 있기 때문에 클라이언트 측의 성능 향상과 서버의 확장성 범위를 향상시킵니다.
- REST에서 캐싱은 적용 가능한 경우 리소스에 적용되어야 하며 이러한 리소스는 캐시 가능하다고 선언해야 합니다.
- 캐싱은 서버 측이나 클라이언트 측에서 구현할 수 있습니다.

**4. Layered System(계층화)**

- REST를 사용하면 예를 들어 서버 A에 API를 배포하고 서버 B에 데이터를 저장하고 서버 C에서 요청을 인증하는 계층화된 시스템 아키텍처를 사용할 수 있습니다.
- 클라이언트는 일반적으로 최종 서버에 직접 연결되어 있는지 아니면 중간에 연결되어 있는지 알 수 없습니다.

**5. Uniform Interface(인터페이스 일관성)**

- URI로 지정한 Resource에 대한 조작을 통일되고 한정적인 인터페이스로 수행합니다.
- HTTP 표준 프로토콜에 따르는 모든 플랫폼에서 사용이 가능합니다.

---

## **REST API의 개념**

![https://blog.kakaocdn.net/dn/cNcyi1/btrzLxD0jsp/gGGQkNUq6rpAC1EBUQAnNK/img.png](https://blog.kakaocdn.net/dn/cNcyi1/btrzLxD0jsp/gGGQkNUq6rpAC1EBUQAnNK/img.png)

### **API(Application Programming Interface)란?**

- API는 응용 프로그램에서 사용할 수 있도록, 운영 체제나 프로그래밍 언어가 제공하는 기능을 제어할 수 있게 만든 인터페이스를 뜻합니다.

### **REST API의 정의**

- REST의 특징을 기반으로 서비스 API를 구현한 것입니다.

### **REST API 설계 규칙**

1. URI는 정보의 자원을 표현해야 합니다.
2. 자원에 대한 행위는 HTTP Method로 표현합니다.
3. URI안에 행위는 포함하지 않습니다.
4. 슬래시(/)는 계층 관계를 나타내는 데 사용합니다.
5. URI 마지막 문자로 슬래시(/)를 포함하지 않습니다.
6. 하이픈(-)은 가독성을 높이는 데 사용합니다.
7. 언더바(_)는 URI에 사용하지 않습니다.
8. URI 경로는 소문자가 적합합니다.
9. 파일 확장자는 URI에 포함하지 않습니다.

여기서 **RESTful API는 이러한 설계 규칙을 잘 지켜서 설계된 API**를 말합니다.

### **이 글을 마치며**

알고 있었지만, 자세히 알지 못했던 REST에 대해서 정리할 수 있는 좋은 시간을 가졌던 것 같습니다. 기본적이고 필수적인 부분이라고 생각합니다. 다시 정리한 것을 머릿속에 새길 수 있도록 노력해야 할 것 같습니다.