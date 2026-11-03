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

── 베가스 '당선' 배너 + 다수당 확정 배너 (2026-11-03 추가) ──
· 트럼프 대통령 지지 후보가 공화당으로 당선(콜)되면: 평소 콜 알림이 끝난 뒤 '트럼프 대통령 지지 후보 당선' 베가스 배너가 약 5.6초 재생
  (확대 팝인 → 테두리 54개 전구가 시계 방향으로 도는 점등+깜빡임 → 금빛 스윕 → 골드 코인 폭죽(canvas, 중력·회전·바닥 튕김) → 페이드아웃).
  큐 순서 유지: [콜 알림 → 베가스 배너] 순으로 하나씩 나오고, 그 사이 다른 콜이 들어와도 뒤에 줄을 섭니다.
  민주 당선·미지지 후보·정정(uncall)·시작할 때 기준선 로드에서는 나오지 않습니다.
· 지지 여부 판정(우선순위): ① races[i].endorsed true/false (레이스별 데이터 필드, 있으면 최우선)  ② &unendorsed=ID,ID 로 제외
  ③ 내장 목록 ENDORSED_LIST (call_alert.html 안, 2026-11-03 지지 명단 endorse_list_20261103.txt 에서 생성, 상원 XX-SEN·주지사 XX-GOV·하원 XX-NN·단일구 XX-AL, 약 370건)
  ④ data 최상위 endorsed:["TX-SEN",…] ⑤ &endorsed=ID,ID 로 추가.
  명단이 바뀌면: python3 ../../win_banners/tools/gen_endorsed.py (새 명단 → JSON) 후 ENDORSED_LIST 를 교체(또는 patch_call_alert.py 재실행).
· 다수당 확정 배너(공화/민주 × 상원/하원 4종, 각 1회): 금빛 스윕 + 팝인, 공화는 코인 폭죽·민주는 코인 없이 차분하게(작은 금가루).
    상원 = 보드와 같은 계산(비개선 baseline R31/D32+민주계 무소속2 + 콜된 35석, 무소속은 caucus). 공화는 50석, 민주는 51석이 되는 그 콜의 알림 뒤에 배너.
    (기본값: 공화 상원 50석(밴스 캐스팅보트)·민주 상원 51석. &senthr=N 을 붙이면 양당 모두 N석 기준)
    하원 = data.house.R / data.house.D (라이브 스냅샷 L.h) 가 218 이상이 되는 순간.  &houthr=218 로 기준 변경 가능.
    하원 숫자가 데이터에 없거나 수동으로 띄우고 싶을 때: data 에 majority:["R_HOUSE"] (또는 라이브 스냅샷 mj) / URL &maj=R_HOUSE (열 때 1회)
    값: R_SEN D_SEN R_HOUSE D_HOUSE.  페이지를 열 때 이미 넘은 상태(기준선)면 배너 없음(깃발만 세움) · 기준 아래로 내려갔다가 다시 확정되면 다시 표시.
· 새 옵션:  &novegas 베가스 끔   &nomaj 다수당 배너 끔   &nobanner 둘 다 끔   &coinsfx=0 코인/차임 소리만 끔   &endorsed= / &unendorsed=   &maj=   &senthr=   &houthr=
· 테스트(네트워크 없음):  &demo=vegas (베가스 배너 반복)   &demo=majority (R상원 → R하원 → D상원 → D하원 반복)   &demo=majority&maj=D_HOUSE (하나만)
    ※ 기존 &demo=1 / &demo=R / &demo=house 는 '지지 후보 공화 콜' 뒤에 베가스 배너가 붙어 나옵니다(보고 싶지 않으면 &novegas).
    ※ &demo=vegas / &demo=majority 는 &novegas·&nomaj 와 상관없이 해당 배너를 보여줍니다.
