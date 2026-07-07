# 포트폴리오 작업 매뉴얼 (AGENTS.md)

> 이 문서는 AI 에이전트(Claude Code, Codex 등)와 사람 모두를 위한 작업 가이드입니다.
> 이 저장소를 수정하기 전에 반드시 끝까지 읽으세요.

## 1. 이 저장소는

- **조성익(whtjddlr)의 개인 포트폴리오 사이트**입니다.
- 배포 주소: **https://whtjddlr.github.io** (GitHub Pages, `main` 브랜치 자동 배포)
- `main`에 push하면 1~2분 내에 자동 반영됩니다. 별도 빌드 과정 없음.
- 정적 사이트: `index.html` 단일 페이지 + `shots/` 이미지 폴더가 전부입니다.

## 2. 소유자 컨텍스트 — 가장 중요

조성익의 커리어 목표는 **PM / 서비스 기획자**입니다. 포지셔닝은
**"직접 만들 수 있는 기획자"** — 기획서로 끝내지 않고 개발·배포·검증까지 완주하는 사람.

따라서 이 포트폴리오의 모든 콘텐츠는 다음 우선순위를 따릅니다:

1. **문제 정의** — 어떤 사용자 문제에서 출발했는가
2. **제품 결정** — 어떤 원칙과 트레이드오프로 방향을 정했는가
3. **검증 설계** — 어떻게 확인했는가 (품질 게이트, 테스트, 채널 분리 등)
4. 기술 구현 — 위 세 가지를 뒷받침하는 수단으로만 서술

❌ 기술 스택 나열을 앞세우지 마세요. ✅ 기획·의사결정 서사를 앞세우세요.

핵심 정체성 문구 (프로필 README에서 가져옴, 수정 금지):
> "잘하는 사람은 많으니, 저는 꾸준히 끝까지 만들어보려 합니다."

## 3. 파일 구조

```
index.html      # 사이트 전체 (마크업 + CSS 인라인). 이 파일이 유일한 소스.
shots/          # 최적화된 이미지 (JPEG, 웹용 리사이즈 완료)
  profile.jpg   # 증명사진 (원본은 소유자만 보유)
  award.jpg     # SSAFY AI 챌린지 시상식
  bbaru-*.jpg   # 프로젝트 스크린샷 3장
  kok-*.jpg     # 3장
  carch-*.jpg   # 4장
  pm-*.jpg      # PlanMerge 3장
  god-*.jpg     # 갓생 퀘스트 펫 2장
fonts/          # Pretendard Variable 서브셋 woff2 (셀프호스팅 — 재생성법은 6절)
googleeea9e1619cfdbbf5.html  # 구글 서치콘솔 소유 확인 파일 — 삭제 금지
AGENTS.md       # 이 문서
CLAUDE.md       # Claude Code용 진입점 (이 문서를 import)
```

모든 `<img>`에는 원본 픽셀 기준 `width`/`height` 속성이 있어야 합니다 (CLS 방지).
새 이미지를 넣을 때 빠뜨리지 마세요. CSS가 크기를 결정하는 경우 `height: auto`를 함께.

JS 프레임워크, 빌드 도구, npm 도입 금지. 단일 HTML 파일 구조를 유지하세요.

## 4. 페이지 구조 (index.html)

| 순서 | 섹션 | id | 내용 |
|---|---|---|---|
| 0 | 상단 고정 내비 | `.topbar` | 워드마크 "just do it" (Georgia 이탤릭, 홈 링크) + 앵커 링크. 이름 반복을 줄이려 브랜드를 이름 대신 워드마크로 씀 — 이름은 히어로 h1과 푸터에만 |
| 1 | 히어로 | `#top` | 사진 + 이름 + 포지셔닝 선언 + 지표 3개 |
| 2 | 수상 기록 | `#award` | VQA 챌린지 193팀 중 전국 1위 (앰버 카드) |
| 3 | 프로젝트 | `#projects` | 5개, 전략적 순서 (아래 참조) |
| 4 | 역량 | `#skills` | Product·기획이 첫 번째 (그린 강조) |
| 5 | 글 | `#writing` | SSAFYcial 기사·블로그 |
| 6 | 연락처 | `#contact` | 푸터 |

