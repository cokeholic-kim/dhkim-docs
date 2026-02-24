# As-Is API Spec (cocktailLibrary / cocktail-app-api)

## 공통
- 응답 래퍼: `Api<T>`
- 인증: JWT 쿠키(`Authorization`) 또는 헤더 기반

---

## 1) 인증/회원

### POST `/join`
- 회원가입
- Request(JSON)
```json
{
  "email": "user@example.com",
  "password": "Abcd1234!",
  "name": "닉네임"
}
```

### POST `/login`
- 로그인 성공 시 JWT 쿠키 발급
- Request: JSON/form (`username`, `password`)

### OAuth2
- `/oauth2/authorization/naver`
- `/oauth2/authorization/google`
- `/oauth2/authorization/kakao`

---

## 2) Cocktail 공개 API

### GET `/cocktail/getAll`
- 전체 칵테일 목록 조회

### GET `/cocktail/getDetail/{name}`
- 칵테일 상세 조회

### GET `/cocktail/glass`
- 잔 종류 목록 조회

### GET `/cocktail/method`
- 제조 방식 목록 조회

---

## 3) Ingredient 공개 API

### GET `/ingredient/getAll`
- 전체 재료 목록 조회

### GET `/ingredient/getDetail/{ingredientName}`
- 재료 상세 조회

### POST `/ingredient/getFitCocktailList`
- 보유 재료 기반 칵테일 추천
- Request(JSON)
```json
{
  "myIngredient": ["Gin", "Lime Juice", "Sugar Syrup"]
}
```

---

## 4) Banner API

### GET `/banner/getAllBanner`
- 배너 전체 조회

---

## 5) Comment API

### POST `/comment/save`
- 댓글 저장 (USER 권한 필요)
- 필드: `content`, `parentCommentId`, `refCategory`, `refCategoryItem`

### GET `/comment/get/{category}/{item}`
- 댓글 목록 조회

### DELETE `/comment/delete`
- 댓글 삭제 (USER 권한 필요)
- Request(JSON)
```json
{
  "commentId": 123
}
```

---

## 6) USER 전용 API (`/user/**`)

### POST `/user/saveCocktail`
- 사용자 칵테일 등록
- multipart/form-data (이미지 + 재료/메타)

### POST `/user/ingredientRegister`
- 사용자 재료 등록
- multipart/form-data

---

## 참고
- 실제 코드 기준 정리: `cocktailLibrary/cocktail-app-api`
- 보안 정책상 `/user/**`는 `ROLE_USER` 필요
