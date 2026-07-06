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
AGENTS.md       # 이 문서
CLAUDE.md       # Claude Code용 진입점 (이 문서를 import)
```

JS 프레임워크, 빌드 도구, npm 도입 금지. 단일 HTML 파일 구조를 유지하세요.

## 4. 페이지 구조 (index.html)

| 순서 | 섹션 | id | 내용 |
|---|---|---|---|
| 0 | 상단 고정 내비 | `.topbar` | 앵커 링크 (수상·프로젝트·역량·글·연락처) |
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

### 컬러 토큰 (CSS 변수, `:root`에 정의됨)

| 토큰 | 값 | 용도 |
|---|---|---|
| `--paper` | `#FAFAF8` | 배경 (웜 오프화이트) |
| `--ink` | `#1B231F` | 본문 텍스트 |
| `--ink-soft` | `#59655D` | 보조 텍스트 |
| `--ink-faint` | `#8B958E` | 캡션·eyebrow |
| `--signal` | `#0E7B4A` | 액센트 (링크, LIVE 배지) — BBARU 보행 신호에서 유래 |
| `--award` | `#9A6A00` | **수상 카드 전용** — 다른 곳에 쓰지 말 것 |
| `--line` / `--line-strong` | `#E4E6E0` / `#C9CDC5` | 헤어라인 |

### 타이포그래피

- 본문: 한글 시스템 산세리프 스택 (`--sans`), 웹폰트 없음 (외부 요청 최소화)
- 디스플레이: 같은 패밀리 800~900 웨이트 + 타이트한 자간 (-0.02 ~ -0.045em)
- 날짜·점수·태그·eyebrow: 모노스페이스 (`--mono`) + `tabular-nums`

### 디자인 원칙 (위반 금지)

- 카드 대신 **헤어라인으로 구분한 문서형 레이아웃**. 그림자·그라데이션 금지.
- 액센트는 시그널 그린 하나. 앰버는 수상 카드에서만.
- 애니메이션은 최소 (LIVE 도트 펄스, 히어로 인트로뿐). 추가 시
  `prefers-reduced-motion: reduce` 대응 필수.
- 이모지를 섹션 마커로 쓰지 않음.
- 인쇄 스타일(`@media print`)이 있음 — 마크업 변경 시 인쇄 결과도 확인.

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

## 9. 백로그 (미착수 아이디어)

- [ ] 프로젝트 스크린샷을 아이폰 프레임 목업으로 교체
- [ ] 방문 분석 (GoatCounter 등 무료·경량 도구)
- [ ] 전용 OG 이미지 제작 (현재는 award.jpg 재사용)
- [ ] GitHub 프로필 README(whtjddlr/whtjddlr)에 포트폴리오 링크 추가
- [ ] 프로젝트별 상세 페이지 또는 케이스 스터디 (지금은 단일 페이지)
- [ ] 영문 버전

## 10. 하지 말 것

- 프레임워크·빌드 도구 도입 (단일 HTML 유지)
- 소유자 확인 없이 사진·연락처·수치 변경
- 프로젝트 순서 임의 변경 (2절의 전략 참조)
- 외부 CDN 폰트·스크립트 추가 (현재 외부 의존성 0)
- `--award` 앰버 색을 수상 카드 밖에서 사용
