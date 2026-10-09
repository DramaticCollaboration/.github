# 🤝 Empasy SyncSeries 기여 가이드 (Contributing Guide)

㈜엠파시(Empasy)의 AI 자율 운영 생태계(Living Software)에 오신 것을 환영합니다!  
모든 기여(코드, 문서, 버그 리포트, 아이디어)는 깊은 공감과 자율적 협업(The Dramatic Collaboration)을 바탕으로 진행됩니다.

---

## 📐 개발 및 협업 기본 원칙

1. **Zero-Mock & Zero-Hardcoding**:
   - 가짜/더미 데이터 응답을 지양하며, PostgreSQL 17 pgvector 실제 데이터베이스와의 실 트랜잭션을 원칙으로 합니다.
2. **Lombok 및 클린 코드 표준 준수**:
   - 수동 Getter/Setter, 수동 생성자 작성을 지양하고 `@Getter`, `@Setter`, `@Builder`, `@RequiredArgsConstructor` 등의 Lombok 애너테이션을 필수로 사용합니다.
3. **단일 Canonical URL `/api/v1/` 표준**:
   - 컨트롤러에 다중 URL 매핑(`@RequestMapping({"/url1", "/url2"})`)을 금지하며, 오직 단일 표준 `/api/v1/{domain}/...` 경로로 매핑합니다.
4. **동적 라우팅 및 Vben 컴포넌트 우선**:
   - 프론트엔드는 DB 단일 원천(`sys_permission`)에 의한 동적 라우팅을 유지하며, `BasicTable`, `BasicForm`, `BasicModal` 등 Vben 표준 고수준 컴포넌트를 사용합니다.

---

## 🌿 Git 브랜치 전략

- **`main`**: 상용 릴리즈 브랜치
- **`develop`**: 주 개발 및 통합 브랜치
- **`feature/{domain}-{feature-name}`**: 단위 기능 개발 브랜치 (예: `feature/shop-pricing-guard`)
- **`fix/{domain}-{issue}`**: 버그 수정 브랜치

---

## 🚀 기여 절차

1. 대상 리포지토리를 Fork 또는 최신 `develop` 브랜치에서 새 브랜치를 생성합니다.
2. 로컬 인프라를 실행합니다:
   ```powershell
   docker-compose-local.yml up -d
   ```
3. 코드를 작성하고 단위 테스트 및 Zero-Mock 검증을 실행합니다:
   ```powershell
   ./verify-zero-mock.ps1
   ```
4. 커밋 메시지는 전사 컨벤션(`feat:`, `fix:`, `refactor:`, `docs:`, `test:`, `chore:`)을 준수합니다.
5. PR을 생성하고 PR 템플릿의 체크리스트를 확인합니다.
