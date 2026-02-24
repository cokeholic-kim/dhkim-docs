# Migration Plan (Java -> FastAPI, Front -> Next.js)

## 목표
- 프론트엔드: Next.js 기반으로 재구축
- 백엔드: Java(Spring) -> Python(FastAPI) 전환
- 도메인 단위로 기능 분리 및 명확한 API 계약 수립

## 권장 아키텍처

### Frontend (Next.js)
- App Router + TypeScript
- API 클라이언트 계층 분리
- 기능 기준(`features/*`) 모듈화

### Backend (FastAPI)
- FastAPI + Pydantic + SQLAlchemy/SQLModel + Alembic
- `/api/v1` 버전 관리
- 표준 에러 스키마/응답 포맷 통일

## 도메인 분리(초안)
- Auth
- Cocktail Catalog
- Ingredient
- Comment
- Favorites
- Banner

## 단계별 진행
1. As-Is API/DB 인벤토리 확정
2. To-Be API(OpenAPI) 설계
3. FastAPI MVP(Auth + Cocktail 조회)
4. Next.js 화면 이식(조회/상세/검색)
5. 병행 검증 후 점진 전환

## 리스크
- 레거시 비즈니스 룰 누락
- 인증 흐름 차이
- 검색/필터 성능 저하

## 대응
- 계약 테스트(API Contract)
- 샘플 데이터 회귀 테스트
- 단계적 트래픽 전환
