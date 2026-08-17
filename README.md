# 중1 수학 Ⅳ. 도형의 기초 — 인터랙티브 탐구 웹앱

중학교 1학년 수학 교과서(김화경 외) **Ⅳ단원 「도형의 기초」(136~175쪽)** 의 활동을
노트북·태블릿에서 직접 조작하며 체험할 수 있게 만든 수업용 웹 콘텐츠 모음입니다.

**학생 접속 주소** → <https://j33333376-ops.github.io/math1-ch4/>

---

## 폴더 구조

```
.
├─ index.html              ← 4단원 목차 (여기서 각 활동으로 이동)
├─ apps/                   ← 개별 콘텐츠 HTML
│   ├─ 01-pixel-zoom.html          픽셀 돋보기            (137쪽)
│   ├─ 02-point-line-plane.html    점·선·면 탐구실        (137~139쪽)
│   └─ 06-mole-game.html           두더지 잡기            (152쪽)
├─ assets/
│   ├─ common.css          공통 색·글꼴·'목차로' 버튼·기본 부품
│   ├─ common.js           목차 버튼 자동 삽입, 학습 기록, 캔버스 도우미(MK)
│   └─ vendor/
│       ├─ tex-svg.js      MathJax (수식 표시)
│       └─ three.min.js    Three.js (3차원 도형)
├─ _원본/                  변환 전 원본 백업 (저장소에는 올리지 않음)
└─ .gitignore
```

라이브러리는 각 HTML에 붙여 넣지 않고 `assets/vendor/`에 **한 벌만** 두고 함께 씁니다.
덕분에 콘텐츠 한 개가 30~60KB로 가벼워지고, 한 반 전체가 동시에 열어도 학교 무선망에 부담이 적습니다.

---

## 새 콘텐츠 만드는 방법

### 1. `apps/` 에 HTML 파일 추가

`<head>` 에 아래 두 줄을 넣습니다.

```html
<link rel="stylesheet" href="../assets/common.css">
<script src="../assets/common.js" data-home="../index.html" defer></script>
```

수식이나 3차원 도형이 필요하면 필요한 것만 더 넣습니다.

```html
<script src="../assets/vendor/tex-svg.js"></script>    <!-- 수식 -->
<script src="../assets/vendor/three.min.js"></script>  <!-- 3차원 -->
```

`<header>` 안 맨 끝에 목차 버튼을 넣습니다. (안 넣으면 화면 오른쪽 위에 자동으로 뜹니다.)

```html
<a class="home-btn" href="../index.html">← 목차</a>
```

### 2. `index.html` 의 `DATA` 목록에 한 줄 추가

`status` 를 `"soon"` → `"done"` 으로 바꾸고 `file` 경로만 맞추면 목차에 바로 나타납니다.

### 3. 배포

```bash
git add -A
git commit -m "합동 포개기 콘텐츠 추가"
git push
```

푸시하고 30초~1분 뒤 GitHub Pages에 자동 반영됩니다.

---

## `common.js` 가 제공하는 도구 (`MK`)

| 함수 | 하는 일 |
|---|---|
| `MK.$(id)` | 아이디로 요소 찾기 |
| `MK.fit(canvas, draw)` | 캔버스를 부모 크기에 맞추고 고해상도로 그리기 (창 크기 변경 자동 대응) |
| `MK.pos(canvas, ev)` | 마우스·터치 좌표를 캔버스 기준으로 변환 |
| `MK.dist / MK.deg` | 두 점 사이 거리 / 라디안→도 |
| `MK.randInt / MK.pick` | 문제 무작위 생성용 |
| `MK.tex(el)` | MathJax 수식 다시 조판 |
| `MK.visited()` | 학생이 학습한 콘텐츠 목록 (목차의 ✓ 표시에 사용) |

---

## 개발 예정 목록

| 소단원 | 콘텐츠 | 교과서 |
|---|---|---|
| 1. 점, 선, 면 | ✅ 픽셀 돋보기 / ✅ 점·선·면 탐구실 | 137~140 |
| 2. 각 | 각도 실험실 · 수선의 발과 거리 | 141~145 |
| 3. 위치 관계 | 3D 위치 관계 탐험 | 146~151 |
| 4. 평행선의 성질 | ✅ 두더지 잡기 · 평행선 각 탐구실 · 보조선 도전 · 착시 실험실 | 152~156 |
| 5. 삼각형의 작도 | 가상 작도판 · 삼각형 결정 조건 | 157~164 |
| 6. 삼각형의 합동 | 합동 포개기 | 165~169 |
| 더 해 보기 | 에그 퍼즐 · 흔들리지 않는 삼각형(트러스) | 174~175 |

---

인천구월중학교 수학과 · 2026학년도
