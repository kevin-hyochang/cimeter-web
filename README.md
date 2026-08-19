# cimeter.dev

[cimeter](https://github.com/kevin-hyochang/cimeter) 의 랜딩 페이지입니다. 제품 소스는 비공개 저장소에 있고, 이 저장소에는 공개해도 되는 정적 파일만 둡니다.

빌드 단계가 없습니다. `main`에 푸시하면 GitHub Actions가 그대로 Pages에 올립니다.

| 파일 | 내용 |
|---|---|
| `index.html` | 랜딩 (한/영 토글, 라이트·다크) |
| `legal.html` | 이용약관 및 개인정보처리방침 |
| `claim.html` | Stripe 결제 완료 후 라이선스 키 수령 |
| `demo-report.html` | 샘플 리포트. 제품 저장소에서 생성해 복사한다 |

## API 주소 설정

체험 폼과 키 수령 페이지는 라이선스 서버를 호출합니다. Pages는 정적 파일만 서빙하므로 서버는 별도 호스팅이 필요하고, 두 파일 상단의 값을 그 주소로 바꿔야 합니다.

```html
<script>window.CIMETER_API = "https://api.cimeter.dev";</script>
```

빈 문자열이면 같은 출처를 호출합니다. 제품 저장소에서 로컬로 띄울 때 쓰는 값입니다.

서버 쪽에는 이 페이지의 출처를 허용 목록에 넣어야 합니다. 넣지 않으면 브라우저가 응답을 막습니다.

```bash
ALLOWED_ORIGINS=https://cimeter.dev,https://kevin-hyochang.github.io
```

## 데모 리포트 갱신

제품 저장소에서 생성한 뒤 복사합니다.

```bash
npm run build && cp server/public/demo-report.html ../cimeter-web/
```

## 커스텀 도메인

`CNAME` 파일에 도메인을 한 줄로 적고 DNS를 GitHub Pages로 향하게 하면 됩니다. 도메인을 붙이면 위의 `ALLOWED_ORIGINS` 와 `CIMETER_API` 도 함께 갱신해야 합니다.
