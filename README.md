# 공채 준비 프로그램 할인 랜딩페이지 — Vercel 배포

## 폴더 구성
- `index.html` — 랜딩페이지 전체 (CSS/JS/이미지 모두 내장된 단일 파일)
- `vercel.json` — 정적 배포 설정
- 빌드 과정 없음. 정적 파일 그대로 올리면 끝.

## 방법 1) 드래그 앤 드롭 (가장 빠름)
1. 이 `deploy` 폴더를 압축 해제한 상태로 준비
2. https://vercel.com/new 접속 → 하단 **Deploy a static site / Drag & drop** 영역에 `deploy` 폴더를 그대로 끌어다 놓기
3. Framework Preset: **Other**, Build Command: 비워두기, Output Directory: 비워두기 → Deploy

## 방법 2) Vercel CLI
```bash
npm i -g vercel
cd deploy
vercel            # 미리보기 배포
vercel --prod     # 프로덕션 배포
```
프롬프트에서 Build Command / Output Directory는 모두 Enter(기본값)로 넘기면 됩니다.

## 방법 3) GitHub 연동
1. `deploy` 폴더 내용을 새 리포지토리 루트에 커밋
2. Vercel → Add New Project → 해당 리포 Import
3. Framework Preset **Other**, Build Command·Output Directory 공란 → Deploy

## 배포 후 확인 사항
- 프로그램 썸네일 5종, 히어로 캐러셀, 쿠폰 복사 버튼, FAQ 아코디언 동작
- 커스텀 도메인: Vercel 프로젝트 → Settings → Domains
- 광고 트래킹(GTM/Meta Pixel)을 붙이려면 알려주세요. `index.html`은 컴파일 산출물이라 직접 수정하지 말고 원본을 고쳐 다시 내보내야 합니다.