**프로젝트 순서는 의도적입니다 — 임의로 바꾸지 마세요:**
PlanMerge(기획 도구 그 자체) → CARCH(팀·운영 요건) → KOK(문제 정의→흐름 재설계)
→ BBARU(제품 관점+엔지니어링 깊이) → 갓생 퀘스트 펫(프로토타입).
PM 지향이므로 기획 역량이 드러나는 순서입니다.

## 5. 디자인 시스템

### 컬러 토큰 (CSS 변수, `:root`에 정의됨) — 2026.07 네이비 테마

| 토큰 | 값 | 용도 |
|---|---|---|
| `--paper` | `#FAFAF8` | 배경 (웜 오프화이트) |
| `--ink` | `#172033` | 본문 텍스트 (네이비 잉크) |
| `--ink-soft` | `#596171` | 보조 텍스트 |
| `--ink-faint` | `#626B78` | 캡션·라벨 — **paper 대비 5.16:1 (WCAG AA)**. 더 밝게 낮추지 말 것 |
| `--signal` | `#183A66` | 액센트 (링크, LIVE 배지, 밑줄) — 네이비 |
| `--signal-bright` | `#2E6EA6` | 진행바·도트 등 밝은 액센트 |
| `--award` | `#806226` | **수상 카드 전용** 금색 — award-bg 대비 5.05:1 (AA). 다른 곳에 쓰지 말 것 |
| `--award-bg` | `#F7F1E4` | 수상 카드 배경 |
| `--line` / `--line-strong` | `#E2E6EA` / `#C5CDD7` | 헤어라인 |

접근성: `--ink-faint`, `--award`는 WCAG AA(소형 텍스트 4.5:1)를 맞춰둔 값입니다.
색을 바꿀 때는 대비를 재계산하세요 (배경 paper와 award-bg 둘 다).

### 타이포그래피

- **Pretendard Variable 서브셋을 셀프호스팅** (`fonts/`, `@font-face`, weight 45~920,
  `font-display: swap`). Windows 맑은 고딕에는 800~900 웨이트가 없어 디스플레이
  타이포가 무너지기 때문 — 외부 CDN이 아니므로 규칙 위반이 아님. 삭제 금지.
- 서브셋 범위: KS X 1001 한글 2,350자 + 페이지 사용 글자 + Latin (재생성법은 6절).
- 디스플레이: 800~900 웨이트 + 타이트한 자간 (-0.02 ~ -0.045em)
- 날짜·점수·태그·eyebrow: 모노스페이스 (`--mono`) + `tabular-nums`
- 브랜드 워드마크만 Georgia 이탤릭 (라틴 전용이라 시스템 폰트로 충분)

### 디자인 원칙 (위반 금지)

- 카드 대신 **헤어라인으로 구분한 문서형 레이아웃**.
- 액센트는 네이비(`--signal`) 계열 하나. 금색은 수상 카드에서만.
- 모든 모션은 `prefers-reduced-motion: reduce` 대응 필수.
- 이모지를 섹션 마커로 쓰지 않음.
- 인쇄 스타일(`@media print`)이 있음 — 마크업 변경 시 인쇄 결과도 확인.

### 카피 원칙 (2026.07 크리틱 반영 — 위반 금지)

- **주장-증거 정합**: 증거 없는 주장 금지. "사용자 앞에서 검증합니다"는 사용자 지표가
  없어서 "실제 환경에서 돌아가는 것까지 확인합니다"로 하향한 이력이 있음 —
  사용자 수·피드백 등 실증 데이터가 생기기 전까지 되올리지 말 것.
- **'검증' 단어는 아껴 쓴다**: 사용자/시장 검증에만. QA는 "테스트",
  갓생의 그룹원 확인은 "상호 승인"으로 구분해 둠.
