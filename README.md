## Hi there 👋

<!--
**Janet159/Janet159** is a ✨ _special_ ✨ repository because its `README.md` (this file) appears on your GitHub profile.

Here are some ideas to get you started:

- 🔭 I’m currently working on ...
- 🌱 I’m currently learning ...
- 👯 I’m looking to collaborate on ...
- 🤔 I’m looking for help with ...
- 💬 Ask me about ...
- 📫 How to reach me: ...
- 😄 Pronouns: ...
- ⚡ Fun fact: ...
-->
<!-- 기존 헤더 부분 그대로 유지 -->

![header](https://capsule-render.vercel.app/api?&type=waving&color=timeAuto&height=180&section=header&text=DoHyeon's%20Hub&fontSize=50&animation=fadeIn&fontAlignY=45)

<br>
<div align='center'>💻 깊고 넓게 공부하는 개발자 박도현(●'◡'●)입니다.</div>
<br>
<div align='center'> ✉ Email : <a href="mailto:qkrehgus2312@naver.com">qkrehgus2312@naver.com</a></div>
<div align='center'> 🔗 Notion : <a href="https://www.notion.so/25e09bf8c3c480e5b274e3a800193c3a?source=copy_link">노션 포트폴리오</a></div>
<br>
<br>
<br>

![Anurag's GitHub stats](https://github-readme-stats.vercel.app/api?username=issohbog&show_icons=true&theme=radical)  
![Top Langs](https://github-readme-stats.vercel.app/api/top-langs/?username=issohbog&layout=compact)

---

## 📌 Projects

### 🖥 MagicPOS — MVC 버전 (SpringBoot MVC + Thymeleaf)

- **Overview**: 좌석 예약, 요금제/상품 관리, 회원 관리, 결제/로그 분석까지 처리하는 소상공인 시간제 매장 통합 관리 시스템  

- **Stack**  
  <img src="https://img.shields.io/badge/Spring_Boot-6DB33F.svg?style=flat-square&logo=Spring%20Boot&logoColor=white"/>&nbsp;
  <img src="https://img.shields.io/badge/Thymeleaf-005F0F.svg?style=flat-square&logo=Thymeleaf&logoColor=white"/>&nbsp;
  <img src="https://img.shields.io/badge/MyBatis-000000.svg?style=flat-square&logoColor=white"/>&nbsp;
  <img src="https://img.shields.io/badge/MySQL-4479A1.svg?style=flat-square&logo=MySQL&logoColor=white"/>&nbsp;
  <img src="https://img.shields.io/badge/Spring%20Security-6DB33F.svg?style=flat-square&logo=Spring%20Security&logoColor=white"/>&nbsp;


- **My Role**  

  #### 🏪 매장 관리
  - **좌석 예약 및 종료**: 로그인 시 `user_tickets`에서 남은 시간을 조회 후 좌석 예약, 로그아웃 시 사용 시간만큼 FIFO 방식으로 차감  
  - **좌석 상태 관리**:  
    - 사용 중 좌석 → 남은 시간이 60분 이상이면 **녹색**, 60분 이하이면 **빨간색** 표시  
    - 고장 좌석은 **노란색**, 로그아웃 시에는 **휴지통 아이콘** 표시 → 관리자가 클릭 시 이용 가능 좌석으로 변경  
  - **실시간 반영**: WebSocket을 이용해 좌석 상태 변화를 알림 및 대시보드에 즉시 반영  

  #### 🎫 요금제 구매 (관리자/사용자)
  - **관리자 구매**:  
    - 관리자 화면에서 회원 검색 → 해당 회원에게 현금/카드 결제 기반 요금제 구매 가능  
    - JS 이벤트로 키 입력 감지 후 실시간 회원 검색 리스트 제공  
  - **TossPayments 결제 연동**:  
    - 신용카드 결제 시 TossPayments 모듈 호출  
    - 결제 성공 후 `user_tickets` 테이블에 구매 내역 저장 (관리자/사용자 공통) 

  #### 🧑🏻 회원 관리
  - **CRUD**: 회원 등록·수정·삭제(일괄 삭제), 조회 기능 구현  
  - **ID 중복 체크**: 등록 시 Ajax 비동기 통신으로 실시간 중복 확인  
  - **비밀번호 초기화**: 회원 정보 화면에서 비밀번호 초기화 → 암호화 후 UPDATE  
  - **페이지네이션**: 대량 데이터에서도 빠른 조회 가능하도록 구현  

  #### 📦 상품 관리
  - **상품 분류/상품 CRUD**: 관리자가 상품과 상품 분류를 등록·수정·삭제 가능  
  - **파일 업로드**: 상품 이미지 업로드 및 수정 기능 구현  
  - **페이지네이션**: 대량 상품 목록 관리 최적화  

  #### 👤 회원 가입
  - **유효성 검사**: 입력 값에 대해 실시간 검사 및 경고 문구 표시 → 올바른 데이터만 저장  

👉 [프로젝트 Repo](https://github.com/issohbog/PowerManager)

---

### 🖥 MagicPOS — Client/Server 분리 버전 (SpringBoot RestAPI + React) 

- **Overview**: MVC 버전 프로젝트를 React + Spring Boot REST 구조로 리팩토링, 무상태 인증(JWT), 좌석/요금제/상품 관리 기능을 개선하고 WebSocket 기반 실시간 좌석 상태 반영 및 사용자 UX를 대폭 향상  

- **Stack**  
  <img src="https://img.shields.io/badge/React-61DAFB.svg?style=flat-square&logo=React&logoColor=black"/>&nbsp;
  <img src="https://img.shields.io/badge/Spring_Boot-6DB33F.svg?style=flat-square&logo=Spring%20Boot&logoColor=white"/>&nbsp;
  <img src="https://img.shields.io/badge/REST%20API-000000.svg?style=flat-square&logoColor=white"/>&nbsp;
  <img src="https://img.shields.io/badge/MyBatis-000000.svg?style=flat-square&logoColor=white"/>&nbsp;
  <img src="https://img.shields.io/badge/MySQL-4479A1.svg?style=flat-square&logo=MySQL&logoColor=white"/>&nbsp;
  <img src="https://img.shields.io/badge/JWT-000000.svg?style=flat-square&logo=JSON%20Web%20Tokens&logoColor=white"/>&nbsp;
  <img src="https://img.shields.io/badge/WebSocket-4285F4.svg?style=flat-square&logoColor=white"/>&nbsp;
  <img src="https://img.shields.io/badge/Tailwind_CSS-06B6D4.svg?style=flat-square&logo=tailwindcss&logoColor=white"/>&nbsp;

- **My Role**

  #### 🪑 좌석 관리 (그룹화/드래그앤드롭)
  - 기존 34석 고정 좌석 구조 → **좌석 추가/삭제 및 상태 변경 가능**하도록 개선  
  - **좌석 그룹화 기능** 추가 → 분단 단위로 좌석 관리 가능  
  - **Drag & Drop UI (Tailwind CSS)** 적용 → 좌석 위치 및 그룹 배치 직관적 수정 가능  

  #### 🏪 매장 관리
  - 로그인 시 `user_tickets` 잔여 시간을 기반으로 좌석 예약, 로그아웃 시 사용한 시간만큼 FIFO 차감 로직 구현  
  - 좌석 상태 시각화: 잔여 시간 ≥ 60분 → **초록색**, ≤ 60분 → **빨간색**, 고장 좌석 → **노란색**, 로그아웃 시 휴지통 표시  
  - **WebSocket 실시간 알림**: 좌석 예약/종료 이벤트 발생 시 서버 → 클라이언트 구독 토픽으로 전달 → 클라이언트는 새로고침 없이 좌석 상태와 Toast 알림 확인 가능  

  #### 🧑🏻 회원 관리
  - **CRUD 기능**: 회원 등록·수정·삭제(일괄 삭제), 조회  
  - **Ajax ID 중복 체크**, **비밀번호 초기화**(암호화 후 업데이트) 구현  
  - **페이지네이션 컴포넌트화**: MVC 대비 더 단순하고 재사용성 높은 구조로 React 컴포넌트 설계  

  #### 📦 상품 관리
  - **상품/상품 분류 CRUD**: 관리자 UI에서 등록·수정·삭제 가능  
  - **파일 업로드 구현**: 상품 이미지 업로드/수정 지원  
  - **페이지네이션 컴포넌트화**로 관리 효율성 향상  

  #### 🎫 요금제 구매 (관리자) 
  - 관리자 화면에서 회원 검색 → 현금/카드로 요금제 구매 가능  
  - **사용자 편의성 향상**: 키 입력 시 실시간 검색, 방향키/엔터키 지원으로 검색/선택 UX 최적화  
  - **TossPayments 결제 연동**: 카드 결제 후 결제 결과를 받아 `user_tickets` 테이블에 저장  

  #### 🎫 요금제 구매 (사용자)
  - 사용자 UI에서 TossPayments 모듈 연동 → 결제 성공 시 DB 적재  

  #### 👤 회원 가입
  - 실시간 유효성 검사 → 잘못된 값 입력 시 경고 메시지 표시  

👉 [프로젝트 Repo](https://github.com/issohbog/PowerManager_ReactREST)

---

### 🛒 NeoBel (화장품 쇼핑몰, JSP/Servlet) — 미니 프로젝트

- **Stack**  
  <img src="https://img.shields.io/badge/JSP-FFA000.svg?style=flat-square&logoColor=white"/>&nbsp;
  <img src="https://img.shields.io/badge/Servlet-6DB33F.svg?style=flat-square&logo=java&logoColor=white"/>&nbsp;
  <img src="https://img.shields.io/badge/MyBatis-000000.svg?style=flat-square&logoColor=white"/>&nbsp;
  <img src="https://img.shields.io/badge/MySQL-4479A1.svg?style=flat-square&logo=MySQL&logoColor=white"/>&nbsp;

- **Overview**: Abib 웹사이트를 모티브로 한 JSP/Servlet 기반 쇼핑몰 프로젝트.  
  상품 조회 → 장바구니 → 주문/주문 내역까지 전자상거래 기본 흐름을 직접 구현하며  
  MVC 아키텍처와 DAO 계층의 동작 원리를 익힌 프로젝트입니다.  

- **My Role**  
  - `alcl-jdbc` DAO 자동 CRUD 기반으로 **재사용 가능한 DAO/Service 구조** 확장  
  - 장바구니 담기·수량 변경·삭제, 주문 시 **장바구니 초기화 로직** 구현  
  - `orders` ↔ `order_details` 간 1:N 관계 설계 및 결제 프로세스 반영  

- **Learned**  
  - **CRUD 중심 웹 개발 흐름**을 체감하며 전체 MVC 구조를 반복 학습  
  - DAO → Service → Controller 계층을 거치며 **데이터 흐름 추적 및 디버깅 능력** 향상  
  - 기초적인 전자상거래 기능을 통해 **실무형 로직에 대한 자신감**을 쌓음  

👉 [프로젝트 Repo](https://github.com/issohbog/TeamProject_Neobel) 


---

### ✈️ 에어두드림 (공항 종합 정보 서비스) — 정규 프로젝트

- **Stack**  
  <img src="https://img.shields.io/badge/Java-007396.svg?style=flat-square&logo=OpenJDK&logoColor=white"/>&nbsp;
  <img src="https://img.shields.io/badge/Spring_Framework-6DB33F.svg?style=flat-square&logo=Spring&logoColor=white"/>&nbsp;
  <img src="https://img.shields.io/badge/전자정부표준프레임워크-0054A6.svg?style=flat-square&logoColor=white"/>&nbsp;
  <img src="https://img.shields.io/badge/JSP-FFA000.svg?style=flat-square&logoColor=white"/>&nbsp;
  <img src="https://img.shields.io/badge/MySQL-4479A1.svg?style=flat-square&logo=MySQL&logoColor=white"/>&nbsp;
  <img src="https://img.shields.io/badge/Tomcat-F8DC75.svg?style=flat-square&logo=Apache%20Tomcat&logoColor=black"/>&nbsp;

- **Overview**  
  국내외 여행객 증가에 따라 **공항 이용객의 편의성 향상**을 목표로 개발한 공항 종합 정보 서비스입니다.  
  항공기 실시간 운항 정보, 공항 버스 정보, 주변 지하철 노선도, 숙박 정보까지 제공하며,  
  **공공데이터 OPEN API**를 적극 활용해 실시간 정보를 제공합니다.  

- **My Role**  

- **OPEN API 파싱 및 정제**: 공공데이터포털 API를 활용하여 버스 노선 데이터 수집 및 정제  
- **무한 스크롤(Infinite Scroll)**: `IntersectionObserver`를 사용해 스크롤 위치 감지 → 추가 데이터 자동 요청  
- **서버 페이지네이션**: `count(pageno)` 기반 서버 처리 + `loading` 플래그로 중복 요청 방지  
- **UX 최적화**:  
  - 1페이지는 검색 버튼으로 로딩, 2페이지 이후는 자동 로딩  
  - 첫 페이지는 `innerHTML` 교체, 이후 페이지는 `insertAdjacentHTML('beforeend')`로 증분 추가  
  - 마지막 페이지/빈 결과 분기 처리 → 불필요한 네트워크 호출 차단 및 사용자 안내 제공
    
👉 [프로젝트 Repo](https://github.com/ezenteamb2/teamb2)

---

<h3 align="center">📚 Tech Stack 📚</h3>
<div align="center">

  <!-- Languages -->
  <img src="https://img.shields.io/badge/Java-007396.svg?style=flat-square&logo=OpenJDK&logoColor=white"/>&nbsp;
  <img src="https://img.shields.io/badge/JavaScript-F7DF1E.svg?style=flat-square&logo=JavaScript&logoColor=black"/>&nbsp;
  <img src="https://img.shields.io/badge/Python-3776AB.svg?style=flat-square&logo=Python&logoColor=white"/>&nbsp;
  <img src="https://img.shields.io/badge/C-A8B9CC.svg?style=flat-square&logo=C&logoColor=white"/>&nbsp;
  <img src="https://img.shields.io/badge/C++-00599C.svg?style=flat-square&logo=C%2B%2B&logoColor=white"/>&nbsp;
  <br/>

  <!-- Backend & Frameworks -->
  <img src="https://img.shields.io/badge/Spring_Framework-6DB33F.svg?style=flat-square&logo=Spring&logoColor=white"/>&nbsp;
  <img src="https://img.shields.io/badge/Spring_Boot-6DB33F.svg?style=flat-square&logo=Spring%20Boot&logoColor=white"/>&nbsp;
  <img src="https://img.shields.io/badge/MyBatis-000000.svg?style=flat-square&logoColor=white"/>&nbsp;
  <img src="https://img.shields.io/badge/Apache%20Tomcat-F8DC75?style=flat-square&logo=Apache%20Tomcat&logoColor=black"/>&nbsp;
  <br/>

  <!-- Database & Tools -->
  <img src="https://img.shields.io/badge/MySQL-4479A1.svg?style=flat-square&logo=MySQL&logoColor=white"/>&nbsp;
  <img src="https://img.shields.io/badge/DBMS-003B57.svg?style=flat-square&logoColor=white"/>&nbsp;
  <img src="https://img.shields.io/badge/Git-F05032.svg?style=flat-square&logo=Git&logoColor=white"/>&nbsp;
  <img src="https://img.shields.io/badge/GitHub-181717.svg?style=flat-square&logo=GitHub&logoColor=white"/>&nbsp;
  <img src="https://img.shields.io/badge/VSCode-007ACC.svg?style=flat-square&logo=Visual%20Studio%20Code&logoColor=white"/>&nbsp;
  <img src="https://img.shields.io/badge/Eclipse-2C2255.svg?style=flat-square&logo=Eclipse%20IDE&logoColor=white"/>&nbsp;
  <img src="https://img.shields.io/badge/Django-092E20.svg?style=flat-square&logo=django&logoColor=white"/>&nbsp;
  <img src="https://img.shields.io/badge/Flutter-02569B.svg?style=flat-square&logo=flutter&logoColor=white"/>&nbsp;
  <br/>

  <!-- Frontend -->
  <img src="https://img.shields.io/badge/HTML5-E34F26.svg?style=flat-square&logo=HTML5&logoColor=white"/>&nbsp;
  <img src="https://img.shields.io/badge/CSS3-1572B6.svg?style=flat-square&logo=CSS3&logoColor=white"/>&nbsp;
  <img src="https://img.shields.io/badge/Tailwind_CSS-06B6D4.svg?style=flat-square&logo=tailwindcss&logoColor=white"/>&nbsp;
  <img src="https://img.shields.io/badge/Bootstrap-7952B3.svg?style=flat-square&logo=Bootstrap&logoColor=white"/>&nbsp;
  <img src="https://img.shields.io/badge/React-61DAFB.svg?style=flat-square&logo=React&logoColor=black"/>&nbsp;
  <img src="https://img.shields.io/badge/jQuery-0769AD.svg?style=flat-square&logo=jQuery&logoColor=white"/>&nbsp;
  <img src="https://img.shields.io/badge/JSP-FFA000.svg?style=flat-square&logoColor=white"/>&nbsp;
  <img src="https://img.shields.io/badge/Ajax-4285F4.svg?style=flat-square&logoColor=white"/>&nbsp;

</div>

![footer](https://capsule-render.vercel.app/api?type=waving&color=auto&height=100&section=footer)
