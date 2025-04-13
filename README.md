🧑‍💻 User (사용자) API
기능	Method	Endpoint	설명	Request Body	Query Params	PathVariable	Response 예시	HTTP Status
회원 가입	POST	/users	사용자 회원 가입	{ "user": "김철수", "email": "test@example.com", "password": "1234" }	X	X	{ "msg": "회원가입이 되었습니다" }	201 CREATED
프로필 조회	GET	/users/{userId}	특정 사용자 프로필 조회	X	X	userId: Long	{ "user": "김철수" }	200 OK
비밀번호 수정	PATCH	/users	자신의 비밀번호 수정	{ "password": "12345" }	X	userId: Long	{ "msg": "비밀번호가 수정되었습니다" }	200 OK
회원 탈퇴	PATCH	/users	자신의 계정 탈퇴 (논리 삭제 등)	{ "password": "1234" }	X	userId: Long	{ "msg": "회원을 삭제했습니다" }	200 OK
🔐 Login (로그인) API
기능	Method	Endpoint	설명	Request Body	Query Params	PathVariable	Response 예시	HTTP Status
로그인	POST	/login	사용자 로그인 요청	{ "email": "test@example.com", "password": "1234" }	X	X	{ "msg": "로그인 성공했습니다" }	200 OK
📝 Post (게시물) API
기능	Method	Endpoint	설명	Request Body	Query Params	PathVariable	Response 예시	HTTP Status
게시물 작성	POST	/posts	새로운 게시물 작성	{ "title": "제목", "postContent": "내용" }	X	X	PostResponseDto	201 CREATED
게시물 목록 조회	GET	/posts	게시물 목록 조회 (페이지네이션)	X	offset, limit	X	List<PostResponseDto>	200 OK
게시물 개별 조회	GET	/posts/{postId}	게시물 상세 조회	X	X	postId: Long	PostResponseDto	200 OK
게시물 수정	PATCH	/posts/{postId}	본인 게시물 수정	{ "title": "수정된 제목", "postContent": "수정된 내용" }	X	postId: Long	PostResponseDto	200 OK
게시물 삭제	DELETE	/posts/{postId}	본인 게시물 삭제	X	X	postId: Long	{ "msg": "게시물이 삭제되었습니다" }	200 OK
👥 Friend (친구) API
기능	Method	Endpoint	설명	Request Body	Query Params	PathVariable	Response 예시	HTTP Status
친구 요청	POST	/friends	친구 요청 전송	{ "toUserId": "2", "fromUserId": "1" }	X	X	{ "msg": "친구 요청을 보냈습니다." }	201 CREATED
친구 요청 수락	POST	/friends/{friendId}	친구 요청 수락	{ "response": "confirm" }	X	friendId: Long	{ "msg": "친구 요청을 수락했습니다" }	200 OK
친구 삭제	DELETE	/friends/{friendId}	친구 삭제	X	X	friendId: Long	{ "msg": "친구 목록을 삭제했습니다" }	200 OK
친구 목록 조회	GET	/friends/{userId}	친구 목록 조회	X	X	userId: Long	{ "friendId": 3, "fromUserId": 1, "toUserId": 2, "status": "CONFIRM", "createdAt": "2025-04-09T10:00:00" }	200 OK
💬 Comment (댓글) API
기능	Method	Endpoint	설명	Request Body	Query Params	PathVariable	Response 예시	HTTP Status
댓글 작성	POST	/comments	게시물에 댓글 작성	{ "content": "댓글 내용" }	X	X	{ "userName": "작성자", "commentContent": "댓글 내용" }	201 CREATED
댓글 조회	GET	/comments/{commentId}	특정 댓글 조회	X	X	commentId: Long	{ "userName": "작성자", "commentContent": "내용" }	200 OK
댓글 수정	PUT	/comments/{commentId}	댓글 수정	{ "content": "수정된 내용" }	X	commentId: Long	{ "userName": "작성자", "commentContent": "수정된 내용" }	200 OK
댓글 삭제	DELETE	/comments/{commentId}	댓글 삭제	X	X	commentId: Long	{ "msg": "댓글이 삭제되었습니다." }	200 OK
