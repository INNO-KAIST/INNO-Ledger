# INNO Ledger — 작업 이력

> 광학 측정 계획·이력 장부. lot × 측정종류 × 여기·검출 구성 매트릭스, Run 티켓 발급 → 파일 연결 → Prism 결과 → 판정, 마운트·보정 세션 관리.
>
> 이 파일 하나에 이 앱의 작업 이력·교훈·문서 색인을 모았다. 자세한 근거는 색인의 문서(claude.ai 프로젝트 ‘유원정’)에 있다.

## 최근 작업
- **10-02 폴더 정리**.
- **09-29 구조 재설계 ③**: 셀 상세를 오른쪽 서랍으로, Run 단계 표시(발급→파일→Prism→판정)·다음 할 일, **발급 뒤 보정·마운트 사후 연결**(유효성은 발급 시각 기준, `calibLinkedLate`/`mountLinkedLate` 기록, 자동판정 재계산), 탭 순서(매트릭스·계획 템플릿·보정·검토 | 프리셋·설정).
- **09-29 휴대폰**: 프리셋·보정 표가 화면보다 넓어 배율이 깨지던 문제 → 표만 가로 스크롤. 표 머리 대문자 변환 제거("λ (nm)"→"(NM)" 단위 오류).
- **09-29 결함 A2·A7**: 유효 보정 중 최신을 기본 선택(‘연결 안 함’ 기본값 때문에 보정 없음 Run 이 발급되던 문제), 보정 λ 빈칸·0 거부.
- **09-28 디자인 파일럿**(INNO 공통 틀의 첫 적용 앱).
- **09-03 측정 매트릭스 설계 확정**.

## 교훈 · 트러블슈팅
- 기본값이 ‘연결 안 함’이면 게이트가 초록이어도 데이터가 빠진 채 기록된다 → 기본값을 유효한 최신값으로.
- 사후 연결은 ‘지금’이 아니라 측정 시각 기준으로 유효성을 판정하고, 사후라는 사실을 기록에 남긴다.
- 휴대폰 회귀 검사는 모든 탭에서(예전 harness 는 2탭만 봐서 놓쳤다).

## 정리 기록 (2026-10-02)
- 삭제: `_backup_design_0929/`(디자인 개편 전 HTML).
- 이동·통합: (없음 — docs/ 신설만)
- 신설: `_drive_backup/`(RESTORE.md · 백업 만들기.bat · make_backup.py), `docs/HISTORY.md`(이 파일).

## INNO 공통 (6개 앱 함께)
- **배포**: GitHub 조직 `INNO-KAIST`, 앱마다 저장소 `INNO-<앱>` → GitHub Pages `https://inno-kaist.github.io/INNO-<앱>/`.
  배포 도구는 `INNO Deploy/inno_deploy.py` 하나로 5개 앱(Prism·NanoLab·Ledger·Analytics·Scheduler)을 올린다.
  `python inno_deploy.py status` (로컬↔원격 비교) / `python inno_deploy.py push <앱>`. 매핑은 `INNO Deploy/manifest.json`. (10-03 `INNO Prism/.deploy/` → `Develop/INNO Deploy/`로 이동)
  RefAtlas 만 예외: 자체 저장소 `INNO-KAIST/INNO-RefAtlas` + Cloudflare Pages, push 는 사용자가 `RefAtlas.bat` 으로.
- **2026-09-22 GitHub 조직 이관**(개인 → INNO-KAIST), 공용 계정 2FA. (문서: GitHub조직이관-*, 계정구조개편-*)
- **2026-09-29 디자인 개편 → 구조 재설계**: 공통 색 토큰(앱별 강조색), 앱 아이콘 시리즈, 공통 UX 층
  (`inno-ux.js/css`: 대화창 Esc·포커스·입력 보호, 키보드 조작, 앱 전환 메뉴, 휴대폰 하단 탭),
  한글 줄바꿈(`word-break:keep-all` + `text-wrap-style`), 결함 7건(A1–A7) 수정, 앱별 구조 재설계.
  상세: `INNO-suite-디자인개편-*`, `INNO-suite-구조재설계-STEP1-사용성감사-*`, `INNO-suite-구조재설계-STEP2-결정·진행-0929`.
- **공통 교훈**
  - `text-wrap` 단축 속성은 상속된 `nowrap` 을 풀어 버린다 → 항상 `text-wrap-style` 로.
  - 연결 폴더로 파일을 덮어쓸 때 첫 쓰기가 반영되지 않은 일이 두 번 있었다 → **배포 전 기기 파일에 새 표식이 있는지 확인**하고, 배포 도구가 "변경 없음"이면 의심할 것.
  - 단일 HTML 앱은 HTML 자체가 원본이다. 수정은 정확한 문자열 치환 + 개수 검사로 하고, 같은 재현 시나리오로 전·후를 확인한다.
- **2026-10-02 폴더 정리**: 앱마다 같은 틀(아래 README의 폴더 지도)로 재구성, 백업 잔재 삭제, Drive 보관용 `_drive_backup/` 신설.

## 문서 색인 (이 앱 관련, 최신 → 과거)
| 날짜 | 문서 제목 (claude.ai 프로젝트 ‘유원정’ → `claude/<제목>.md`) |
|---|---|
| 09-03 | nanolab-INNO-Ledger-측정매트릭스-설계확정-0903 |

### INNO 공통 문서
| 날짜 | 문서 제목 (claude.ai 프로젝트 ‘유원정’ → `claude/<제목>.md`) |
|---|---|
| 09-29 | INNO-suite-구조재설계-STEP2-결정·진행-0929 |
| 09-29 | INNO-suite-구조재설계-STEP1-사용성감사-6개앱-0929 |
| 09-29 | INNO-suite-디자인개편-공통틀·앱별강조색-파일럿Ledger-0929 |
| 09-27 | GitHub자동배포-inno_deploy-5개플랫폼·토큰·사용법-0927 |
| 09-22 | GitHub조직이관-이관후실측·수정적용·잔여조치-0922 |
| 09-22 | 계정구조개편-공용계정2FA·GitHub조직·공유드라이브-진행상황-0922 |
| 09-22 | GitHub조직이관-INNO-KAIST-파괴지점·실행순서·검증-0922 |
