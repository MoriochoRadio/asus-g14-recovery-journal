# 근거 목록

[처음으로](../README.md) · [선별 검사 수치](measurements.json)

이 목록의 E 번호는 공개 문서의 주장과 로컬 근거를 연결합니다. 경로는 공개 저장소 안의 파일 링크가 아니라 원자료를 식별하는 이름입니다. 개인 식별자가 포함될 수 있어 원본은 공개하지 않습니다.

| ID | 로컬 원자료 또는 기록 | 주로 뒷받침하는 내용 |
|---|---|---|
| E01 | ASUS_G14_인수인계.md | 사건 전체 순서, 사용자 보고와 현재 요청의 경계 |
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
| E14 | 현재 작업의 후속 사용자 대화 | 메모리 기억 정정, 보증·검사 부담 논의, 부하 검사 중단·공개 기록 선택 |

## 원자료 접근 범위

이번 문서화에서 로컬 인수인계, 위의 조사 문서, 현재 검사 요약과 일부 원본 로그 발췌를 읽었습니다. 다른 장비에 보존된 전체 SSD 이미지, 모든 과거 대화·덤프·이벤트 파일을 이번에 다시 분석하지 않았습니다.

과거 수치는 해당 조사 기록에 근거한 것으로, 이번 작성자가 원자료 전부를 새로 전수 분석한 것처럼 표현하지 않았습니다. 과거 보고서의 시점과 현재 상태가 다르면 이후 검증·사용자 정정을 우선했습니다.

## 공식 자료

다음 자료는 개념과 설치 출처를 확인하는 데 사용했습니다. 제품 하나의 실제 고장 여부는 공식 문서만으로 판단할 수 없습니다.

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

이 저장소는 제품·소프트웨어의 2026-09-19 관측 기록입니다. 미래에 해당 링크의 버전이나 안내가 변경돼도 당시 설치 결과를 소급해 바꾸지 않습니다.
