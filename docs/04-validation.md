# 재설치 후 점검

[처음으로](../README.md) · [검사 수치 JSON](../evidence/measurements.json)

기준일: 2026-09-19. 새 Windows에서 확인한 적용 버전, 검사 결과 및 미완료 항목.

## 변경 전 상태

- **호스트·OS:** GA403UM, Windows 11 Home 25H2 26200.9457, OEM 정품 인증 확인.
- **하드웨어:** RAM 32GB, 내부 Micron SSD 1TB 인식.
- **보안:** BitLocker 보호·Secure Boot 켜짐, TPM Ready.
- **설치 상태:** NVIDIA App·Armoury Crate 버전 확인. GPU 드라이버는 nvidia-smi와 장치 정보로 대조.
- **문제 장치:** ACPI PS883508 드라이버 누락 1개. [E10, E11]

## 드라이버와 앱

| 구성 | 확인된 최종 상태 | 판단 |
|---|---|---|
| NVIDIA App / RTX 드라이버 | 11.0.9.251 / 616.92 | 실제 GPU 적용 확인, 재설치하지 않음 |
| Radeon 780M | 32.0.21036.1002 | ASUS 공식 패키지·서명·해시·HW ID 대조 후 적용 |
| ASUS System Control Interface | 3.1.70.0 | 유지 |
| Armoury Crate Control Interface | 1.2.0.2 | 준비물 1.2.0.1로 내리지 않음 |
| Armoury 앱·서비스 / Framework | 6.5.14.0 / 4.2.5.4 | 실제 장비 제어 화면과 업데이트 센터 확인 |
| MyASUS | 4.0.73.0 | 공식 Store 설치 및 진단 실행 |
| Parade HID PS883508 | 1.0.17.0 | 정확한 ACPI 장치에 설치, 문제 장치 0개로 감소 |
| Parade SPB | 1.0.18.0 | HID와 다른 구성으로 구분, 유지 |
| Wi-Fi / Bluetooth | 5.7.0.5115 / 1.1045.0.566 | 실제 장치 적용 유지 |
| Realtek 오디오 / 터치패드 | 6.0.9921.1 / 16.0.0.44 | 실제 버전 확인 |
| Cirrus / Dolby 패키지 | 23.26.47.832 / 10.1031.743.43 | 이미 DriverStore에 존재, 표시 장치 버전 차이만으로 재설치하지 않음 |
| GA403UM Slash / ICM | 20241114 / 1.0.3.0 | 업데이트 후 최신 표시 |
| AURA add-on x86·x64 | 0.0.60 | 처음 요청 뒤에는 0.0.21, 이후 실제 설치 갱신 확인 |
| Smart Display Control | 배포 패키지 2.11.31 | 공식 MSI 설치 종료 코드 0 및 프로세스 확인 |
| Realtek Audio Console | 설치 미완료 | 재부팅 전후 Store 0x803fb005, 반복 중단 |
| BIOS | 310 유지 | 당시 공식 최신과 동일, WU 10.1.2.310 재플래시 보류 |
| SSD 펌웨어 | V8MA000 유지 | 적용 가능한 OEM 공식 업데이트를 확인하지 못해 변경하지 않음 |
| 카메라 확장 | 신규 패키지 미설치 | 10.0.22000.10010의 지원 HW ID가 실제 카메라와 불일치 |

버전 표기 확인:

- Smart Display Control: 배포 패키지 2.11.31 / MSI 제품 2.11.0 / EXE 파일 1.2.0.0.
- Cirrus: 패키지 23.26.47.832 / 기능 드라이버 21.51.46.157.

기존 앱·필수 구성요소는 다음 버전 확인 후 유지. [E10]

| 항목 | 버전·식별 정보 |
|---|---|
| ChatGPT 창 제목의 앱 | 실제 패키지 OpenAI.Codex, 26.915.4065.0 |
| Claude | 2.2553.1.0 |
| WebView2 | 153.0.4234.48 |
| VC++ x86·x64 | 14.42.34438 |

## Windows 업데이트

8개 항목 설치 완료: ResultCode 2 / HResult 0.

- 보안 업데이트: KB5007651, KB890830, KB4052623
- AMD GPIO 2.2.0.134, I2C 1.2.0.126, Crash Defender 25.20.0.4
- 모니터 확장 1.7.0.0, DRTM 1.0.20.0

- **후속 버전 변경:** ASUS Radeon 설치 시 동봉 Crash Defender 25.10.0.4 적용. 강제 다운그레이드 옵션 미사용. 재부팅 후 서비스 실행 중이며 WU에서 25.20.0.4 재제공 없음, 현 상태 유지.
- **최종 재검색:** 현재 BIOS와 같은 펌웨어 항목만 남음. Defender 정의 1.459.287.0 적용. MyASUS·Armoury 업데이트 페이지 최신 표시. [E10–E12]

