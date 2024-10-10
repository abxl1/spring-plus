### # SPRING PLUS - 주특기 플러스주차 개인과제

### # 프로젝트 개요
* 실전 프로젝트 이전 마지막 개인 프로젝트 진행 주차에서 그간 배웠던 기술 스택과 문법, 개념들을 복습하기 위함
* 필수 기능 구현 섹션에서는 JPA, JWT, QueryDSL, Spring Security를 적용한 코드와 이 구현에서 발생하는 N+1 문제, 성능 저하 등을 해결하도록 함
* 도전 기능 구현 섹션에서는 필수 구현 기능에서 확장하여 심화된 QueryDSL, AWS 대용량 데이터 처리 등의 기술을 구현함

### # API 명세 

- 회원 관리

| 기능 | method | URL | request header | request | response |
|-----|--------|-----|----------------|--------|--------|
| 회원가입 | POST | /auth/signup | - | requestBody | Bearer Token |
| 로그인 | POST | /auth/signin | - | requestBody | Bearer Token |
| 회원 조회 | GET | /users/{userId} | Authentication Token | PathVariable | UserResponse |
| 비밀번호 변경 | PUT | /users | Authentication Token | requestBody | HTTP CODE |
</br>

- 일정 관리

| 기능 | method | URL | request header | request | response |
|-----|--------|-----|----------------|--------|--------|
| 일정 생성 | POST | /todos | Authentication Token | requestBody | TodoSaveResponse |
| 일정 단건 조회 | GET | /todos/{todoId} | Authentication Token | PathVariable | TodoResponse |
| 일정 다건 조회 | GET | /todos | Authentication Token | requestParam | TodoResponse |
| 일정 다건 조회 - QueryDSL | GET | /todos/query | Authentication Token | requestBody | TodoProjectionsDto |
</br>

- 댓글 관리

| 기능 | method | URL | request header | request | response |
|-----|--------|-----|----------------|--------|--------|
| 댓글 생성 | POST | /todos/{todoId}/comments | Authentication Token | PathVariable, RequestBody | CommentSaveResponse |
| 댓글 조회 | GET | /todos/{todoId}/comments | Authentication Token | PathVariable | CommentResponse |
</br>

- 담당자 관리

| 기능 | method | URL | request header | request | response |
|-----|--------|-----|----------------|--------|--------|
| 담당자 생성 | POST | /todos/{todoId}/managers | Authentication Token | PathVariable, RequestBody | ManagerSaveResponse |
| 담당자 조회 | GET | /todos/{todoId}/managers | Authentication Token | PathVariable | ManagerResponse |
| 담당자 삭제 | DELETE | /todos/{todoId}/managers/{managerId} | Authentication Token | PathVariable | HTTP CODE |
</br>

### # 트러블 슈팅

* 3번 문제
QueryDSL 적용 시에 build > ... > domain > entity 패키지 내의 엔티티 클래스들의 Q클래스가 생성이 되지 않는 문제가 발생함 </br>
