GODDESS NETWORK · '당선 확정' 알림 오버레이 (call_alert.html, 1920×1080, 배경 투명)

[XSplit] 모든 장면의 맨 위 레이어에 '웹페이지' 소스로 추가 → 크기 1920×1080. 평소엔 아무것도 안 보이고,
  새 콜이 들어오면 공화 약 7.4초(금빛 플래시·광선·꽃가루) / 민주·무소속 약 6초(차분한 파란 패널) 표시 후 사라짐.
  여러 콜이 한꺼번에 들어오면 콜 시각 순으로 하나씩 차례로 표시(큐).
[주소] 보드와 같은 토픽·키를 그대로 붙이면 됨 (이 파일에는 비밀값 없음):
  call_alert.html?live=ntfy&topic=<보드 토픽>[&api=소유자/저장소]#k=<보드 키>
  파일 모드: call_alert.html (같은 폴더 data.json/data.js — call.py 가 저장할 때마다 미러, BOARD_DATA_MIRROR 파일 덕분)
[규칙] 처음 열 때 이미 있는 콜은 알리지 않음 → 그 뒤 새로 생긴 콜(또는 승자 정정)만 알림. 서명 틀린 메시지는 무시.
  (예외: 페이지를 연 직후 보낸 첫 라이브 메시지는 미러 data.json 과 비교해 새 콜만 알림, 4개 넘으면 무시)
  예시 데이터면 '예시 · 실제 결과 아님' 표시.
[옵션] &noflash=1 플래시·꽃가루·광선 끔   &static=1 모든 애니메이션 끔   &interval=3 파일 모드 갱신 주기(초)
[테스트] &demo=1 네트워크 없이 예시 콜 반복(공화 탈환 → 민주 → 공화 수성 → 사진 없는 공화)   &demo=R 공화 콜만
[사진] 공화 승리 + assets/sen_XX.png 있는 6곳(ME·MI·OH·IA·NC·GA)은 사진, 나머지/민주 승리는 정당 엠블럼.
[검증] python3 shot.py  (가짜 SSE 서버, 테스트 키만 사용, ntfy.sh 로 아무것도 안 보냄)
  미리보기: screenshots/call_alert_R_예시.mp4 / .gif, 정지 화면 alert_*_예시.png (배경은 상원 카드 장면 예시)
[인장] 공화 당선 = 사진 오른쪽 아래에 금빛 인장이 '쾅' 찍힘(패널 흔들림·금가루·플래시). 민주·무소속은 인장 없이 차분한 파란 배지.

── 하원 주요 지역구 (2026-10-23 추가) ──
· NY-17 MI-07 NJ-07 PA-08 PA-07 NC-01 콜도 알림: '뉴욕 17선거구 하원 [NY-17]' + 공화 승리 때 후보 사진(assets/hou_*.png).
  데이터: data.json 의 house_races(선택 필드) 또는 라이브 c 의 같은 키. house_races 가 없는 옛 data.json 이어도 내장 META 로 동작.
· &demo=1 순서에 NC-01 공화 탈환 추가, &demo=house = 하원 콜만(NC-01 R → NJ-07 R → PA-07 D).
· 테스트: python3 shot_house.py → screenshots/alert_HOUSE_R_예시.png, alert_HOUSE_D_예시.png, call_alert_HOUSE_R_예시.mp4/.gif

── 효과음 sting (2026-10-31 추가) ──
· 알림이 화면에 나타나는 순간 자동 재생:  상원 콜 → sfx/sting_senate.mp3 / 하원 콜 → sfx/sting_house.mp3
  (주지사 콜은 상원 소리를 사용. 끄려면 &govsfx=0.  정정/취소(uncall)는 알림도 소리도 없음)
· 파일 위치: call_alert.html 과 같은 폴더의 sfx/ (상대경로) → 저장소에 scenes/call_alert/sfx/ 로 같이 올려야 소리가 납니다.
· 새 옵션
    &nosfx          효과음 끄기 (화면 알림만)
    &sfxvol=0~1     음량 (기본 0.9)   예) &sfxvol=0.6   (0 이면 무음)
    &sfxfull        알림이 사라진 뒤에도 끝까지 재생 (기본: 파일이 7~12초라서 알림 퇴장에 맞춰 0.6초 페이드아웃)
    &govsfx=0       주지사 콜은 무음
· 다음 알림이 바로 이어지면 앞 소리는 끊고 새 소리로 교체(겹치지 않음).
· 테스트: &demo=1 / &demo=R / &demo=house 모두 알림과 함께 맞는 소리가 납니다 (소리 확인용: 데모 주소에 &sfxvol=0.5 등).
· 자동재생: XSplit 웹페이지 소스(CEF)는 보통 허용. 일반 브라우저(크롬 등)에서 열었을 때 소리가 안 나면 페이지를 한 번 클릭하거나
  크롬 사이트 설정에서 '소리 허용'. 재생이 막혀도 오류 없이 알림 화면만 정상 표시됩니다.
· 진단: 개발자도구 콘솔에 '[sfx] play SEN sfx/sting_senate.mp3 vol=0.90 race=MI-SEN' 처럼 재생 기록이 남습니다.
· 소리 교체: sfx/ 안의 같은 이름 mp3 를 덮어쓰기.
