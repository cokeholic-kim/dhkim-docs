# To-Be FastAPI Spec Draft

Base URL: `/api/v1`

## Auth
- `POST /auth/login`
- `POST /auth/refresh`
- `POST /auth/logout`
- `POST /auth/join`

## Cocktail
- `GET /cocktails`
- `GET /cocktails/{name}`
- `GET /cocktails/meta/glass`
- `GET /cocktails/meta/method`

## Ingredient
- `GET /ingredients`
- `GET /ingredients/{ingredient_name}`
- `POST /ingredients/fit-cocktails`

## Comment
- `POST /comments`
- `GET /comments/{category}/{item}`
- `DELETE /comments/{comment_id}`

## User
- `POST /users/me/cocktails`
- `POST /users/me/ingredients`

## Banner
- `GET /banners`

---

## 예시 스키마

### FitCocktailRequest
```json
{
  "my_ingredients": ["Gin", "Lime Juice", "Sugar Syrup"]
}
```

### CommentCreateRequest
```json
{
  "content": "좋은 레시피네요",
  "parent_comment_id": null,
  "ref_category": "cocktail",
  "ref_category_item": "Margarita"
}
```