· 소리: 새 음원 파일 없음. 콜 알림의 기존 sting mp3 는 그대로, 코인 소리·차임은 브라우저 WebAudio 로 합성(&nosfx·&sfxvol 따름).
· 이미지(필수 업로드): assets/vegas_endorsed_win.webp  assets/R_senate_majority.webp  assets/R_house_majority.webp  assets/D_senate_majority.webp  assets/D_house_majority.webp
  원본 컷아웃: ../../win_banners/out/*.png(투명, 고해상도) / *.webp(방송용).  재생성: win_banners/tools/build_cutouts.py (src/ → out/)
· 미리보기: ../../win_banners/preview/  vegas_endorsed_win_preview.mp4/.gif · majority_banners_preview.mp4/.gif · stills/  (어두운 배경 합성, 헤드리스 크롬; python3 ../../win_banners/tools/shot_win.py)
· 트리거 검증: python3 ../../win_banners/tools/test_triggers.py  (로컬 가짜 서버만 사용, ntfy 접속 없음) — 지지 R 콜→베가스, 미지지·D·novegas→없음, 상원 51·하원 218·수동 majority→배너, 기준선 로드→없음 등
· 백업: call_alert.html.bak_20261103b / README.txt.bak_20261103b

· 베가스 배너 효과음: sfx/sting_vegas.mp3 (Suno "Vegas Jackpot Win" 2번 곡 앞 6초 + 코인 쏟아지는 소리, -16.7 LUFS). 배너가 뜰 때 1회 재생, &nosfx/&sfxvol/&coinsfx=0 따름. 파일이 없거나 재생이 막히면 합성 코인음으로 대체. (MUSIC 제작 v1~v3 는 sfx/sting_vegas_v1~v3.mp3, Suno 원본은 sfx/suno/ 에 보관)

── 베가스 배너 4종 로테이션 (2026-11-03e 추가) ──
· 베가스 '당선' 배너가 4가지 디자인으로 돌아가며 나옴: 1=기존(assets/vegas_endorsed_win.webp) → 2(와인색, 한글만: vegas_endorsed_win_2.webp) → 3(보라색, 한글+ELECTED: _3.webp) → 4(초록색 주먹 포즈: _4.webp) → 다시 1.
  전구 깜빡임·코인 폭죽(coinPlan 'vegas')·타이밍(VG_T 5.6초)·효과음(sting_vegas.mp3)·위치/크기(같은 1480×740 자리, 이미지 1774×887 동일 비율)는 4종 모두 동일. 전구 위치만 디자인별(VG_BULBS, VG_BULBS_2~4).
· 순서: 배너가 실제로 재생될 때마다 다음 디자인. 다음 번호는 localStorage 'call_alert_vegas_idx_v1' 에 저장 → 페이지 새로고침/재시작해도 이어서(저장소를 못 쓰면 1번부터 메모리 카운터).
· 새 옵션:  &vegasimg=1~4  그 디자인만 고정(저장 번호 안 건드림)   &demo=vegas  4종을 1→2→3→4 순으로 반복(네트워크 없음, 항상 1번부터, localStorage 안 씀). &demo=vegas&vegasimg=3 처럼 하나만 볼 수도 있음.
  (&demo=1/R/house 의 베가스도 데모에서는 1번부터 메모리 순환)
· 이미지 4장은 열 때 미리 읽어둠. 업로드 필수 파일 추가: assets/vegas_endorsed_win_2.webp  assets/vegas_endorsed_win_3.webp  assets/vegas_endorsed_win_4.webp (기존 vegas_endorsed_win.webp 와 함께)
· 새 디자인 전구 좌표: ../../win_banners/tools/vegas_bulbs_2_3_4.json (자동 검출 detect_bulbs_new.py + 눈 확인; 4번은 리본 아래 안쪽 줄 8개를 맨 끝에 이어 붙임)
· 미리보기: preview_vegas_rotation.png (2×2, 2.6초 시점) · preview_vegas_rotation.mp4 (24초, 4종 연속+sting) · preview_vegas_design1~4_2.6s.png
· 백업: call_alert.html.bak_20261103e / README.txt.bak_20261103e
