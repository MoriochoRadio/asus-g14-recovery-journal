# ASUS G14 부팅 장애 복구 기록

ASUS ROG Zephyrus G14 GA403UM의 부팅 장애, 복구 시도, Windows 재설치 및 점검 기록. 작업 기간: 2026-09-18~19.

## 진행 요약

| 단계 | 현상 | 시도 | 결과 |
|---|---|---|---|
| 최초 장애 | 오류 화면 0% 정지 후 BIOS 진입 | SSD 인식 확인, 전체 이미지 확보 | 이미지 읽기 오류 0, Windows 부팅 불가 |
| 파티션 복구 | 주 GPT·보호 MBR 손상 | 정상 기록과 백업 GPT 대조 후 복원 | 파티션 인식 회복, WinRE 진입 |
| 파일시스템 수리 | NTFS 구조 오류, 파일 접근 불가 | CHKDSK 수리 | 파일 접근 회복, Windows는 0x74로 중단 |
| 시스템 복구 | BAD_SYSTEM_CONFIG_INFO | 레지스트리 사본 검사, SFC·DISM 시도 | 사본 로드 성공, DISM은 SAM 로드 실패로 중단 |
| ASUS 복구 | 복구 USB의 Wi-Fi 연결 중 0xD1/nwifi.sys 발생 | Microsoft 공식 설치 USB로 전환 | 새 Windows 설치 및 로그인 완료 |
| 재설치 후 점검 | 드라이버 누락 1개 | 공식 구성요소 설치·업데이트, 재부팅 후 검사 | 문제 장치 0개, 시스템·SSD·MyASUS 검사 완료 |

## 최종 상태

- **사용 환경:** Windows 재설치 완료, 드라이버 적용 확인, 일상 사용 재개.
- **검사 결과:** DISM 손상 없음, SFC 검증 완료, SSD 짧은 자체 검사 통과·매체 오류 0, MyASUS 문제 0개.
- **남은 사항:** 최초 손상 원인 미확정. NVMe 관리 명령 오류·시간초과 기록 존재. 오프라인 메모리 검사와 일부 기능 검증 미완료.
- **설정:** Armoury Windows 모드 / Windows 균형 조정. 추가 부하 검사 없이 사용하기로 결정.

확인된 범위에서 부품 고장은 검출되지 않았으며, 검사 범위와 남은 오류는 [점검 결과](docs/04-validation.md)에 기록.

## 문서 목록

| 문서 | 내용 |
|---|---|
| [타임라인](docs/01-timeline.md) | 작업 순서와 확인 시각 |
| [복구 과정](docs/02-recovery-journey.md) | 단계별 현상·시도·결과 |
| [주요 결정](docs/03-decisions.md) | 복구·설치 방법을 선택한 근거 |
| [재설치 후 점검](docs/04-validation.md) | 적용 버전, 검사 수치, 미완료 항목 |
| [원인 분석](docs/05-cause-and-uncertainty.md) | 확인된 손상과 원인 미확정 사유 |
| [작업 정리](docs/06-retrospective.md) | 주요 확인 사항과 후속 관리 |
| [참고 기록](evidence/README.md) | 근거 자료 목록과 공식 문서 |

## 장비 정보

| 항목 | 사양 |
|---|---|
| 모델 | ASUS ROG Zephyrus G14 GA403UM |
| CPU | AMD Ryzen 9 270 |
| GPU | Radeon 780M / RTX 5060 Laptop GPU |
| RAM | 32GB |
| SSD | Micron MTFDKBA1T0QGN-1BN1AABGA, 1TB |
| Windows | Windows 11 Home 25H2, 26200.9457 |
| BIOS / SSD 펌웨어 | GA403UM.310 / V8MA000 |

버전·검사 기준일: 2026-09-19. 초기 복구는 별도 정상 PC를 활용했으며, 재설치 후 점검은 해당 노트북에서 진행.

공개 범위: 정리 문서와 [검사 수치](evidence/measurements.json). 원본 로그·복구 이미지·개인정보는 별도 보관. [공개 자료 안내](PRIVACY.md)
