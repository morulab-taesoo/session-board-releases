# 세션 진행 대시보드 (Session Board)

Claude 데스크톱 앱(Code 탭)에서 여러 세션에 일을 시켰을 때, 세션마다 **지금 몇 번째 단계인지·걸린 시간과 예상 시간·백그라운드 작업이 살아 있는지·누가 내 답을 기다리는지**를 한 창에서 보여 줘요. "끝났어?" 라고 묻지 않아도 돼요.

- 항상 위에 뜨는 **미니 창**(구역: 봐야 할 것 · 일하는 중 · 쉬는 중 · 끝남), 큰 창, 트레이 숫자 배지
- 줄을 누르면 Claude 앱의 그 세션으로 바로 이동
- 예상 시간을 넘긴 단계·답을 기다리는 세션은 깜빡이는 `!` 로
- 다크 모드, 하트비트 캐릭터(대시보드가 살아 있는지)

Windows 10/11 · Claude 데스크톱 앱 전용 · 화면 글은 한국어예요.

## 설치

1. **대시보드**: [최신 릴리스](https://github.com/morulab-taesoo/session-board-releases/releases/latest)에서 `SessionBoard-Setup-<버전>.exe` 를 받아 실행해요(관리자 권한 필요 없음). 서명이 없어서 SmartScreen 경고가 뜨면 '추가 정보 → 실행'.
2. **훅 플러그인**(권장): 세션이 작업 목록을 놓치지 않게 붙잡고, 예상 시간을 넘기면 중간 점검·재계산을 하게 해요.
   ```
   claude plugin marketplace add morulab-taesoo/session-board-releases
   claude plugin install session-board@session-board
   ```
   그 뒤 Claude 앱 세션에서 `/reload-plugins`(또는 앱 다시 시작). 플러그인이 없으면 대시보드에 주황 안내가 떠요.

대시보드는 모드 런처에서도 설치할 수 있어요.

## 세션이 진행을 잘 보이게 하려면

플러그인이 세션 시작 때 알려 주는 규칙이에요(직접 지켜도 돼요):
- 작업 목록 단계 이름 끝에 예상 시간을 `(~30분)`처럼 적기
- 단계를 마칠 때마다 넘기기, 예상을 넘기면 중간 점검하고 `(~50분, 재계산)`처럼 다시 적기
- 오래 걸리는 명령은 백그라운드로 + 로그 파일로, 기다리며 쉴 땐 예상 끝 시각 알람(`sleep`)

## 개인정보·한계

- 대화 기록은 **이 PC 안에서만** 읽어요. 밖으로 보내는 건 새 버전 확인(GitHub)뿐이에요.
- Claude 데스크톱 앱의 내부 파일 형식을 읽어요. 앱이 업데이트되면 일부가 안 보일 수 있어요(새 버전에서 맞춰요).

## 지우기

설정 → 앱에서 '세션 진행 대시보드' 제거. 플러그인은 `claude plugin uninstall session-board@session-board`.

## 라이선스 고지

화면은 [Qt for Python (PySide6)](https://www.qt.io/qt-for-python)(LGPLv3)를 고치지 않고 동적으로 써요. 프로세스 정보는 [psutil](https://github.com/giampaolo/psutil)(BSD-3)을 써요.
