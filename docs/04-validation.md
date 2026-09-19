# 재설치 후 실제 검증

[처음으로](../README.md) · [선별 수치](../evidence/measurements.json)

2026-09-19의 검사 결과입니다. 이전 손상 Windows, 복구 USB, 새 Windows의 기록을 섞지 않았습니다. “장치 오류 없음”과 “사용자가 실제로 영상·소리·로그인을 확인함”도 별도입니다.

## 변경 전 확인

실행 호스트는 GA403UM이었고 Windows 11 Home 25H2 26200.9457의 OEM 정품 인증을 확인했습니다. CPU·GPU·32GB 메모리·내부 Micron SSD를 식별했습니다. 암호화는 보호 On/100%, TPM Ready, Secure Boot On이었습니다. 복구 키·제품 키·계정 토큰은 보고서에 출력하지 않았습니다.

NVIDIA App과 Armoury Crate는 이미 설치돼 있었습니다. 앱 설치 자체를 GPU 드라이버 적용 완료로 간주하지 않고 nvidia-smi와 실제 장치 드라이버를 확인했습니다. 초기 문제 장치는 ACPI PS883508의 드라이버 누락 1개였습니다. [E10, E11]

## 설치·유지·보류한 구성

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

Smart Display Control의 배포 버전과 MSI 제품 버전 2.11.0, EXE 파일 버전 1.2.0.0은 서로 달랐습니다. 숫자만 비교해 설치 실패라고 판단하지 않았습니다. Cirrus 기능 드라이버의 21.51.46.157도 패키지 버전과 다릅니다.

OpenAI 앱은 창 제목이 ChatGPT였으나 패키지는 OpenAI.Codex 26.915.4065.0으로 확인했습니다. Claude는 2.2553.1.0, WebView2는 153.0.4234.48, VC++ x86/x64는 14.42.34438이었습니다. 앱 명칭 차이 때문에 처음부터 다시 설치하지 않았습니다. [E10]

## Windows 업데이트와 예상 밖의 버전 변화

보안 업데이트 KB5007651, KB890830, KB4052623 및 AMD GPIO 2.2.0.134, I2C 1.2.0.126, Crash Defender 25.20.0.4, 모니터 확장 1.7.0.0, DRTM 1.0.20.0의 총 8개 업데이트는 ResultCode 2/HResult 0으로 완료됐습니다.

이후 ASUS Radeon 패키지의 정상 PnP 설치 과정에서 Crash Defender가 동봉 버전 25.10.0.4로 바뀌었습니다. 강제 다운그레이드 옵션은 쓰지 않았지만 실제 버전 하락은 관측됐으므로 기록했습니다. 재부팅 후 Windows Update는 25.20을 다시 제공하지 않았고 서비스는 실행 중이었습니다. 숫자만 보고 강제로 재변경하지 않았습니다.

최종 Windows Update 재검색은 성공했고, 현재 BIOS와 같은 펌웨어 항목만 남았습니다. Defender 정의 1.459.287.0 적용을 확인했습니다. MyASUS와 Armoury 업데이트 페이지도 최신 상태였습니다. [E10–E12]

## SSD 검사

| 수치 | 초기 19:48경 | 재부팅 후 22:03 |
|---|---:|---:|
| 온도 | 39°C | 41°C |
| Available Spare | 100% | 100% |
| Percentage Used | 2% | 2% |
| Media Errors | 0 | 0 |
| Error Log Entries | 0 | 0 |
| Unsafe Shutdowns | 24 | 24 |
| Power On Hours | 1110 | 1112 |

짧은 NVMe 자체 진단은 Completed without error였습니다. 긴 자체 진단이나 전 구간 쓰기 검사는 수행하지 않았습니다. 수명 사용량은 장치가 보고한 지표이며 노트북 전체의 남은 수명을 뜻하지 않습니다. 비정상 종료 24회는 누적값이고, 이번 장애를 일으킨 사건 24개를 특정한 것이 아닙니다.

Windows 기본 신뢰성 값의 Wear=0보다 직접 읽은 NVMe 사용량 2%를 우선했습니다. 기본 TemperatureMax=86은 SMART 경고 임계값과 같았으므로 실제 86°C 과열 이력으로 단정하지 않았습니다. [E10–E12]

## 메모리·시스템·팬

