# ASUS G14 부팅 장애 복구기

2026년 9월 18일, 쓰고 있던 노트북에 오류 화면이 떴다. 진행률은 0%에서 멈췄고, 재부팅 후에는 Windows 대신 BIOS가 열렸다.

처음에는 기존 환경을 살려 보려고 했다. SSD 전체를 이미지로 남기고 파티션 표와 파일시스템을 복구했다. 파일은 다시 읽을 수 있게 됐지만 Windows는 끝내 부팅되지 않았다. ASUS 복구 USB마저 Wi-Fi 연결 중 오류가 나면서, 결국 Microsoft 공식 USB로 새로 설치했다.

금요일부터 토요일까지 이어진 과정을 정리했다. 무엇을 시도했고 어디서 막혔는지, 다시 겪는다면 무엇부터 확인할지 남겨 두고 싶었다.

## 지금은

Windows를 새로 설치한 뒤 필요한 드라이버를 정리했고, 다시 사용할 수 있는 상태가 됐다.

- 장치 관리자 문제 항목 0개
- Windows 시스템 검사 완료
- SSD 짧은 자체 검사 통과, 매체 오류 0
- MyASUS 자동 진단 문제 0개

최초 고장의 원인은 아직 모른다. 새 설치 뒤에도 NVMe 관리 명령 오류가 남아 있어 [확인한 내용과 모르는 부분](docs/05-cause-and-uncertainty.md)을 따로 정리했다. 추가 부하 검사는 하지 않고 일상 사용으로 돌아가기로 했다.

## 읽는 순서

1. [복구 과정](docs/02-recovery-journey.md) — 고장부터 새 Windows에 로그인하기까지
2. [선택의 이유](docs/03-decisions.md) — 기존 환경을 포기하고 재설치를 결정한 이유
3. [재설치 후 점검](docs/04-validation.md) — 드라이버 버전과 실제 검사 결과
4. [원인에 대해 알게 된 것](docs/05-cause-and-uncertainty.md) — 남아 있는 단서와 결론
5. [돌아보며](docs/06-retrospective.md) — 이틀 동안 겪으며 남은 생각

정확한 순서와 시각은 [타임라인](docs/01-timeline.md), 자료 출처는 [참고 기록](evidence/README.md)에 모았다.

## 복구 흐름

~~~mermaid
flowchart TD
    A["오류 화면 이후 부팅 불능"] --> B["SSD 전체 이미지 보존"]
    B --> C["GPT 복원 · NTFS 수리"]
    C --> D["파일 접근 회복 · Windows 부팅은 실패"]
    D --> E["ASUS 복구 USB에서도 Wi-Fi 오류"]
    E --> F["Microsoft USB로 Windows 새 설치"]
    F --> G["드라이버 정리 · 진단 후 사용 재개"]
~~~

## 노트북 사양

| 항목 | 사양 |
|---|---|
| 모델 | ASUS ROG Zephyrus G14 GA403UM |
| CPU | AMD Ryzen 9 270 |
| GPU | Radeon 780M / RTX 5060 Laptop GPU |
| RAM | 32GB |
| SSD | Micron MTFDKBA1T0QGN-1BN1AABGA, 1TB |
| Windows | Windows 11 Home 25H2, 26200.9457 |
| BIOS / SSD 펌웨어 | GA403UM.310 / V8MA000 |

버전과 검사 결과는 2026년 9월 19일 기준이다. 초기 복구는 별도 정상 PC의 도움을 받았고, 재설치 후 점검은 이 노트북에서 진행했다.

개인정보가 포함된 원본 로그와 복구 이미지는 별도 보관했다. 저장소에는 정리한 글과 [검사 수치](evidence/measurements.json)를 올렸다. 자세한 내용은 [공개 자료 안내](PRIVACY.md)를 참고하면 된다.
