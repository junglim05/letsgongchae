# 공채 준비 프로그램 할인 랜딩페이지 — Vercel 배포

## 원인 (썸네일이 안 뜬 이유)
이전 버전은 일부 이미지를 **프로젝트 내부 경로**로 참조하고 있어서, `index.html`만 올리면
그 이미지들이 404가 났어요. 이번 버전은 해당 이미지들을 `assets/` 폴더로 정리했습니다.
**`index.html`과 `assets/` 폴더를 반드시 함께** 올려주세요.

## 폴더 구성 (이 구조 그대로 유지)
```
index.html
assets/
  vod-33-thumb.png
  challenge-3-thumb-web.png
  logo-letscareer-default.png
  logo-letscareer-horizontal-bw.png
  favicon.svg / favicon-32.png / apple-touch-icon.png
  og-image.png              ← 카카오·페북·슬랙 공유 미리보기 (1200×630)
vercel.json
```

## OG / 파비콘
- `<head>`에 og:title / og:description / og:image / twitter:card / favicon 태그 포함
- og:image 절대 URL은 `https://letsgongchae.vercel.app/assets/og-image.png` 기준. 도메인이 바뀌면 알려주세요.
- 카카오톡 캐시 갱신: https://developers.kakao.com/tool/debugger/sharing 에서 URL 입력 → 캐시 초기화

## 방법 1) 드래그 앤 드롭
1. zip 압축 해제
2. https://vercel.com/new → 하단 **Drag & drop** 영역에 `deploy` **폴더 전체**를 끌어다 놓기
   (index.html 파일 하나만 올리면 다시 썸네일이 깨집니다)
3. Framework Preset **Other**, Build Command·Output Directory 공란 → Deploy

## 방법 2) Vercel CLI
```bash
npm i -g vercel
cd deploy
vercel --prod
```

## 방법 3) GitHub
`deploy` 폴더 **내용 전체**를 리포 루트에 커밋 → Vercel에서 Import → Preset **Other**, 빌드 설정 공란.

## 남아 있는 외부 의존
VOD 1종·가이드북 2종 썸네일은 렛츠커리어 S3(`letsintern-bucket.s3...`)를 직접 참조해요.
S3가 외부 도메인 요청을 차단하면 이 3개만 안 보일 수 있습니다.
그럴 경우 해당 이미지 파일을 주시면 `assets/`에 넣어 다시 내보내드립니다.

## 재배포
`index.html`은 컴파일 산출물이라 직접 수정하지 마세요. 원본을 고친 뒤 다시 내보내야 합니다.
