# 작업 방법과 함정들

빌드 단계가 없습니다. `index.html`, `styles.css`, `assets/` 가 전부입니다.

## 로컬에서 보기

`file://` 로 열어도 되지만, 상대 경로와 폰트 때문에 서버로 띄우는 편이
확실합니다.

```sh
cd ~/workspace/ian-works
python3 -m http.server 8777
# http://127.0.0.1:8777/
```

## 헤드리스 Chrome으로 스크린샷

눈으로 확인할 때 씁니다.

```sh
CHROME="/Applications/Google Chrome.app/Contents/MacOS/Google Chrome"

"$CHROME" --headless=new --disable-gpu --hide-scrollbars \
  --virtual-time-budget=8000 --window-size=1200,1250 \
  --screenshot=shot.png "http://127.0.0.1:8777/"
```

`--virtual-time-budget` 을 넉넉히 줘야 웹폰트와 애니메이션이 자리를 잡습니다.

### 풍경만 크게 보기

실제 표시 크기에서는 SVG의 문제가 잘 안 보입니다. SVG만 뽑아 500px로
띄우는 임시 페이지를 만들어 찍으면 훨씬 잘 보입니다.

```sh
python3 - <<'EOF'
import re
html = open('index.html', encoding='utf-8').read()
svg  = re.search(r'<svg class="scene".*?</svg>', html, re.S).group(0)
css  = open('styles.css', encoding='utf-8').read()
open('/tmp/scene.html', 'w', encoding='utf-8').write(f"""<!DOCTYPE html>
<html><head><meta charset="utf-8"><style>{css}
body{{background:#fff;margin:0;padding:16px}}.scene-wrap{{width:500px}}</style></head>
<body><figure class="scene-wrap">{svg}</figure></body></html>""")
EOF
```

### 애니메이션이 실제로 도는지 확인

`--virtual-time-budget` 을 다르게 줘서 두 장 찍고 픽셀이 다른지 보면 됩니다.
정지 화면만 봐서는 알 수 없습니다.

## 함정 모음

작업하면서 실제로 걸린 것들입니다.

### 한글 줄바꿈

`word-break: keep-all` 이 없으면 단어 중간에서 끊깁니다 — "만듭니 / 다.",
"걸러내 / 는". `body` 에 걸어 두었습니다. 지우지 마세요.

### 헤드리스 Chrome의 최소 창 너비

`--window-size=390,...` 을 줘도 실제 레이아웃 뷰포트는 **500px 근처로
클램프**됩니다. 스크린샷은 390px로 잘리기 때문에 내용이 잘린 것처럼 보이지만
실제 버그가 아닙니다. 진짜 모바일 폭을 보려면 iframe에 넣어서 찍으세요.

```html
<!-- /tmp/harness.html -->
<style>html,body{margin:0;background:#666}iframe{width:390px;height:2400px;border:0}</style>
<iframe src="http://127.0.0.1:8777/"></iframe>
```

### macOS `sips` 의 크롭 기준

`sips -c H W --cropOffset T L` 에서 오프셋이 **`0 0` 이면 가운데 기준**으로
자르고, 값이 있으면 위쪽 기준으로 자릅니다. 스크린샷을 잘라 볼 때 엉뚱한
부분이 나오면 이것 때문입니다.

### 다크/라이트 강제

헤드리스 Chrome은 시스템 테마를 따라갑니다. `--force-dark-mode` 는 있지만
라이트 강제 플래그는 없습니다. 라이트를 보려면 CSS에서
`@media (prefers-color-scheme: dark)` 블록만 걷어낸 사본을 만들어 띄우세요.

### 교보문고 상품 페이지

SPA라 `curl` 이나 단순 fetch로는 **본문이 비어서** 옵니다. 텍스트 추출
프록시(`https://r.jina.ai/<url>`)를 통하면 ISBN·쪽수·표지 이미지 ID까지
읽을 수 있습니다.

### 아마존 상품 페이지

봇 차단이 강합니다. 표지 이미지는 페이지를 긁지 말고 ASIN 기반 CDN 패턴을
쓰세요 — `https://images-na.ssl-images-amazon.com/images/P/<ASIN>.01._SCLZZZZZZZ_.jpg`

### BlueArgos 앱 아이콘

검은 배경 위에 파란 링이 발광하는 그림입니다(투명 배경 아님). 밝은 배경에
그냥 올리면 검은 사각형이 됩니다. 둥근 타일로 감싸 앱 아이콘처럼 보이게
해야 합니다.

## 배포

`main` 에 push하면 GitHub Pages가 자동으로 배포합니다.
Settings → Pages → Deploy from a branch → `main` / `(root)` 로 설정되어
있습니다. 저장소 이름이 `ian-works.github.io` 라 사용자 페이지로 동작합니다.

`_notes/` 와 `_config.yml` 은 Jekyll이 결과물에서 제외합니다.
**`.nojekyll` 파일을 추가하면 이 제외가 무효가 되어 `_notes/` 가 그대로
공개됩니다.** 그럴 일이 생기면 `.gitignore` 로 옮기세요.
