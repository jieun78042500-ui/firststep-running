# 첫걸음 러닝

한국의 초보 러너가 날씨를 확인하고 운동을 기록하며, 훈련법·식단·마라톤 대회를 살펴볼 수 있는 반응형 다페이지 서비스입니다.

## 설치 및 실행

```bash
pnpm install
pnpm dev
```

품질 확인은 `pnpm lint`, 배포용 빌드는 `pnpm build`를 사용합니다.

## 페이지 구조

- `/` 서비스 소개 랜딩페이지
- `/training`, `/nutrition`, `/races`, `/races/[id]`, `/about` 공개 콘텐츠
- `/dashboard`, `/workout`, `/records`, `/goals`, `/profile` 개인 관리
- `/login`, `/signup` 데모 인증

## 폴더 구조

- `app/`: App Router 페이지와 메타데이터
- `components/`: 헤더, 푸터, 카드, 기록·대시보드 기능
- `data/`: 운동, 식단, 대회, 훈련 샘플 데이터
- `lib/`: localStorage 저장소와 날씨 서비스 인터페이스
- `types.ts`: 도메인 타입

## 샘플 데이터 수정

`data/exercises.ts`, `data/meals.ts`, `data/races.ts`, `data/workouts.ts`의 배열을 수정하세요. 대회 정보는 반드시 예시 또는 공식 검증 여부를 표시하세요.

## 날씨 API 연결

`lib/weather.ts`의 `WeatherService` 인터페이스를 구현해 `mockWeatherService` 대신 기상청 단기예보 또는 OpenWeather 어댑터를 주입합니다. API 키는 환경 변수로 관리하세요.

## 로그인과 데이터베이스 연결

현재 인증·운동 기록·목표·관심 대회는 `components/app-provider.tsx`와 `lib/storage.ts`를 통해 브라우저에 저장됩니다. Supabase 등을 연결할 때 같은 도메인 타입을 유지한 채 인증 공급자와 저장소 함수만 서버 API 구현으로 교체하면 됩니다.