## SSD

| 수치 | 초기 19:48경 | 재부팅 후 22:03 |
|---|---:|---:|
| 온도 | 39°C | 41°C |
| Available Spare | 100% | 100% |
| Percentage Used | 2% | 2% |
| Media Errors | 0 | 0 |
| Error Log Entries | 0 | 0 |
| Unsafe Shutdowns | 24 | 24 |
| Power On Hours | 1110 | 1112 |

- **자체 진단:** 짧은 검사 Completed without error. 긴 검사·전 구간 쓰기 검사 미실시.
- **비정상 종료:** 누적 24회, 점검 전후 증가 없음.
- **수치 해석:** Windows Wear=0과 달리 직접 조회한 NVMe 사용량은 2%. TemperatureMax=86은 SMART 경고 임계값과 동일해 실제 과열 이력으로 판단하지 않음. [E10–E12]

## Windows·메모리·팬 검사

| 검사 | 결과 |
|---|---|
| DISM 온라인 ScanHealth | 종료 코드 0, 구성 요소 저장소 손상 없음 |
| SFC verifyonly | 종료 코드 0, CBS에서 Verify complete 확인 |
| MyASUS 자동 진단 | 21:55:40 완료, 문제 0 / 제안 2 |
| Windows 오프라인 메모리 진단 | 예약 기록 있음, 완료 결과는 미확인 |

- **SFC:** 콘솔 문자 깨짐으로 CBS 재확인. [SR] 498개 줄의 요약에서 손상 관련 줄 0개. 새 OS에서 RestoreHealth·scannow 수리 미실시.
- **MyASUS:** 어댑터·메모리·Wi-Fi·Bluetooth·SSD·배터리·팬 통과. 제안 2개는 Windows 업데이트 확인과 앱 메모리 사용량 안내. CPU·GPU·시스템 팬의 단계별 회전 증가 확인.
- **오프라인 메모리:** 완료 Results 이벤트 없음, 사용자도 검사 진행 여부 불확실. MyASUS 온라인 검사와 별개로 미확인 처리.
- **복구·덤프 설정:** WinRE Enabled, 페이지 파일 자동 관리, 작은 메모리 덤프. [E10–E13]

## 남아 있는 오류와 경고

재부팅 직후 NVMe 관리 명령 이벤트:

| 종류 | 건수 | 기록 값 |
|---|---:|---|
| Admin Command Error | 1 | OPC 10, SCT 0, SC 2, CmdInfo 127 |
| Admin Command Timeout | 1 | OPC 9, CmdInfo 2 |

별도 I/O 집계 실패 카운터·SSD 매체 오류는 0. 관리 명령 이벤트와 최초 장애의 관련성은 미확정.

| 범위 | 확인 내용 |
|---|---|
| 이번 부팅~22:02 System 로그 | BugCheck·WHEA·Kernel-Power 41 없음 |
| 같은 구간의 경고·이벤트 | BitLocker 24641 2건, WUDFRd 219 2건, USBXHCI Companion 관련 Wdf 경고 |
| 설치 중 앱·서비스 오류 | Parade 추출 래퍼 충돌, 기존 AMD 서비스 종료, Armoury 서비스 앱 충돌 |
| 그래픽 드라이버 변경 후 | 화면 캡처 도구 실패, 재부팅 후 회복 |
| 재부팅 대기 값 | TPM RestartPending=true, CBS·Windows Update=false |
| 기타 | Claude VM 서비스 복구 설정 Access denied, CodexSandboxService 이벤트 |

설치 중 오류와 이후 일상 사용 중 재발 여부는 구분해 기록. [E10–E12]

## 조회 보완

- **Storport:** 표준 권한의 빈 결과는 채널 접근 거부에 따른 것. 첫 UAC 취소 후 두 번째 관리자 조회에서 실제 이벤트 확인, 오류 없음 판단 정정.
- **시간 비교:** Windows PowerShell JSON 날짜를 한국 시각으로 변환해 재부팅 전후 구분.

## 마지막 설정과 남은 확인

- **현상:** Armoury 성능 모드 선택 후에도 Windows 구성표는 Turbo 유지.
- **조치·결과:** Armoury Windows 모드 / Windows 균형 조정 적용 확인. 팬 자동 제어 유지, 수동 팬 곡선·언더볼팅·오버클럭 미적용.

미완료 항목:

- Windows 오프라인 메모리 검사
- 카메라·얼굴 로그인, 스피커·마이크, 실물 Bluetooth 기기 연결
- 핫키와 절전 복귀
- 장시간 CPU·GPU 부하에서의 안정성

추가 부하 검사 없이 일상 사용 재개 결정. 확인된 검사 범위에서 부품 고장 미검출.
