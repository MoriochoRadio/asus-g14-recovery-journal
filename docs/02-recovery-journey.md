# 복구 과정

[처음으로](../README.md) · [타임라인](01-timeline.md)

## 1. 부팅 불능 및 SSD 이미지 확보

- **현상:** 사용 중 오류 화면이 0%에서 정지. 재부팅 후 BIOS 진입. SSD는 인식됐으나 Windows 부팅 항목과 설치 환경의 파티션 인식에 문제 발생.
- **시도:** SystemRescue로 부팅해 ddrescue로 SSD 전체 이미지 확보.
- **결과:** Finished, rescued 100%, read errors 0. 이미지 확보 후 복구 진행. 이미지에는 기존 논리 구조 손상도 포함. [E01–E03]

## 2. GPT 복원

- **현상:** 주 GPT·보호 MBR 손상. 이미지의 앞쪽 1MiB는 디스크 서명 4바이트를 제외하고 0으로 확인. 백업 GPT는 정상.
- **시도:** 고장 당일 Windows 로그의 6개 파티션과 백업 GPT의 위치·종류·GUID·속성을 대조한 뒤 실제 SSD에 복원.
- **결과:** 유효한 GPT·보호 MBR 인식, CRC 경고 해소. Windows 자동 복구 화면까지 진입했으나 정상 부팅은 실패. [E02, E03, E05]

## 3. NTFS 수리

- **현상:** BitLocker 잠금 해제 상태에서도 디스크 구조 오류로 파일 접근 불가.
- **시도:** CHKDSK로 MFT mirror, Attribute Definition Table, Boot File, bitmap, USN 관련 구조 수리.
- **결과:** NTFS 인식과 디렉터리·파일 접근 회복. Windows 부팅은 계속 실패했으며, 자동 재시작을 중지한 화면에서 **BAD_SYSTEM_CONFIG_INFO(0x74)** 확인. [E01, E05]

## 4. 레지스트리 사본 검사

- **현상:** 사용 가능한 복원 지점 없음, RegBack 비어 있음. SYSTEM 헤더 시퀀스 360426/360425 불일치.
- **시도:** SYSTEM·SOFTWARE 사본 분석. YARP 구조 검사와 주요 키 조회, SYSTEM.LOG1/LOG2를 반영한 별도 후보 생성. 정상 PC와 노트북 WinRE에서 로드 검사.
- **결과:** YARP 검사 통과. 정상 PC에서는 대조군까지 실패했으나, WinRE에서는 대조군·원본+로그 사본·후보 SYSTEM·SOFTWARE 모두 로드·조회·언로드 성공.
- **적용 여부:** 원본과 로그 사이의 시퀀스 간격, 검사 중 로그 재적용 가능성이 있어 후보를 SSD에 덮어쓰지 않음. 사본 로드 성공만으로 부팅 가능 여부는 확인되지 않음.
- **검사 보완:** WinRE에 findstr가 없어 요약 명령 실패. 결과 파일을 직접 열어 앞선 검사 성공 확인. [E06]

## 5. 오프라인 시스템 검사

- **현상:** 레지스트리 사본 검사 이후에도 기존 Windows 부팅 불가.
- **시도:** BCD 경로 확인, 오프라인 SFC 및 DISM ScanHealth 실행.
- **결과:** BCD는 Windows 부팅 로더를 가리킴. SFC는 작업 수행 불가로 중단. DISM은 0xd000015c로 중단됐으며, 로그 82·84행에서 SAM 하이브 로드 실패 확인.
- **남은 사항:** 최초 손상 원인 미확정. 후속 조회에서 MEMORY.DMP를 찾지 못했으며, 확인된 Minidump는 이전 날짜의 기록. [E03, E07]

## 6. ASUS 복구 경로 시도

- **현상:** 파티션·파일 접근은 회복됐으나 기존 Windows 복구 미완료.
- **시도:** 자료 보존 후 재설치 결정. ASUS Cloud Recovery와 공식 MyASUS in WinRE USB 사용.
- **결과:** Cloud Recovery는 다운로드만 확인, OS 복원 완료는 미확인. 복구 USB에서는 Wi-Fi 연결 중 **DRIVER_IRQL_NOT_LESS_OR_EQUAL / nwifi.sys** 발생.
- **후속 조치:** 자동 재부팅 후 기존 Windows의 0x74·BitLocker 화면으로 복귀한 것으로 관찰. Microsoft 공식 설치 USB로 전환. 복구 USB의 0xD1과 기존 Windows의 0x74는 별도 환경에서 발생한 오류. [E01, E08]

## 7. Microsoft 설치 USB 제작 및 검증

- **현상:** Media Creation Tool 1차 시도에서 약 33% 이후 창 종료. 완료 기록과 종료 원인 미확인.
- **시도:** 2차 제작 후 파일 해시·서명·이미지 정보 검사. USB에 있던 진단 자료는 사전 보존.
- **결과:** 9월 19일 18:07:49 MediaCreationSuccess, 종료 코드 0. 준비 원본과 USB 사본의 1,069개 파일 SHA-256 일치. 주요 실행·EFI 부팅 파일의 Microsoft 서명과 이미지 언어·에디션·빌드 확인.
- **검증 범위:** 분할 SWM은 메타데이터·크기 확인. 원본 ESD와 바이트 단위 비교는 미실시. [E09]

## 8. Windows 새 설치

- **시도:** 내부 1TB SSD와 USB를 구별한 뒤 SSD의 기존 파티션 삭제 및 Windows 새 설치. 초기 설정에서 준비한 공식 Wi-Fi 드라이버 사용.
- **결과:** Windows 로그인 완료. 이후 로컬 조회에서 설치 시각 2026-09-19 18:32:23 확인. [E09, E10]

## 9. 드라이버 정리 및 재부팅 후 점검

- **현상:** NVIDIA App·Armoury Crate·사용 앱 설치 완료 상태. 장치 관리자 문제 항목 1개.
- **시도:** 현재 버전과 실제 드라이버 적용 상태 확인. 장치 ID가 맞는 공식 패키지 선별 설치, Windows 업데이트, 시스템·SSD·MyASUS 검사 수행. 재부팅 전 진행 상황 저장 후 재수집.
- **결과:** 문제 장치 0개. Windows 시스템 검사 완료, SSD 짧은 자체 검사 통과, MyASUS 문제 0개. NVMe 관리 명령 이벤트는 별도로 확인.
- **최종 결정:** 추가 부하 검사 없이 일상 사용 재개. 오프라인 메모리 검사와 일부 실제 기능 검증은 미완료로 기록. [E10–E14]

세부 버전과 검사 범위: [재설치 후 점검](04-validation.md).
