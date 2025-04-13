## 🧑‍💻 User (사용자) API

| 기능         | Method | Endpoint       | 설명                          | Request Body | Query Params | PathVariable | Response 예시 | HTTP Status |
|--------------|--------|----------------|-------------------------------|---------------|---------------|---------------|----------------|--------------|
| 회원 가입     | POST   | `/users`       | 사용자 회원 가입               | `{ "user": "김철수", "email": "test@example.com", "password": "1234" }` | X | X | `{ "msg": "회원가입이 되었습니다" }` | `201 CREATED` |
