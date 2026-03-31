# NGO DRTV 일일 효율 대시보드

매일 CSV 데이터를 `data/` 폴더에 업로드하면 대시보드가 자동으로 갱신됩니다.

---

## 폴더 구조

```
drtv-dashboard/
├── index.html                  ← 대시보드 (자동 갱신됨, 직접 수정 불필요)
├── update_dashboard.py         ← 업데이트 스크립트
├── data/                       ← CSV 파일 넣는 폴더
│   ├── DRTV일별효율_03월_DATA.csv
│   └── ...
└── .github/
    └── workflows/
        └── update.yml          ← GitHub Actions 자동화 설정
```

---

## 매일 데이터 업데이트 방법

### GitHub에서 직접 업로드 (가장 간단)

1. GitHub 레포 페이지 접속
2. `data/` 폴더 클릭
3. **Add file → Upload files** 클릭
4. 새 CSV 파일 드래그앤드롭
5. **Commit changes** 클릭
6. 1~2분 후 대시보드 URL 자동 갱신 완료 ✅

> CSV 파일을 올리면 GitHub Actions가 자동으로 `update_dashboard.py`를 실행해서 `index.html`을 갱신합니다.

---

## CSV 파일 형식

| 컬럼명 | 설명 |
|--------|------|
| 상담일자 | YYYY-MM-DD 형식 |
| Channel | 채널명 (예: EBS, JTBC4) |
| 소재 | 소재명 |
| 광고비 | 숫자 (쉼표 포함 가능) |
| 광고횟수 | 숫자 |
| I/B콜수 | 인입콜 수 |
| 응대호 | 응대콜 수 |
| 정기건수 | 정기후원 건수 |
| 정기금액 | 정기후원 금액 |

---

## 로컬에서 직접 실행하는 방법 (선택사항)

Python이 설치된 경우, 직접 스크립트를 실행할 수 있습니다.

```bash
python update_dashboard.py
```

---

## GitHub Pages 설정

1. 레포 → **Settings → Pages**
2. Source: **Deploy from a branch**
3. Branch: **main** / `/(root)`
4. Save → URL 생성: `https://[아이디].github.io/drtv-dashboard`
