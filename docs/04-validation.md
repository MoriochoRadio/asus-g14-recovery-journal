# 재설치 후 점검

[처음으로](../README.md) · [검사 수치 JSON](../evidence/measurements.json)

2026년 9월 19일, 새 Windows에서 확인한 버전과 검사 결과다. 장치가 인식되는지 확인한 항목과 실제 사용까지 시험한 항목을 구분했다.

## 점검을 시작했을 때

GA403UM에서 Windows 11 Home 25H2 26200.9457과 OEM 정품 인증을 확인했다. 메모리는 32GB, SSD는 내부 Micron 1TB로 인식됐다. BitLocker 보호와 Secure Boot는 켜져 있었고 TPM은 Ready였다.

이미 설치한 NVIDIA App과 Armoury Crate의 버전부터 확인했다. GPU 드라이버는 nvidia-smi와 장치 정보로 대조했다. 장치 관리자에는 ACPI PS883508의 드라이버 누락 1개가 있었다. [E10, E11]

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

버전 숫자가 다르게 표시돼 주의해서 본 항목도 있었다. Smart Display Control은 배포 패키지 2.11.31, MSI 제품 버전 2.11.0, EXE 파일 버전 1.2.0.0이었다. Cirrus도 패키지는 23.26.47.832였지만 기능 드라이버에는 21.51.46.157이 표시됐다.

평소 쓰던 앱도 확인했다. ChatGPT라는 창 제목의 앱은 실제 패키지 이름이 OpenAI.Codex였고 버전은 26.915.4065.0이었다. Claude는 2.2553.1.0, WebView2는 153.0.4234.48, VC++ x86/x64는 14.42.34438이었다. 기존 설치를 유지했다. [E10]

## Windows 업데이트

다음 8개 항목은 ResultCode 2/HResult 0으로 설치가 완료됐다.

- 보안 업데이트: KB5007651, KB890830, KB4052623
- AMD GPIO 2.2.0.134, I2C 1.2.0.126, Crash Defender 25.20.0.4
- 모니터 확장 1.7.0.0, DRTM 1.0.20.0

이후 ASUS Radeon 패키지를 설치하면서 동봉된 Crash Defender 25.10.0.4로 바뀌었다. 강제 다운그레이드 옵션을 쓴 것은 아니지만 실제 버전은 내려갔다. 재부팅 후 서비스는 실행 중이었고 Windows Update에서도 25.20을 다시 제공하지 않아 그대로 두었다.

최종 재검색에서는 현재 BIOS와 같은 펌웨어 항목만 남았다. Defender 정의는 1.459.287.0이 적용됐고, MyASUS와 Armoury 업데이트 페이지에도 최신으로 표시됐다. [E10–E12]

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

짧은 NVMe 자체 진단 결과는 **Completed without error**였다. 비정상 종료 횟수 24회는 누적값이며, 이번 점검 전후로 늘지 않았다. 긴 자체 진단이나 전 구간 쓰기 검사는 하지 않았다.

Windows 기본 신뢰성 값에는 Wear=0이 표시됐지만 직접 읽은 NVMe 사용량은 2%였다. TemperatureMax=86은 SMART 경고 임계값과 같아서 실제 과열 이력으로 세지 않았다. [E10–E12]

## Windows·메모리·팬 검사

| 검사 | 결과 |
|---|---|
| DISM 온라인 ScanHealth | 종료 코드 0, 구성 요소 저장소 손상 없음 |
| SFC verifyonly | 종료 코드 0, CBS에서 Verify complete 확인 |
| MyASUS 자동 진단 | 21:55:40 완료, 문제 0 / 제안 2 |
| Windows 오프라인 메모리 진단 | 예약 기록 있음, 완료 결과는 미확인 |

SFC 콘솔의 한글이 깨져 CBS의 해당 구간을 따로 확인했다. [SR] 498개 줄을 정리한 요약에서 손상 관련 줄은 0개였다. 새 OS에서 RestoreHealth나 scannow 수리는 하지 않았다.

MyASUS에서는 어댑터·메모리·Wi-Fi·Bluetooth·SSD·배터리·팬이 통과로 표시됐다. 두 제안은 Windows 업데이트 확인과 앱 메모리 사용량 안내였다. 팬 검사 중에는 CPU·GPU·시스템 팬이 단계별로 속도를 올리는 것을 확인했다.

Windows 메모리 진단은 재부팅 중 완료됐는지 기억이 확실하지 않았다. Results 이벤트도 없어 통과로 기록하지 않았다. MyASUS의 온라인 메모리 검사와는 별개다.

WinRE는 Enabled, 페이지 파일은 자동 관리, 메모리 덤프는 작은 덤프로 설정돼 있었다. [E10–E13]

## 남아 있는 오류와 경고

재부팅 직후 다음 NVMe 관리 명령 이벤트가 남았다.

| 종류 | 건수 | 기록 값 |
|---|---:|---|
| Admin Command Error | 1 | OPC 10, SCT 0, SC 2, CmdInfo 127 |
| Admin Command Timeout | 1 | OPC 9, CmdInfo 2 |

별도 I/O 집계의 실패 카운터와 SSD 매체 오류는 0이었다. 이 관리 명령 이벤트가 최초 장애와 관련 있는지는 아직 알 수 없다.

이번 부팅부터 22:02까지의 System 로그에는 BugCheck/WHEA/Kernel-Power 41이 없었다. BitLocker 24641 두 건, WUDFRd 219 두 건, USBXHCI Companion 관련 Wdf 경고는 있었다.

설치 과정에서도 오류가 몇 차례 있었다. Parade 추출 래퍼가 충돌했고, 기존 AMD 서비스가 종료됐으며, Armoury 서비스 앱 충돌도 기록됐다. 그래픽 드라이버를 바꾼 뒤에는 화면 캡처 도구가 실패했지만 재부팅 후 회복됐다. 설치 중 오류와 평소 사용 중 재발 여부를 따로 기록했다.

TPM RestartPending은 true, CBS/Windows Update 재부팅 대기는 false였다. Claude VM 서비스의 복구 설정 Access denied와 CodexSandboxService 이벤트도 남아 있었다. [E10–E12]

## 조회하면서 바로잡은 부분

표준 권한으로 읽은 Storport 결과가 비어 있어 새 오류가 없는 것으로 생각했다. 나중에 채널 접근 거부를 확인했다. 첫 UAC 요청은 취소됐고, 두 번째 관리자 조회에서 실제 이벤트를 읽을 수 있었다.

시간 비교도 주의가 필요했다. Windows PowerShell이 저장한 JSON 날짜를 한국 시각으로 변환한 뒤 재부팅 전후를 비교했다.

## 마지막 설정과 남은 확인

Armoury에서 성능 모드를 선택해도 Windows 구성표에는 Turbo가 남는 차이가 있었다. 최종적으로 **Armoury Windows 모드 / Windows 균형 조정**을 적용하고 확인했다. 팬은 자동 제어를 유지했고 수동 팬 곡선·언더볼팅·오버클럭은 적용하지 않았다.

다음 항목은 충분히 시험하지 못했다.

- Windows 오프라인 메모리 검사
- 카메라·얼굴 로그인, 스피커·마이크, 실물 Bluetooth 기기 연결
- 핫키와 절전 복귀
- 장시간 CPU·GPU 부하에서의 안정성

추가 부하 검사는 하지 않기로 했다. 새 Windows에서 사용 가능한 상태로 돌아왔고, 현재 검사에서 부품 고장은 확인되지 않았다.
