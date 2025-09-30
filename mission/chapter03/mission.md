# 📑 API 명세서

## 🍔 Drone API

| 기능 | 설명 | 메소드 | API Endpoint | Request Header | Request Body | Query String | Path Variable | Response |
|------|------|--------|--------------|----------------|--------------|--------------|---------------|----------|
| 홈 화면 | 유저 정보 조회 | GET | `/umc/user/{user-id}/info` | `Authorization: Bearer {token}`<br>`Content-Type: application/json` | - | - | `user-id`: 조회할 유저 ID | userId에 해당하는 유저의 지역(region), 완료한 미션 수, 모아놓은 point 반환 |
| 홈 화면 | 지역별 미션 조회 | GET | `/umc/mission` | `Authorization: Bearer {token}`<br>`Content-Type: application/json` | - | `region={user.region}` | - | 해당 지역(region)에 있는 미션 목록(missionId, name, content 등) 반환 |
| 마이 페이지 | 포인트 내역 조회 | GET | `/umc/user/{user-id}/point` | `Authorization: Bearer {token}`<br>`Content-Type: application/json` | - | - | `user-id`: 조회할 유저 ID | userId에 해당하는 유저의 포인트 내역(point)과, 각 포인트가 발생한 미션 완료 정보(미션 ID, 미션 제목 등) 반환 |
| 마이 페이지 리뷰 작성 | 리뷰 작성 | POST | `/umc/shop/{shop-id}/review` | `Authorization: Bearer {token}`<br>`Content-Type: application/json` | ```json { "userId": "지금 로그인한 유저의 id", "rating": 5, "comment": "맛있어요!", "images": [ "https://cdn.myapp.com/images/review/file1.jpg", "https://cdn.myapp.com/images/review/file2.jpg" ] } ``` | - | `shop-id`: 리뷰가 쓰여질 shop | - |
| 미션 목록 조회 | 진행 중인 미션 목록 조회 | GET | `/umc/user/{user-id}/mission` | `Authorization: Bearer {token}`<br>`Content-Type: application/json` | - | `mission.status=ongoing` | `user-id`: 조회할 유저 ID | 진행 중인 미션 목록 반환 |
| 미션 목록 조회 | 진행 완료된 미션 목록 조회 | GET | `/umc/user/{user-id}/mission` | `Authorization: Bearer {token}`<br>`Content-Type: application/json` | - | `mission.status=completion` | `user-id`: 조회할 유저 ID | 완료된 미션 목록 반환 |
| 미션 성공 | 미션 성공 누르기 | POST | `/umc/mission/{mission-id}/complete` | `Authorization: Bearer {token}`<br>`Content-Type: application/json` | ```json { "userId": "지금 로그인한 유저의 id" } ``` | - | `mission-id`: 성공 요청할 미션 | mission에 해당하는 인증번호 반환 |
| 회원 | 회원 가입 하기 | POST | `/umc/auth/users/login` | `Content-Type: application/json` | ```json { "email": "abba210@naver.com", "password": "1234", "name": "배민", "gender": "남", "birth": "2001-02-10", "address": "부천시 상일로72", "preferredFoods": ["한식", "치킨", "일식"] } ``` | - | - | - |
