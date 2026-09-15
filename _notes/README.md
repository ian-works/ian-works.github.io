# _notes — 작업 메모

이 사이트(`ian-works.github.io`)를 만들며 모은 자료와, 나중에 개편할 때
다시 찾지 않아도 되도록 정리해 둔 기록입니다.

`_` 로 시작하는 디렉터리라 GitHub Pages(Jekyll)가 빌드 결과물에 넣지
않습니다. git에는 남지만 `https://ian-works.github.io/_notes/...` 로는
열리지 않습니다. `_config.yml` 의 `exclude` 에도 명시해 두었습니다.

> 주의: 저장소에 `.nojekyll` 파일을 추가하면 Jekyll이 꺼지면서 이 폴더도
> 그대로 서빙됩니다. 그때는 `.gitignore` 로 옮기거나 폴더를 저장소 밖으로
> 빼야 합니다.

## 파일

| 파일 | 내용 |
| --- | --- |
| [sources.md](sources.md) | 저서·앱 관련해서 수집한 사실관계와 원본 링크 |
| [design.md](design.md) | 디자인 결정, 색·폰트 값, 레이아웃 구조, 항목 추가 방법 |
| [scene.md](scene.md) | 오른쪽 풍경 SVG의 좌표 구조와 애니메이션 |
| [workflow.md](workflow.md) | 로컬 확인 방법과 작업하며 걸린 함정들 |
