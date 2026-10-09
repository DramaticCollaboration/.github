## 🚀 PR 개요 (Summary)
<!-- 본 PR의 목적과 변경 내용을 간략히 기술해 주세요. -->

- **연관 이슈**: 
- **작업 유형**: `feat` / `fix` / `refactor` / `test` / `chore` / `docs`

---

## 🛠️ 주요 변경 사항 (Key Changes)
<!-- 주요 변경 내역과 설계 의도를 작성해 주세요. -->
- 

---

## ✅ 전사 표준 및 Zero-Mock 검증 체크리스트 (Quality Checklist)
<!-- 아래 항목들을 확인하고 체크해 주세요 ([x]). -->

### 백엔드 (Java / Spring Boot)
- [ ] **Lombok 표준 준수**: `@Getter`, `@Setter`, `@Builder`, `@RequiredArgsConstructor` 적용 및 수동 보일러플레이트 배제
- [ ] **단일 Canonical URL 준수**: 모든 Controller에 `/api/v1/{product}/...` 단일 엔드포인트 매핑 완료 (배열 다중 매핑 금지)
- [ ] **Zero-Mock & Zero-Hardcoding**: 더미/가짜 데이터 없이 PostgreSQL 17 pgvector 실 연동 및 원자적 롤백 지원
- [ ] **SQL 무결성**: DB 스크립트 내 `ON CONFLICT` 임시 방편 배제 및 순수 단일 `INSERT INTO` 준수

### 프론트엔드 (Vue 3 / TypeScript / Vben Admin)
- [ ] **동적 라우팅 모드**: `permissionMode: PermissionModeEnum.BACK` 유지 (정적 라우트 하드코딩 금지)
- [ ] **Vben 표준 컴포넌트 우선**: `BasicTable`, `BasicForm`, `BasicModal` 등 프레임워크 표준 고수준 컴포넌트 사용
- [ ] **투명 프록시 원칙**: `/api/v1/...` 경로 변형 없이 백엔드로 1:1 패스스루

---

## 🧪 테스트 결과 (Test Results)
<!-- 단위 테스트, Zero-Mock 하네스 테스트, 통합 테스트 실행 결과 -->
- [ ] `mvn clean test-compile` 또는 `build.ps1` 검증 통과
- [ ] Zero-Mock 하네스 검증 통과 (`verify-zero-mock.ps1`)
