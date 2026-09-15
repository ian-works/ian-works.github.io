# 디자인 결정

## 무엇을 참고했나

[leerob.com](https://leerob.com)의 결을 따라갑니다. 핵심은 네 가지입니다.

1. 따뜻한 종이 톤 배경 (`#f7f7f4`), 다크는 `#1a1a18`
2. 본문이 **세리프** — leerob은 `Iowan Old Style / Palatino / Georgia` 스택을
   씁니다. 여기서도 같은 스택을 쓰고, 한글은 `Noto Serif KR` 로 떨어지게
   순서를 잡았습니다. 라틴 글자는 앞쪽 세리프가, 한글은 Noto Serif KR이
   각각 잡히는 식입니다.
3. 좁은 한 단 + 실선 구분. 카드·그림자·알약 배지 없음
4. 오른쪽에 **세로로 긴 그림 한 장**. 스크롤하면 따라옵니다(`position: sticky`)

테마는 `prefers-color-scheme` 로 **시스템 설정을 따라갑니다.** 토글 버튼은
없습니다.

## 값

`styles.css` 상단 `:root` 에 모여 있습니다.

| 토큰 | 라이트 | 다크 |
| --- | --- | --- |
| `--bg` | `#f7f7f4` | `#1a1a18` |
| `--text` | `#16161e` | `#eceae4` |
| `--text-dim` | `#4d4d55` | `#a8a69f` |
| `--text-faint` | `#86868d` | `#7c7a74` |
| `--rule` | `#e3e2dc` | `#2e2e2b` |
| `--link-underline` | `#c7c6be` | `#55534d` |

- 본문 18px / `line-height: 1.75`
- `--font-ui` (시스템 산세리프)는 메타 정보·꼬리말 같은 작은 글자에만 씁니다
- 폰트는 Google Fonts에서 Noto Serif KR만 받습니다. 라틴은 시스템 폰트라
  네트워크 요청이 없습니다

## 레이아웃

`.page` 가 2열 그리드입니다.

```
.page { grid-template-columns: minmax(0, 1fr) 320px; }
.intro   → 1열 1행
.content → 1열 2행
.art     → 2열 1~2행, sticky
```

DOM 순서는 `intro → art → content` 입니다. 900px 이하에서 한 단으로 접히면
자연스럽게 **머리말 → 그림 → 본문** 순서가 됩니다. leerob의 모바일은 그림을
아래로 내리지만, 여기서는 그림이 이 사이트의 성격을 말해주는 요소라 본문
앞에 둡니다.

## 항목 추가하기

각 섹션에 주석을 달아 두었습니다. `li` 하나를 같은 모양으로 복사하면 됩니다.

**저서** — 제목 왼쪽, 메타 오른쪽, 행마다 실선:

```html
<li>
  <a href="..." target="_blank" rel="noopener noreferrer">제목</a>
  <span class="meta">출판사 · 연도</span>
</li>
```

**앱 / 웹 서비스** — 제목 + 상태 + 설명 한 문단:

```html
<li>
  <p class="block-head">
    <a href="...">이름</a>
    <span class="meta">테스트 중</span>
  </p>
  <p class="note">설명</p>
</li>
```

링크가 아직 없으면 `<a>` 대신 `<span class="name">이름</span>` 을 씁니다.

상태는 색 배지가 아니라 흐린 글자입니다 — 절판 / 테스트 중 / 기획 중처럼
그대로 적으면 됩니다.

섹션 자체를 늘릴 때는 `<section class="section">` 을 복사하세요. 위쪽 실선과
간격은 클래스가 알아서 붙입니다.

## 접근성 / 잔손질

- `word-break: keep-all` — **빼지 마세요.** 없으면 한글이 단어 중간에서
  끊깁니다("만듭니 / 다.")
- `prefers-reduced-motion: reduce` 에서 풍경 애니메이션이 모두 멈춥니다
- 링크 밑줄은 기본으로 켜 두고 호버에서 진해집니다. `text-underline-offset`
  으로 한글 받침과 겹치지 않게 띄웠습니다
- 파비콘은 `assets/favicon.svg` — 어두운 타일에 세리프 `ian`. 16px에서도
  읽히도록 글자를 최대한 키웠습니다. `assets/apple-touch-icon.png` 는 같은
  SVG를 180px로 렌더링한 것이라, 파비콘을 고치면 같이 다시 만들어야 합니다
  ([workflow.md](workflow.md) 참고)

## 지금 쓰지 않는 것

- 책 표지 이미지 — 목록이 글자만으로 충분해서 뺐습니다. 되살리려면
  [sources.md](sources.md)의 표지 URL을 참고하세요
- 상단 내비게이션 — 한 화면에 다 들어와서 없앴습니다
- `@ian-works` 핸들 줄 — 꼬리말의 GitHub 링크로 갈음합니다
- 책 표지 파일은 더 쓰지 않아 저장소에서 지웠습니다. 원본 주소는
  [sources.md](sources.md)에 있습니다

## 링크 미리보기

`assets/og.png` (1200×630). 왼쪽에 이름과 한 줄, 오른쪽에 풍경 — 사이트
레이아웃을 그대로 줄인 카드입니다. `twitter:card` 는 `summary_large_image`.

풍경이나 문구를 고치면 이 이미지도 다시 뽑아야 합니다. 만드는 법은
[workflow.md](workflow.md)에 있습니다.
