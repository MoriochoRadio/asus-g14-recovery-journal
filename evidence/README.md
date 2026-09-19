# 참고 기록과 공식 문서

[처음으로](../README.md) · [선별 검사 수치](measurements.json)

본문 E 번호별 근거 자료 목록. 원본은 별도 보관하며 파일 이름과 확인 범위만 공개.

| ID | 자료 | 내용 |
|---|---|---|
| E01 | ASUS_G14_인수인계.md | 사건 전체 순서와 재설치 전까지의 인수인계 |
| E02 | Windows로그_분석결과.md | 과거 이벤트·WER·덤프 분석 범위, NVMe 이력, 파티션 대조 |
| E03 | 최초원인_조사범위와한계.md | SAM 실패 지점, 원인 미확정 이유 |
| E04 | Windows_Hello_조사결과.md | 9월 초 인증 증상과 이후 정상 읽기 기록, 이전 상담 검토 |
| E05 | gpt-repair-result.json, partition-log-comparison.json, CHKDSK 결과 기록 | GPT 복원과 파일시스템 수리의 관측 |
| E06 | 레지스트리_검사결과.md | YARP 후보, 대조군, WinRE 사본 로드, SSD 미적용 |
| E07 | DISM-scan.log 82·84행 및 오프라인 SFC/BCD 결과 | 기존 OS의 SAM 로드 실패와 검사 중단 |
| E08 | cloud-recovery-wifi-crash/조사결과.md | ASUS USB Wi-Fi 충돌과 기존 Windows 오류의 분리 |
| E09 | Windows_USB_검증완료.md, installers/README.md | Microsoft USB 제작·서명·해시와 공식 WLAN 준비 |
| E10 | 진행기록.md | 새 Windows 설치·변경 전후, 버전·진단·정정 |
| E11 | 20260919-194548-before, ssd-smart-before.json | 실제 GA403UM 변경 전 측정 |
| E12 | 20260919-220241-after-reboot 및 22:03 SSD·Storport JSON | 관리자 권한 재부팅 후 검사 |
| E13 | sfc-current-summary.json, CBS 발췌 | 새 OS SFC 종료 코드·검증 완료 |
| E14 | 재설치 후 남긴 대화와 메모 | 메모리 기억 정정, 보증·검사 부담 논의, 부하 검사 중단·공개 기록 선택 |

## 정리 방법

- 인수인계·조사 기록·검사 결과를 바탕으로 작성.
- 초기 복구 수치는 당시 분석 기록 기준. 문서 작성 중 전체 SSD 이미지·덤프 재분석은 미실시.
- 후속 확인 결과와 앞선 기록이 다른 항목은 정정 반영.

로그 분석과 문서 정리에는 에이전트의 도움도 받았다.

## 공식 자료

오류 코드·저장장치 구조·설치 파일 출처 확인에 사용한 문서.

- [Microsoft: 0x74 BAD_SYSTEM_CONFIG_INFO](https://learn.microsoft.com/en-us/windows-hardware/drivers/debugger/bug-check-0x74--bad-system-config-info)
- [Microsoft: 0xD1 DRIVER_IRQL_NOT_LESS_OR_EQUAL](https://learn.microsoft.com/en-us/windows-hardware/drivers/debugger/bug-check-0xd1--driver-irql-not-less-or-equal)
- [Microsoft: NTSTATUS 정의](https://learn.microsoft.com/en-us/openspecs/windows_protocols/ms-erref/596a1078-e883-4972-9bbc-49e60bebca55)
- [Microsoft: HRESULT_FROM_NT](https://learn.microsoft.com/en-us/windows/win32/api/winerror/nf-winerror-hresult_from_nt)
- [UEFI: GPT 구조](https://uefi.org/specs/UEFI/2.10/05_GUID_Partition_Table_Format.html)
- [Microsoft: Windows 11 설치 미디어](https://www.microsoft.com/ko-kr/software-download/windows11)
- [ASUS: GA403UM 드라이버](https://www.asus.com/us/supportonly/ga403um/helpdesk_download/)
- [ASUS: GA403UM BIOS](https://www.asus.com/us/supportonly/ga403um/helpdesk_bios/)
- [ASUS: Armoury Crate 안내](https://www.asus.com/support/FAQ/1043747)
- [ASUS: UEFI 진단](https://www.asus.com/us/support/faq/1049279/)
- [NVIDIA: 2026-09-09 드라이버 발표](https://www.nvidia.com/en-sg/geforce/news/wardogs-aniimo-007-first-light-path-tracing-geforce-game-ready-driver/)
- [ASUS 한국: 노트북 보증 안내](https://www.asus.com/kr/support/article/1150/)
- [ASUS 한국: 보증 상태 확인](https://www.asus.com/kr/support/faq/1041323/)

버전·검사 기준일: 2026-09-19.
