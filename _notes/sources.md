# 수집한 사실관계

사이트에 적은 내용의 출처입니다. 수치나 링크를 다시 쓸 일이 있으면 여기서
가져오세요. 조사 시점은 2026-09-15입니다.

## 저서 — 리눅스 백신 개발

같은 내용이 세 번 출간됐습니다. 한빛판이 먼저 나왔고, 영문판이 이어졌고,
2023년에 소나무에에서 다시 나왔습니다.

### 1. UML로 개발하는 리눅스 백신 프로그램 (현행 국내판)

- 저자 이창우, 출판사 **소나무에**
- 발행일 **2023-04-28**, **331쪽**, 176 × 248 mm
- ISBN **979-11-979255-1-1** (`9791197925511`)
- 부제(표지) — "초보 개발자가 소프트웨어 공모전에 도전하는 이야기"
- 교보문고 POD, 정가 24,000원
- 링크: https://product.kyobobook.co.kr/detail/S000202225021
- 출판사 페이지: https://www.sonamue.com/books/computer-books/리눅스-백신-프로그램

### 2. Beginning Linux Antivirus Development (영문판)

- 부제 "The Story about IoT Security Design with UML"
- 저자 Ian Lee, Jenny Lim
- Kindle 전자책 **2017-11-29**, ASIN `B077VRYKYP`
- 종이책 ASIN `B08T4B1LWM`, ISBN `9791197325601`
- 링크: https://www.amazon.com/-/ko/dp/B077VRYKYP
- 출판사 페이지: https://www.sonamue.com/books/computer-books/beginning-linux-antivirus

### 3. 직접 설계하고 개발하는 IoT 백신(초급) (초판, 절판)

- 저자 이창우, 출판사 **한빛미디어**
- 발행일 **2017-04-07**, **300쪽**, ISBN `9788968487361`, 정가 24,000원
- 링크: https://www.hanbit.co.kr/books/직접-설계하고-개발하는-iot-백신-초급?code=B8304726903
- 목차 대분류 — 백신 개발 프로젝트 Airplane 시작 / 요구사항 / 프로토타입 /
  설계 / 구현 / 테스트 / 뫼비우스의 띠

### 데모 영상

- YouTube `dAGKQBZxKFI` — https://www.youtube.com/watch?v=dAGKQBZxKFI
- 설명(출판사 페이지) "The Demo video for Beginning Linux Antivirus Development"
- 썸네일은 `https://img.youtube.com/vi/dAGKQBZxKFI/mqdefault.jpg` 가 16:9.
  `hqdefault` 는 4:3 안에 레터박스가 들어 있어 잘라 써야 합니다.
  `maxresdefault` 는 이 영상에 없습니다(404).

### 책 소개 문구 (소나무에/교보 기준, 필요하면 재사용)

> 저도 백신을 개발 할 수 있을까요? 네. 여러분도 개발할 수 있습니다.
> 왜냐면 백신도 소프트웨어의 한 종류입니다. (…) 이렇게 보안 솔루션을
> 개발해 보지 않은 분들을 위해 Security School을 시작하게 되었습니다.
> 이 책은 Security School의 첫 번째 책입니다.

구성 요약 — ① UML 실용 설계 ② 백신 개발 초급 ③ 모듈식 구성.

### 표지 이미지

지금 사이트는 표지를 쓰지 않지만, 되살릴 때를 위해 남깁니다.

- 국내판(소나무에) — 구글 사이트에 올라간 목업 이미지. URL이 길고 만료될 수
  있으니 필요하면 출판사 페이지에서 다시 받으세요. 배경 여백을 잘라내 쓰면
  됩니다(478 × 692 정도).
- 영문판 — `https://images-na.ssl-images-amazon.com/images/P/B077VRYKYP.01._SCLZZZZZZZ_SL1000_.jpg`
  (ASIN 기반 CDN 패턴, 다른 ASIN도 같은 형식으로 됩니다)
- 한빛판 — `https://cdn-prod.hanbit.co.kr/books/B8304726903_l.jpg`
- **교보문고 표지 CDN**은 `https://contents.kyobobook.co.kr/sih/fit-in/800x0/pdt/{상품이미지ID}.jpg`
  형식입니다. ISBN을 넣으면 "제공된 상품이미지가 없습니다" 플레이스홀더가
  옵니다 — 상품 페이지에서 실제 이미지 ID를 찾아야 합니다.
  (이 책은 `1400000592540`)

두 표지 파일(`assets/book-en-2017.jpg`, `assets/book-hanbit-2017.jpg`)은
목록에서 표지를 뺄 때 삭제했습니다. 커밋 `2bbab65` 이전에 남아 있습니다.

## App — BlueArgos

- 저장소: https://github.com/ian-works/blue-argos
- 사이트: https://ian-works.github.io/blue-argos/
- 한 줄 설명 — "깨끗하고 편리한 과속카메라 알림"
- 핵심 문구(앱 랜딩 페이지에서 그대로 가져옴)
  - "목적지나 경로를 입력하지 않아도, 지금 달리는 길 위의 카메라를 그때그때
    알려줍니다"
  - "회원가입, 로그인, 차량 정보 입력도 필요 없습니다"
  - "현재 속도를 기준으로 모든 카메라를 동일하게 15초 전에 알려줍니다"
  - "2주 혹은 한 달에 한 번 3MB 정도 데이터를 다운로드하여 계속 사용합니다"
  - "통신·배터리 사용 최소화 · 광고 없음"
- AI 기반 카메라 데이터 전처리 — 특허 출원 중
- 데이터 출처: 경찰청 · 공공데이터포털(data.go.kr), 공공누리 제1유형(출처표시)
- iOS / Android 모두, 테스터 모집 중
- 앱 아이콘은 `assets/blue-argos-icon.png` 에 사본이 있습니다(검은 배경 위
  파란 링). 밝은 배경에 올릴 때는 둥근 타일로 감싸야 자연스럽습니다.

## Web Service — Save my time

- 사람들의 시간을 아껴주기 위해 준비 중인 웹 서비스. **아직 기획 중**이라
  사이트에는 한 줄만 적어 두었습니다.

## 소개 문구

사이트에 쓰는 표현은 회사 이름을 넣지 않기로 했습니다.

> 보안 회사에서 보안솔루션을 개발했었고, 현재는 국내 전자회사에서 개발자로
> 근무중입니다. / 사람들에게 편리하고 이로운 무언가를 만드는 걸 좋아합니다.

참고로 영문판 책의 저자 소개에는 아래처럼 적혀 있습니다. 필요하면 근거로
쓸 수 있습니다.

> Ian Lee has 10 years of experience in the development of antivirus
> firewalls for PC, Intrusion Prevention System Engine and solutions for web
> security in an information security company. He has been designing enhanced
> security for smart TVs in Samsung Electronics (…) since 2012.
