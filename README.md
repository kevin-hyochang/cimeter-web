# cimeter 랜딩 페이지

[cimeter](https://www.npmjs.com/package/cimeter) 의 공개 랜딩입니다. 제품 소스는 비공개 저장소에 있고, 이 저장소에는 공개해도 되는 정적 파일만 둡니다.

배포 주소: <https://kevin-hyochang.github.io/cimeter-web/>

빌드 단계가 없습니다. `main` 에 푸시하면 GitHub Actions가 그대로 Pages에 올립니다.

| 파일 | 내용 |
|---|---|
| `index.html` | 랜딩 (한/영 토글, 라이트·다크) |
| `legal.html` | 이용약관 및 개인정보처리방침 |
| `claim.html` | Stripe 결제 완료 후 라이선스 키 수령 |
| `demo-report.html` | 샘플 리포트 |

## 직접 수정하지 않습니다

이 파일들은 제품 저장소에서 생성해 동기화합니다. 여기서 직접 고치면 다음 동기화 때 덮어써집니다.

```bash
node scripts/sync-landing.mjs ../cimeter-web https://cimeter-api.onrender.com
```

동기화 스크립트가 복사하면서 라이선스 서버 주소를 주입합니다. 제품 저장소의 원본은 같은 출처를 가리킨 채로 두어야, 로컬에서 서버를 띄웠을 때 그 서버에 붙습니다.

## 연결된 서버

체험 폼과 키 수령 페이지는 <https://cimeter-api.onrender.com> 을 호출합니다. 서버 쪽 `ALLOWED_ORIGINS` 에 이 페이지의 출처가 들어 있어야 브라우저가 응답을 읽습니다.

```bash
ALLOWED_ORIGINS=https://kevin-hyochang.github.io
```

서버 상태는 <https://cimeter-api.onrender.com/api/health> 에서 확인합니다.
