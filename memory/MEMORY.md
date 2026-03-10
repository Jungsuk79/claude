# 프로젝트 메모리

## 환경
- OS: Windows 11
- Shell: bash (WSL 아님, Git Bash 등)
- Node.js v22 사용 가능 / Python 없음
- 작업 경로: C:/project/claude

## 프로젝트 구조
- `images/` : 이미지 파일 보관
  - `image.png` : 원본 이미지 (378x455)
  - `20260304/` : 날짜 폴더에 잘린 이미지 저장
- `sample/` : 샘플 소스 코드
  - `이벤트/` : 이벤트 페이지 샘플
  - `카달로그/` : 카탈로그 페이지 샘플
- `guide.html` : 이벤트 페이지 개발 가이드 (PDF 출력용)

## 작업 내역
- 이미지 4등분 자르기 스크립트 (`crop.js`) 작성
  - sharp 라이브러리 사용 (npm install sharp)
  - 출력: webp 포맷, img_product_01~04.webp
  - 날짜 폴더 자동 생성
  - → 이 스크립트는 이벤트 페이지용 디자인 시안을 섹션별로 잘라 webp로 변환하는 용도

- 신세계 이벤트 페이지 코드 분석 (2026-03-10)
  - 대상: `sample/이벤트/` 내 2개 폴더 전체 분석
  - 앱 웹뷰 삽입용 스니펫 방식 (DOCTYPE 없음)
  - 이미지 기반 레이아웃 + 투명 버튼(opacity:0) 오버레이 방식
  - 단위: vw 사용 (px 아님)
  - 가로 스크롤: evt-scroll (scroll-snap, position:absolute)
  - 팝업: JS 없이 CSS checkbox + :has(:checked) 방식
  - 앱 네이티브 함수: $$unifiedMoveTo({ screenId, screenDetail, conditions })
  - CDN 경로: https://appdept.shinsegae.com/contents/event/{폴더명}/{파일명}.webp
  - 가이드 문서: guide.html (PDF 출력 가능)

## 사용자 선호
- 파일명 형식: `img_product_01.webp` (날짜 폴더 안에 저장)
- 이미지 처리: Node.js + sharp 사용
- 새 피그마 디자인 → 분석된 코드 패턴 기반으로 동일한 방식으로 구현
