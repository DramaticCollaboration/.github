# Empasy SyncSeries 기여 가이드 (Contributing Guide)

엠파시 SyncSeries 프로젝트에 오신 것을 환영합니다.  
코드, 문서 보완, 버그 제보, 기능 제안 등 모든 형태의 기여를 환영하며, 아래의 개발 원칙과 절차를 참고해 주시기 바랍니다.

---

## 개발 기본 원칙

1. **실제 데이터 기반 검증 (Zero-Mock)**
   - 가짜 데이터나 임시 응답 대신, 실제 데이터베이스(PostgreSQL 17 pgvector) 및 인프라와의 연동을 기준으로 기능을 검증합니다.
2. **Lombok 및 클린 코드 표준**
   - 백엔드 DTO, Entity, VO에 Lombok 애너테이션(`@Getter`, `@Setter`, `@Builder`, `@RequiredArgsConstructor` 등)을 활용하여 불필요한 보일러플레이트 코드를 줄입니다.
3. **단일 API URL 매핑**
   - 컨트롤러에 다중 URL 매핑(`@RequestMapping({"/url1", "/url2"})`)을 지양하고, `/api/v1/{domain}/...` 형태의 명확한 단일 표준 경로를 사용합니다.
4. **동적 라우팅 및 표준 컴포넌트 우선**
   - 프론트엔드는 소스코드 내 정적 라우트 하드코딩 대신 DB 권한(`sys_permission`) 기반의 동적 라우팅을 유지하며, 테이블과 폼, 모달 등은 공통 프레임워크 컴포넌트를 우선 활용합니다.

---

## Git 브랜치 규칙

- `main`: 상용 배포 브랜치
- `develop`: 통합 개발 브랜치
- `feature/{domain}-{작업명}`: 신규 기능 개발 브랜치 (예: `feature/shop-pricing-guard`)
- `fix/{domain}-{이슈명}`: 버그 수정 브랜치 (예: `fix/auth-token-refresh`)

---

## 기여 절차

1. 저장소를 Fork하거나 최신 `develop` 브랜치에서 작업 브랜치를 생성합니다.
2. 로컬 개발에 필요한 인프라(DB, Redis 등)를 실행합니다:
   ```powershell
   docker compose -f docker-compose-local.yml up -d
   ```
3. 코드를 작성하고 단위 테스트 및 빌드 검증을 진행합니다:
   ```powershell
   ./verify-zero-mock.ps1
   ```
4. 커밋 메시지는 표준 접두사(`feat:`, `fix:`, `refactor:`, `docs:`, `test:`, `chore:`)를 사용합니다.
5. Pull Request를 생성하고 PR 템플릿의 체크리스트를 확인합니다.