- DISM 온라인 ScanHealth: 종료 코드 0, 구성 요소 저장소 손상 없음. RestoreHealth는 실행하지 않음.
- SFC verifyonly: 종료 코드 0. 콘솔 인코딩이 깨져 CBS 해당 구간 498개 [SR] 줄을 확인했고, 저장한 요약에서 손상 관련 줄 0개와 Verify complete 확인. 새 OS에서 scannow 수리는 실행하지 않음.
- MyASUS 사용자 지정 자동 진단 21:55:40: 문제 0, 제안 2. 어댑터·메모리·Wi-Fi·Bluetooth·SSD·배터리·팬 통과 표시.
- 두 제안은 Windows 업데이트 확인과 앱 메모리 사용량 안내. 부품 고장 판정이 아니었음.
- CPU·GPU·시스템 팬의 단계별 회전 반응 확인. 검사 중 높은 팬 속도를 평상시 소음이나 고장 증거로 취급하지 않음.
- Windows 메모리 진단 예약은 확인했지만 Results 이벤트 없음. 사용자가 완료했을 수도 있다고 말했다가 불확실하다고 정정했으므로 **미확인** 유지.
- WinRE Enabled, 페이지 파일 자동 관리, 작은 메모리 덤프 설정 확인. 이를 임의로 변경하지 않음.

MyASUS 온라인 메모리 검사와 재부팅 중 오프라인 메모리 검사를 동일한 검사로 세지 않았습니다. [E10–E13]

## 남아 있는 이벤트와 도구 문제

재부팅 직후 NVMe Admin Command Error 1건(OPC 10, SCT 0, SC 2, CmdInfo 127), Admin Command Timeout 1건(OPC 9, CmdInfo 2)이 기록됐습니다. 별도 I/O 집계의 실패 카운터는 0이었습니다. 관리 명령 이벤트와 SSD 매체 오류를 같은 것으로 계산하지 않았습니다.

22:02까지의 이번 부팅 System 조회에서 BugCheck/WHEA/Kernel-Power 41은 없었습니다. BitLocker 24641 두 건, WUDFRd 219 두 건, USBXHCI Companion 관련 Wdf 경고는 있었습니다. 현재 장치 열거가 정상이라고 이 경고의 원인이 규명된 것은 아닙니다.

설치 중에는 Parade 추출 래퍼 충돌, 기존 AMD 서비스 종료, Armoury 서비스 앱 충돌도 관찰했습니다. 그래픽 교체 뒤 화면 캡처 도구가 실패했으나 재부팅 뒤에는 회복됐습니다. 이를 자동으로 최초 장애의 재발로 연결하지 않았습니다.

표준 권한에서는 Storport 결과가 비어 보여 한때 새 오류가 없다고 설명했으나, 채널 접근 거부를 확인하고 철회했습니다. 최초 UAC는 취소됐고 두 번째 UAC 후 관리자 조회로 실제 이벤트를 확인했습니다. Windows PowerShell JSON 날짜는 UTC/KST 변환 후 비교했습니다.

TPM RestartPending은 true였지만 CBS/Windows Update의 재부팅 대기는 false였습니다. 서로 다른 속성을 하나로 단정하지 않았습니다. Claude VM 서비스의 복구 설정 Access denied와 CodexSandboxService 이벤트도 기록했으며, 데스크톱 앱 전체 실패나 재설치 필요로 확대하지 않았습니다. [E10–E12]

## 최종 사용 설정과 검사 범위

Armoury 성능 모드를 선택했을 때 Windows 구성표가 Turbo로 남는 차이를 관찰했습니다. 최종적으로 Armoury Windows 모드를 선택하고 실제 활성 Windows 구성표가 균형 조정인 것을 확인했습니다. 원인이 확인되지 않은 표시 차이는 기록하고, 수동 팬 곡선·언더볼팅·오버클럭은 적용하지 않았습니다.

카메라/얼굴 로그인·스피커/마이크·실물 Bluetooth 연결·핫키·절전 복귀의 전체 실제 동작과 장시간 CPU/GPU 안정성은 완료로 처리하지 않았습니다. 추가 부하 검사는 사용자의 최종 선택에 따라 진행하지 않았습니다.

**결론은 검사 범위에서 양호하고 사용 환경을 회복했다는 것입니다. 모든 부품 정상이나 최초 원인 제거를 인증한 것은 아닙니다.**
