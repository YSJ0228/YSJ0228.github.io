# 모아모아 초대 랜딩 사이트

이 폴더는 **`YSJ0228.github.io` 레포로 미러링되는 원본**입니다.
여기서 고치고, 아래 순서로 Pages 레포에 반영하세요.

```bash
# Moa 레포에서 수정 → Pages 레포로 복사 → 푸시
cp -R ~/Documents/Claude/Projects/Moa/web/. ~/Documents/Claude/Projects/moa-pages/
cd ~/Documents/Claude/Projects/moa-pages
git add -A && git commit -m "랜딩 페이지 업데이트" && git push
```

## 파일 역할

| 파일 | 역할 |
|---|---|
| `join/index.html` | 초대 랜딩 페이지 — 코드 표시·복사, 앱 열기, 스토어 안내 |
| `index.html` | 루트 페이지 (스토어 링크만 있는 최소 페이지) |
| `.well-known/assetlinks.json` | **Android App Links 검증용.** Play 앱 서명 SHA-256 필요 |
| `.well-known/apple-app-site-association` | **iOS Universal Links 검증용.** Apple Team ID 필요 |
| `.nojekyll` | 없으면 GitHub Pages가 `.well-known/`을 통째로 무시함 (필수) |
| `_headers` | Cloudflare Pages로 옮길 때만 쓰임. GitHub Pages는 무시 |

## 주소를 바꿀 때

호스트는 **세 곳이 반드시 일치**해야 합니다. 하나라도 다르면 검증이 전부 실패해요.

1. `app.json` → `android.intentFilters[0].data[0].host`
2. `app.json` → `ios.associatedDomains`
3. `app/invite.tsx` → `INVITE_LINK_BASE`

바꾸면 **네이티브 재빌드가 필요합니다** (OTA로 안 나감).