- **한 불릿 = 한 아이디어**, 모든 불릿은 "**볼드 리드** — 본문" 문법.
- 기간 표현은 사실 그대로 ("올해 봄 석 달 동안" — 5개 프로젝트는 전부 2026.04~05 시작).
- 수치는 원본 README에 실재하는 것만 (CARCH의 "연회비 월 환산·보유 카드 대비
  추가 이득" 규칙은 carch README 5절에 근거).

### 모션·인터랙션 시스템

`index.html` 하단의 단일 `<script>`가 전부 담당합니다. 의존성 0, 바닐라 JS.

| 구성요소 | 구현 | 비고 |
|---|---|---|
| 히어로 인트로 | CSS 애니메이션 스태거: kicker → 이름(블러 해제) → 역할 → 인용구(따옴표 팝) → 본문 → 링크 → 지표, 사진은 회전 살짝 섞어 등장, "끝까지" 형광펜은 마지막에 스와이프 | 페이지 로드 시 1회 |
| 스크롤 리빌 | IO가 `.rv` 부여 → 교차 시 `.in` | 대상: `.section-head, .award-card, .shots, .footer`. **`.shot` 개별 관찰 금지** — 가로 클리핑된 스샷이 스와이프 전까지 투명해지는 버그 이력 (컨테이너 `.shots`를 관찰하고 자식은 `--d` 스태거) |
| 섹션 줄긋기 | 섹션 구분선이 왼→오로 그려짐 (`html.js .section.in::before` scaleX) | `.section`은 `.rv` 없이 `.in`만 사용. `html.js` 게이트라 no-JS에서는 일반 border로 폴백 |
| 수상 샤인 | `.award-card.in::after` — 금빛 하이라이트가 카드를 한 번 스침 (1.15s, 1회) | 금색이므로 수상 카드 전용 규칙과 부합 |
| 점수 카운트업 | `.score-block`이 보일 때 0→0.97635 (1.3s) | award-card가 아니라 score-block 기준 — 모바일에서 숫자가 보이기 전에 끝나던 버그 수정 |
| 스크롤 진행바 | `.progress` (상단 2px, scaleX) | JS가 body에 동적 생성 |
| 스크롤스파이 | rootMargin 밴드 + **양끝 보정**: 최하단이면 '연락처' 강제 점등, 히어로 복귀 시 active 해제 (`spyEdge`, paint()에서 호출) | 밴드만으로는 짧은 푸터를 영원히 못 켬 |
| 커서 | 수채 잉크 오브(`.cursor-orb`) — 유기적 blob이 마우스를 lerp로 따라오고 링크 위에서 진해짐. **기본 커서를 숨김**(`body.cursor-ready` → `cursor: none`) | `pointer: fine` + 모션 허용 시에만. 하드한 도형 커서(원/링/반전)는 소유자가 거절한 이력 있음 |
| 라이트박스 | `.shot img` 클릭 → 확대 다이얼로그 (배경/×/Esc로 닫기) | 스크린샷 판독성의 핵심 — 제거 금지 |
| 스윕 언더라인 | topbar 링크·`.link-out` 호버 시 밑줄이 왼쪽에서 그려짐, `.active`는 유지 | 새 링크 스타일도 이 언어를 따를 것 |
| 사진 패럴랙스 | 데스크톱 한정 translateY(scrollY×0.08) | 모바일에서는 해제 |
| 호버 마이크로 | 스크린샷 리프트, 히어로 사진 리프트+미세 회전, 태그 틴트 | 전부 `@media (hover: hover)` 안 — 터치 스티키 호버 방지 |

**모션 규칙 (위반 금지):**

- 모든 모션은 `prefers-reduced-motion: reduce`에서 완전히 꺼져야 함
  (CSS는 media query로, JS는 `reduce` 변수 게이트로 이미 처리됨 — 새 모션도 동일하게).
- JS 실패/미로드 시에도 콘텐츠가 전부 보여야 함 (`.rv`는 JS가 부여하므로 no-JS는 자동 안전).
- `@media print`에서 `.rv`·`.shots .shot`을 강제 표시하고 섹션 border를 복원하는
  규칙이 있음 — 삭제하면 인쇄(PDF)가 빈 페이지로 나옴.
- 새 리빌 대상은 기존 IntersectionObserver에 추가 (관찰자 새로 만들지 말 것).
- 스크롤 리스너는 `passive: true` + rAF 스로틀 유지.
- 이동/변형 모션은 0.9s 이하 (예외: 점수 카운트업 1.3s, 수상 샤인 1.15s —
  이동이 아닌 강조 연출이라 허용). 과한 이징·회전·블러 금지. 은은하게.

## 6. 이미지 파이프라인

스크린샷 원본은 각 프로젝트 저장소에 있습니다. 갱신 시:

```bash
# 1. 원본 다운로드 (예시)
curl -sL -o raw.png "https://raw.githubusercontent.com/whtjddlr/<repo>/<branch>/<path>"

# 2. 웹용 변환 (macOS sips 기준)
#    모바일 스크린샷: 폭 340 / CARCH류 태블릿 비율: 440 / 와이드(데스크톱): 680
sips -s format jpeg -s formatOptions 72 --resampleWidth 340 raw.png --out shots/이름.jpg
```

원본 위치:
- BBaru: `docs/screenshots/` (main-search, route-result, en-route)
- KOK: `src/assets/landing/*.webp` (02-map과 03-participants는 동일 파일이니 하나만 사용)
- carch: `docs/screenshots/` (cards, analytics, budget, chat)
- planmerge-ai: `docs/images/`
- godlife-quest-pet: `src/layout-*-friendly.png`
- Recycle_VQA_Challenge: `assets/` (award_ceremony.jpg, leaderboard_*.png) — 기본 브랜치가 **master**

### 폰트 서브셋 재생성 (페이지에 새 한글 글자를 추가했는데 KS X 1001 밖일 때)

서브셋에 없는 글자는 시스템 폰트로 폴백되어 Windows에서 웨이트가 어긋납니다.
KS X 1001 2,350자에 없는 희귀 글자(예: "뷁")를 썼다면 재생성:

```bash
pip3 install --user fonttools brotli
curl -sL -o /tmp/pv.woff2 "https://cdn.jsdelivr.net/gh/orioncactus/pretendard@v1.3.9/packages/pretendard/dist/web/variable/woff2/PretendardVariable.woff2"
python3 - <<'PY'
import re
src = open('index.html', encoding='utf-8').read()
used = {c for c in set(re.sub(r'<[^>]+>', ' ', src)) if c.strip()}
ksx = set()
for code in range(0xAC00, 0xD7A4):
    ch = chr(code)
    try: ch.encode('iso2022_kr'); ksx.add(ch)
    except UnicodeEncodeError: pass
base = set(chr(c) for c in range(0x20, 0x7F)) | set('↗→·—–""''…×°±%')
open('/tmp/chars.txt', 'w', encoding='utf-8').write(''.join(sorted(used | ksx | base)))
PY
python3 -m fontTools.subset /tmp/pv.woff2 --text-file=/tmp/chars.txt \
  --flavor=woff2 --layout-features='*' \
  --output-file=fonts/PretendardVariable-sub.woff2
```

## 7. 데이터 소스 — 소유자의 프로젝트 저장소

| 프로젝트 | 저장소 | 라이브 | 비고 |
|---|---|---|---|
| PlanMerge | whtjddlr/planmerge-ai | planmerge-ai.vercel.app | 단독 |
| CARCH | whtjddlr/carch | carch.vercel.app (+carch-demo.vercel.app/demo) | 2인 팀, 조성익=백엔드·데이터·AI·배포 |
| KOK | whtjddlr/KOK | kok-meet.vercel.app | 단독, 전 범위 |
| BBARU | whtjddlr/BBaru | bbaru.vercel.app | 단독, vitest 59건+Playwright |
| 갓생 퀘스트 펫 | whtjddlr/godlife-quest-pet | godlife-mu.vercel.app | Vanilla JS 프로토타입 |
| Recycle VQA | whtjddlr/Recycle_VQA_Challenge | — | 193팀 중 전국 1위, 팀장. Private 0.97635 / Public 0.96452 (둘 다 1st) |

기타: 블로그 blog.naver.com/solist- (SSAFYcial 기자), 이메일 choim2008@naver.com,
소속 SSAFY 15기 (삼성 청년 SW·AI 아카데미).

**수치를 새로 쓰지 마세요.** 위 저장소의 README가 사실의 원천입니다.
불확실하면 `gh api repos/whtjddlr/<repo>/readme --jq '.content' | base64 -d`로 확인.

## 8. 수정 → 배포 → 검증 절차

```bash
# 1. index.html 직접 수정 (빌드 없음)
# 2. 로컬 확인: 브라우저로 index.html 열기 (open index.html)
# 3. 커밋 & 푸시
git add -A && git commit -m "변경 내용" && git push
# 4. 1~2분 후 검증
curl -s -o /dev/null -w "%{http_code}" https://whtjddlr.github.io/   # 200 확인
```

**빌드가 3분 넘게 안 끝나면** (실제로 종종 발생): 수동 재빌드를 요청하면 바로 풀립니다.

```bash
gh api -X POST repos/whtjddlr/whtjddlr.github.io/pages/builds
gh api repos/whtjddlr/whtjddlr.github.io/pages/builds --jq '.[0].status'  # built 확인
```

### 변경 체크리스트

- [ ] PM 서사 우선순위(문제→결정→검증→구현)를 지켰는가
- [ ] 모바일(≤720px) 레이아웃 확인했는가
- [ ] 새 이미지는 `shots/`에 최적화(JPEG, 수십 KB)해서 넣었는가
- [ ] 새 수치·사실은 원본 저장소 README와 대조했는가
- [ ] 링크가 실제로 열리는지 확인했는가
- [ ] 푸터의 `UPDATED YYYY.MM`을 갱신했는가

### 커밋 규칙

- 커밋 메시지는 한국어로, 무엇을 왜 바꿨는지 한 줄.
- 개인 이메일 노출 방지를 위해 이 저장소의 git identity는
  `조성익 <{github-id}+whtjddlr@users.noreply.github.com>` 사용 (이미 설정돼 있으면 유지).

## 9. 백로그

**콘텐츠 — 2026.07 크리틱(6렌즈 41에이전트)에서 확정된 최우선 과제.
전부 소유자의 실제 경험/데이터가 필요하므로 지어내지 말고 소유자에게 물어볼 것:**

- [ ] **사용자 검증 증거** — 프로젝트당 지인 5~10명이라도 실사용 테스트 → 발견한 문제와
      개선 결과를 수치로 기록 ("N명 테스트 → 이탈 지점 발견 → 흐름 수정" 형식).
      현재 페이지에는 사용자 지표가 0건이라 PM 포지셔닝의 최대 약점.
- [ ] **협업 서사** — CARCH(2인 팀)에서 요구사항 조율·우선순위 합의·의견 충돌 해소
      경험을 불릿 1-2개로. VQA 팀장 서사도 "의견이 갈렸을 때 무엇으로 정리했나" 구체화.
- [ ] **대표작 케이스 스터디** — PlanMerge 하나만 심층으로: 문제 가설 → 버린 대안 →
      트레이드오프 → 검증 → **다시 한다면**. '다시 한다면' 섹션이 메타인지 증명의 핵심.
- [ ] **제품 결정 회고 글 1~2편** — 소재는 이미 페이지 안에 있음
      ("KOK: 최종 결정을 왜 추첨으로 만들었나", "BBARU: 잔여 초를 왜 안 보여주나").
      글 섹션이 현재 개발 입문 콘텐츠뿐이라 PM 신호가 없음.

**폴리시:**

- [ ] 전용 OG 이미지 제작 (현재는 award.jpg 재사용)
- [ ] GitHub 프로필 README(whtjddlr/whtjddlr)에 포트폴리오 링크 추가
- [ ] 방문 분석 (개인정보 최소 수집 도구, 소유자 승인 필요)
- [ ] 영문 버전

## 10. 하지 말 것

- 프레임워크·빌드 도구 도입 (단일 HTML 유지)
- 소유자 확인 없이 사진·연락처·수치 변경
- 프로젝트 순서 임의 변경 (2절의 전략 참조)
- 외부 CDN 폰트·스크립트 추가 (셀프호스팅은 허용 — 현재 런타임 외부 요청 0)
- `--award` 금색을 수상 카드 밖에서 사용
- 증거 없는 주장으로 카피 되돌리기 (5절 카피 원칙 참조)
- `fonts/`·`googleeea9e1619cfdbbf5.html` 삭제
