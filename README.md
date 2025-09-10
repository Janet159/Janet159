![header](https://capsule-render.vercel.app/api?type=waving&color=gradient&customColorList=9&height=200&width=1000&section=header&text=YE%20JI%27S%20HUB&fontSize=60&fontColor=ffffff&animation=twinkling&fontAlignY=40&desc=Creative%20Developer%20Journey&descAlignY=60&descAlign=50)


<br>
<div align="center">
  🚀 <span style="color:#FF6F61"><b>학습 속도</b></span>와  
  <span style="color:#6A5ACD"><b>실행력</b></span>을 무기로 성장하는 개발자,<br/>
  <b>장예지</b>입니다!
</div>


<br>
<div align='center'> ✉ Email : <a href="mailto:janet15916@naver.com">janet15916@naver.com</a></div>
<div align='center'> 🔗 Notion : <a href="https://www.notion.so/2656bc55e4d58006a413d4bd8aa49c44?source=copy_link">노션 포트폴리오</a></div>
<br>
<br>
<br>

---

## 📌 Projects

### 🖥 MagicPOS — MVC 버전 (SpringBoot MVC + Thymeleaf)

- **Overview**: 로그인/인증, 상품 구매·결제, 주문/매출 집계, 로그 기록 기능을 구현하여 매장 운영의 핵심 업무를 통합 관리

- **Stack**  
  <img src="https://img.shields.io/badge/Spring_Boot-6DB33F.svg?style=flat-square&logo=Spring%20Boot&logoColor=white"/>&nbsp;
  <img src="https://img.shields.io/badge/Thymeleaf-005F0F.svg?style=flat-square&logo=Thymeleaf&logoColor=white"/>&nbsp;
  <img src="https://img.shields.io/badge/MyBatis-000000.svg?style=flat-square&logoColor=white"/>&nbsp;
  <img src="https://img.shields.io/badge/MySQL-4479A1.svg?style=flat-square&logo=MySQL&logoColor=white"/>&nbsp;
  <img src="https://img.shields.io/badge/Spring%20Security-6DB33F.svg?style=flat-square&logo=Spring%20Security&logoColor=white"/>&nbsp;


- **My Role**

  #### 🔑 로그인 / 인증
  - **회원 로그인**: `users` 테이블과 연동, Spring Security 기반 인증·인가 처리  
  - **접근 권한 제어**: 관리자/사용자 권한에 따라 접근 가능한 메뉴 분리  
  - **Session 관리**: 로그인 상태 유지 및 로그아웃 시 세션 만료 처리  
  - **로그 기록 연동**: 로그인/로그아웃 성공 시 `logs` 테이블에 자동 기록 (Spring AOP 기반) → 관리자 페이지에서 조회 가능  

  #### 🛒 상품 구매 (관리자 / 사용자)
  - **결제 방식 선택**: 현금 / 카드 / QR(TossPayments) 중 선택하여 결제 가능  
  - **주문 처리 흐름**:  
    - 상품 선택 → 수량 입력 → 결제 버튼 클릭 → `OrderController` POST 요청  
    - 카드/QR 결제 시 TossPayments API 호출 → 성공 콜백에서 `orders`, `order_details`, `user_tickets` 테이블 저장  
    - 현금 결제 시 서버에서 즉시 내역 반영  
  - **추가 요청 전달**: 주문 시 요청 메시지를 함께 입력 → 관리자 페이지에서 확인 가능  
  - **유효성 검사 / 트랜잭션 처리**: 수량·금액 검증 및 주문-결제-재고 차감 일괄 처리  
  - **로그 저장**: 결제 성공 시 `orders`, `order_details`, `logs` 테이블에 내역 기록 (관리자/사용자 공통)  
  
  #### 🏠 사용자 메인 화면
  - **상품 조회**: `products` + `categories` 테이블 조인 결과를 Thymeleaf 템플릿으로 렌더링  
  - **회원 정보 표시**: 로그인한 회원의 `users` 테이블 정보 조회 (닉네임, 권한, 이용권 상태 등)  
  - **좌석·시간 관리**:  
    - `seats_reservations` × `user_tickets` 데이터 조인으로 사용 중 좌석 및 남은 시간 계산  
    - 경과 시간은 서버에서 불러온 값을 JavaScript 타이머로 실시간 업데이트  
  - **구매 내역 조회**:  
    - `orders` × `order_details` 조인 결과를 사용자 페이지에서 확인 가능  
    - 결제 방식, 결제 금액, 이용권/상품 내역을 필터링하여 조회 가능  


  #### 📊 주문 현황 관리
  - **주문 리스트 조회**: `orders` + `order_details` 조인 후 JSP/Thymeleaf 표로 출력  
  - **주문 상태 변경**: 수량 변경, 부분 취소, 전체 취소 기능 제공  
  - **재고 반영**: 취소·변경 시 `products.stock` 자동 증감 처리  
  - **화면 반영**: AJAX 기반 비동기 통신으로 변경 즉시 관리자/사용자 화면 갱신  
  - **동시성 제어**: 여러 관리자가 동시에 주문을 수정할 때 데이터 충돌 방지  
  - **페이지네이션**: 대량 주문 데이터도 빠르게 조회할 수 있도록 서버 단 페이징 처리  

  #### 📅 당일 내역 조회
  - **일일 집계**: SQL 집계 함수(`SUM`, `COUNT`, `GROUP BY`)로 당일 발생한 주문·이용권 내역 합산  
  - **데이터 매핑**: MyBatis `resultMap`으로 집계 결과 매핑  
  - **대시보드 출력**: 결제 수단별 매출, 판매량 순위, 총 매출액을 관리자 페이지에서 확인 가능  
  - **조건별 조회**: 결제 방식 / 특정 시간대 등 필터링 가능  
  - **성능 최적화**: 인덱스 적용 및 집계 쿼리 최적화로 대량 데이터도 빠른 조회  

  #### 💺 사용 중 회원 조회
  - **조인 조회**: `seats_reservations` × `users` × `user_tickets` 데이터 조인  
  - **남은 시간 계산**: 로그인 시 잔여 이용권 시간을 불러와 사용 중 좌석에 매핑  
  - **관리자 조회**: 현재 좌석 사용자와 남은 시간을 관리자 페이지에서 확인 가능  
  - **실시간 반영**: AJAX 호출로 좌석/회원 상태 변경 즉시 반영  
  - **경고 표시**: 잔여 시간이 10분 이하일 경우 빨간색/아이콘으로 시각적 강조  

  #### 📝 로그 관리
  - **주요 이벤트 기록**: 로그인/로그아웃, 주문/결제, 매출 내역 등을 AOP 기반으로 자동 기록  
  - **DB 저장**: `logs` 테이블(행위자, 작업, 대상, 시간, 상세정보) 구조로 관리  
  - **로그 카테고리화**: 로그인/주문/결제/관리자 작업 등 유형별 구분 저장  
  - **검색 최적화**: 기간 + 키워드 조건 검색으로 특정 회원/주문 로그 빠르게 추적 가능  
  - **관리자 조회**: 기간/유형별 필터링과 페이징을 통한 로그 조회 지원  
 


👉 [프로젝트 Repo](https://github.com/issohbog/PowerManager)

---

### 🖥 MagicPOS — Client/Server 분리 버전 (SpringBoot RestAPI + React) 

- **Overview**: 로그인/인증, 상품 구매·주문 관리, 매출 분석 및 시각화, 실시간 메시지 송수신, 로그 관리(TTS 알림 포함) 기능을 구현하여 매장 운영의 핵심 흐름을 담당


- **Stack**  
  <img src="https://img.shields.io/badge/React-61DAFB.svg?style=flat-square&logo=React&logoColor=black"/>&nbsp;
  <img src="https://img.shields.io/badge/Spring_Boot-6DB33F.svg?style=flat-square&logo=Spring%20Boot&logoColor=white"/>&nbsp;
  <img src="https://img.shields.io/badge/REST%20API-000000.svg?style=flat-square&logoColor=white"/>&nbsp;
  <img src="https://img.shields.io/badge/MyBatis-000000.svg?style=flat-square&logoColor=white"/>&nbsp;
  <img src="https://img.shields.io/badge/MySQL-4479A1.svg?style=flat-square&logo=MySQL&logoColor=white"/>&nbsp;
  <img src="https://img.shields.io/badge/JWT-000000.svg?style=flat-square&logo=JSON%20Web%20Tokens&logoColor=white"/>&nbsp;
  <img src="https://img.shields.io/badge/WebSocket-4285F4.svg?style=flat-square&logoColor=white"/>&nbsp;
  <img src="https://img.shields.io/badge/Tailwind_CSS-06B6D4.svg?style=flat-square&logo=tailwindcss&logoColor=white"/>&nbsp;

- **My Role (React + Spring Boot REST API)**

- **My Role (React + Spring Boot REST API)**

  #### 🔐 로그인 / 인증
  - **회원 로그인**: `users` 테이블 연동, Spring Security + JWT 기반 인증·인가 처리  
  - **Axios Interceptor**: 모든 API 요청 시 JWT 자동 첨부, 401 응답 시 재로그인 유도  
  - **권한 제어**: 사용자/관리자 권한(Role)에 따라 접근 가능한 메뉴 및 라우트 분리  
  - **좌석 선택 검증**: 로그인 시 `seats` 테이블에서 사용 중 좌석 조회 → 사용 중이지 않은 좌석만 선택 가능  
  - **유효성 검사**: 사용 중 좌석을 선택하면 로그인 불가 처리 (서버·클라이언트 양쪽에서 검사)  

  #### 🛒 상품 구매 (관리자 / 사용자)
  - **상품 조회**: `products` 테이블에서 메뉴판 정보 조회 후 React 컴포넌트로 렌더링  
  - **결제 방식 선택**: 현금 / 카드 / QR(TossPayments API) 중 선택 가능  
  - **주문 처리 흐름**:  
    - 사용자: 상품 선택 → 수량 입력 → 결제 요청 → TossPayments SDK 승인 → `orders`, `order_details`, `user_tickets` 테이블 반영  
    - 관리자: 검색 기능을 통해 회원 조회 후 판매 처리 가능  
  - **로그 저장**: 결제 성공 시 주문 내역과 함께 `logs` 테이블에 기록  

  #### 🏠 사용자 메인 화면
  - **메뉴판 조회**: `/api/products` 호출, 상품/카테고리 데이터를 React 컴포넌트로 렌더링  
  - **회원 정보 표시**: `/api/users/me` 호출 → `users` 테이블 기반 닉네임, 권한, 이용권 상태 출력  
  - **좌석·시간 관리**:  
    - `/api/seats/{seatId}/usage` 호출 → `seats_reservations` × `user_tickets` 조인 결과 반환  
    - React 타이머 컴포넌트로 잔여 시간·경과 시간 실시간 표시  
  - **구매 내역 조회**: `/api/orders/user` 호출 → 본인의 `orders` × `order_details` 데이터 출력  
    - 결제 방식, 상품명, 결제 금액, 결제 일시를 React 테이블로 표시  


  #### 📊 주문 현황 관리
  - **주문 리스트 조회**: `/api/orders/active` API 호출, React 테이블로 출력  
  - **주문 상태 변경**: 수량 변경 / 부분 취소 / 전체 취소 기능 지원  
  - **재고 동기화**: 주문 취소·변경 시 `products.stock` 자동 증감 반영  
  - **비동기 처리**: Fetch/Axios를 이용해 변경 즉시 반영, 토스트 알림 제공  

  #### 📅 운영 매출 분석 & 당일 내역
  - **일일/주간/월간 매출 집계**: SQL 집계 함수(`SUM`, `COUNT`, `GROUP BY`)로 서버 집계 후 `/api/stats` 제공  
  - **시각화**: Chart.js 기반 시계열 그래프, 막대 차트로 매출/기간 비교 표시  
  - **필터링**: 기간별(일/주/월) 및 결제 수단별 매출 분석 기능 제공  
  - **당일 내역 조회**: `orders` + `user_tickets` 기준 하루 발생 내역 확인, 서버사이드 페이지네이션 지원  

  #### 💺 사용 중 회원 조회
  - **조인 조회**: `seats_reservations` × `users` × `user_tickets` 데이터 조인 후 API 응답  
  - **남은 시간 표시**: React 타이머 컴포넌트로 잔여 시간 카운트다운 표시  
  - **관리자 조회**: 현재 좌석 사용자와 남은 시간 실시간 확인 가능  

  #### 💬 실시간 메시지 송수신
  - **WebSocket (STOMP)**: 사용자 ↔ 관리자 간 실시간 메시지 교환  
  - **채널 구독 구조**: 좌석 ID 단위로 채널을 구독/발행하여 메시지 분리 관리  
  - **매크로 기능**: 관리자 측에서 자주 쓰는 응답 메시지를 매크로로 등록/삭제, DB와 연동  

  #### 📝 로그 관리 & 알림
  - **로그 적재**: Spring AOP로 회원 활동, 주문, 매출 내역 등을 자동 기록 → `logs` 테이블 저장  
  - **로그 조회**: REST API + 관리자 페이지에서 기간·유형별 조회 및 페이지네이션 지원  
  - **음성 알림 (TTS)**: 새로운 로그가 발생하면 TTS(Text-to-Speech) API로 관리자에게 음성 알림 제공  


 

👉 [프로젝트 Repo](https://github.com/issohbog/PowerManager_ReactREST)

---

### 🏢 Sprint StudyCafe (스터디카페 통합 관리 시스템, JSP/Servlet)

- **Stack**  
  <img src="https://img.shields.io/badge/Java-007396.svg?style=flat-square&logo=java&logoColor=white"/>&nbsp;
  <img src="https://img.shields.io/badge/JSP-FFA000.svg?style=flat-square&logoColor=white"/>&nbsp;
  <img src="https://img.shields.io/badge/Servlet-6DB33F.svg?style=flat-square&logo=java&logoColor=white"/>&nbsp;
  <img src="https://img.shields.io/badge/MyBatis-000000.svg?style=flat-square&logoColor=white"/>&nbsp;
  <img src="https://img.shields.io/badge/MySQL-4479A1.svg?style=flat-square&logo=MySQL&logoColor=white"/>&nbsp;

- **Overview**:  
  스터디카페 좌석 예약, 회원 관리, 편의시설 관리 등 운영 전반을 통합 관리할 수 있는  
  JSP/Servlet 기반 웹 프로젝트입니다.  
  로그인/회원가입, 마이페이지, 관리자 편의시설 관리, DB 설계 및 구현을 맡으며  
  MVC 패턴과 JDBC/SQL 기반 CRUD 흐름을 학습한 프로젝트입니다.  


- **My Role (Sprint StudyCafe – Spring MVC + JSP/Servlet)**

  #### 🔐 회원 관리
  - **로그인 / 회원가입**: Session 기반 인증·인가, JSP/Servlet + JDBC/SQL로 구현  
  - **마이페이지**: 관리자/사용자 페이지 분리, 회원 정보 조회 및 수정 / 관리자 회원 목록 조회 기능 제공  

  #### 🏠 화면 구현
  - **메인 페이지**: 헤더·푸터 구현 및 동적 이벤트 처리 (hover, 드롭다운 메뉴)  
  - **회사 소개 / 방문 위치 페이지**: HTML·CSS·JSP 기반 화면 구현  

  #### 🏪 편의시설 관리 (관리자)
  - **CRUD 기능**: 편의시설 등록·수정·삭제·조회 기능 구현 (JSP/Servlet + JDBC CRUD)  
  - **데이터 처리**: SQL 쿼리를 이용해 DB와 연동  

  #### 🗄 DB 설계
  - **ERD 설계**: 전체 테이블 구조 및 관계 정의  
  - **DDL/DML 작성**: MySQL 기반 DDL 스크립트와 초기 데이터 작성  
  - **데이터베이스 구축**: 회원, 편의시설, 예약 등 주요 테이블 설계 및 최적화  


- **Learned**  
  - **DB 설계부터 구현까지 전 과정**을 직접 경험하며 테이블 정의·관계 설정 능력 강화  
  - 회원 관리/편의시설 관리 기능을 구현하며 **JSP·Servlet·JDBC를 활용한 CRUD 로직 이해** 심화  
  - 메인 페이지와 서브 페이지 UI를 직접 구현하면서 **HTML/CSS/JavaScript 기반 동적 화면 구성 역량** 향상  
  - 프로젝트 발표 자료(PPT)를 준비하며 **팀 내 기여 내용과 개발 흐름을 체계적으로 정리·표현하는 능력** 습득


👉 [프로젝트 Repo](https://github.com/Janet159/sprint_studycafe.git) 


---

### 🌱 Smart Garden Embedded System (스마트팜 임베디드) — 개인 프로젝트

- **Stack**  
  <img src="https://img.shields.io/badge/C-00599C.svg?style=flat-square&logo=C&logoColor=white"/>&nbsp;
  <img src="https://img.shields.io/badge/Arduino-00979D.svg?style=flat-square&logo=Arduino&logoColor=white"/>&nbsp;
  <img src="https://img.shields.io/badge/LCD-3366CC.svg?style=flat-square&logoColor=white"/>&nbsp;
  <img src="https://img.shields.io/badge/Sensor-FF6F00.svg?style=flat-square&logoColor=white"/>&nbsp;

- **Overview**  
  토양 습도, 온도, 조도 등 환경 데이터를 센서로 수집하고, 자동 급수·조명·환기 기능을 통해  
  **식물 생육 환경을 자동 제어**하는 임베디드 기반 스마트팜 프로젝트입니다.  
  LCD 디스플레이와 경고 시스템으로 사용자에게 실시간 상태를 전달하며,  
  **센서-액추에이터 제어 로직**을 직접 구현해 임베디드 시스템 개발 경험을 쌓았습니다.  


- **My Role (Smart Garden Embedded System)**

  #### 💧 자동 급수 기능
  - 토양 습도 센서 값을 주기적으로 측정하여 기준치 이하일 경우 워터 펌프를 동작
  - 토양 건조 상태에 맞춘 자동 급수 로직 구현으로 식물 관리 자동화  

  #### 🌡 환경 모니터링
  - 토양 습도, 온도, 습도, 조도(밝기) 데이터를 실시간으로 측정
  - LCD 화면에 측정값을 표시하여 사용자가 현재 상태를 직관적으로 확인 가능  

  #### 💡 자동 조명 제어
  - 주변 조도를 감지하여 일정 기준 이하일 경우 LED 조명을 자동 점등
  - 광합성을 위한 빛 공급을 자동화해 식물 생장 환경 개선  

  #### 🚨 경고 시스템
  - 센서 값이 임계치 이상/이하로 벗어날 경우 부저 및 경고등 동작
  - 사용자에게 이상 상황을 즉각적으로 알림  

  #### 🌬 공기/바람 공급
  - 팬을 활용하여 바람을 공급, 이산화탄소 순환 및 씨앗 수정 지원
  - 식물 환경의 공기 흐름을 개선해 생육 효율성 향상  

  #### 🖥 소통 기능
  - LCD 디스플레이를 통해 식물 상태 메시지 출력
  - 센서 데이터와 간단한 알림/멘트를 사용자에게 전달  

- **Learned**  
  - 다양한 센서를 연동하며 **하드웨어 제어와 데이터 수집** 과정을 직접 경험  
  - 자동 급수·조명·바람 공급 로직을 구현하며 **조건문·제어문 기반 실시간 처리 능력** 습득  
  - LCD, 부저, LED 등 출력 장치를 활용하면서 **센서-출력 간 데이터 흐름 이해** 심화  
  - 경고 시스템과 소통 기능 구현을 통해 **사용자 중심의 임베디드 서비스 설계 경험** 확보  

    
👉 [프로젝트 Repo](https://github.com/Janet159/embedded-smart-garden.git)

---

<h3 align="center">📚 Tech Stack 📚</h3>
<div align="center">

  <!-- Languages -->
  <img src="https://img.shields.io/badge/Java-007396.svg?style=flat-square&logo=OpenJDK&logoColor=white"/>&nbsp;
  <img src="https://img.shields.io/badge/JavaScript-F7DF1E.svg?style=flat-square&logo=JavaScript&logoColor=black"/>&nbsp;
  <img src="https://img.shields.io/badge/Python-3776AB.svg?style=flat-square&logo=Python&logoColor=white"/>&nbsp;
  <img src="https://img.shields.io/badge/C-00599C.svg?style=flat-square&logo=C&logoColor=white"/>&nbsp;
  <br/>

  <!-- Backend & Frameworks -->
  <img src="https://img.shields.io/badge/Spring_Boot-6DB33F.svg?style=flat-square&logo=SpringBoot&logoColor=white"/>&nbsp;
  <img src="https://img.shields.io/badge/Spring_Security-6DB33F.svg?style=flat-square&logo=SpringSecurity&logoColor=white"/>&nbsp;
  <img src="https://img.shields.io/badge/MyBatis-000000.svg?style=flat-square&logoColor=white"/>&nbsp;
  <img src="https://img.shields.io/badge/Django-092E20.svg?style=flat-square&logo=django&logoColor=white"/>&nbsp;
  <img src="https://img.shields.io/badge/Apache_Tomcat-F8DC75.svg?style=flat-square&logo=Apache%20Tomcat&logoColor=black"/>&nbsp;
  <br/>

  <!-- Database & Tools -->
  <img src="https://img.shields.io/badge/MySQL-4479A1.svg?style=flat-square&logo=MySQL&logoColor=white"/>&nbsp;
  <img src="https://img.shields.io/badge/Git-F05032.svg?style=flat-square&logo=Git&logoColor=white"/>&nbsp;
  <img src="https://img.shields.io/badge/GitHub-181717.svg?style=flat-square&logo=GitHub&logoColor=white"/>&nbsp;
  <img src="https://img.shields.io/badge/VSCode-007ACC.svg?style=flat-square&logo=Visual%20Studio%20Code&logoColor=white"/>&nbsp;
  <img src="https://img.shields.io/badge/Eclipse-2C2255.svg?style=flat-square&logo=Eclipse%20IDE&logoColor=white"/>&nbsp;
  <br/>

  <!-- Frontend -->
  <img src="https://img.shields.io/badge/HTML5-E34F26.svg?style=flat-square&logo=HTML5&logoColor=white"/>&nbsp;
  <img src="https://img.shields.io/badge/CSS3-1572B6.svg?style=flat-square&logo=CSS3&logoColor=white"/>&nbsp;
  <img src="https://img.shields.io/badge/JavaScript-F7DF1E.svg?style=flat-square&logo=JavaScript&logoColor=black"/>&nbsp;
  <img src="https://img.shields.io/badge/React-61DAFB.svg?style=flat-square&logo=React&logoColor=black"/>&nbsp;
  <img src="https://img.shields.io/badge/jQuery-0769AD.svg?style=flat-square&logo=jQuery&logoColor=white"/>&nbsp;
  <img src="https://img.shields.io/badge/JSP-FFA000.svg?style=flat-square&logoColor=white"/>&nbsp;
  <img src="https://img.shields.io/badge/AJAX-4285F4.svg?style=flat-square&logoColor=white"/>&nbsp;
</div>


![footer](https://capsule-render.vercel.app/api?type=waving&color=gradient&customColorList=9&height=100&section=footer)

