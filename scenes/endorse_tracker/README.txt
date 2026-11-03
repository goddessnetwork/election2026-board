GODDESS NETWORK · '트럼프 지지 후보 성적' 오버레이 (endorse_tracker.html, 1920×1080, 배경 투명)

[XSplit] 웹페이지 소스로 추가 → 크기 1920×1080 (call_alert 와 같은 방식, 모든 장면 맨 위 레이어). 모서리의 작은 패널(460px)만 보이고 나머지는 투명.
[주소] 보드·call_alert 와 같은 토픽·키를 그대로 (이 파일에는 비밀값 없음):
  endorse_tracker.html?topic=<보드 토픽>[&pos=tr][&api=소유자/저장소]#k=<보드 키>
  (call_alert 처럼 &live=ntfy 를 붙여도 됨. 토픽이 있으면 자동으로 라이브 모드)

[표시] 제목 "트럼프 지지 후보 성적" (금빛 3D 광택, BHS 폰트) / ✅ 당선 N · ❌ 낙선 N · ⏳ 개표 중 N / 승률 % + 막대 / 상원·하원·주지사 '당선/확정'(예: 3/4, 아래 작게 '전체 24') / 새 콜 한 줄('✅ 켄 팩스턴 (TX-SEN) 당선', 8초)
  숫자가 바뀌면 부드럽게 카운트업(0.9초) + 해당 칸이 톡 튀며 반짝. 데모/예시 데이터면 우측 상단에 'DEMO · 예시' / '예시 · 실제 아님' 표시.

[데이터] call_alert.html 과 같은 피드를 같은 방식으로 읽음(코드는 복사, call_alert.html 은 수정 안 함):
  · 라이브: ntfy 토픽의 서명된 압축 스냅샷(v1, c = {레이스id:[승자,…]} = 현재 콜 전체). 시작할 때 최근 12시간 기록에서 가장 새 서명 스냅샷을 읽고(→ 새로고침해도 즉시 복구),
    이어서 SSE 구독. #k= 서명(HMAC-SHA256) 틀린 메시지는 무시, 더 오래된 s(시각)의 메시지도 무시. (call_alert 와 동일: #k= 를 안 붙이면 서명 검사 생략)
  · 파일 모드(토픽 없음): ../call_alert/data.json (없으면 data.js) 를 &interval=3 초마다 읽음 — tracker/call.py 가 저장할 때마다 미러되는 파일. &data= &datajs= 로 변경.
  · 스냅샷에서 받는 건 '콜 결과'뿐 → 매번 전체 상태로 다시 계산하므로 콜 취소(uncall)·승자 정정이 자동 반영됨.
[판정] 지지 후보 = call_alert.html 의 ENDORSED_LIST 복사본(endorse_list_20261103.txt 에서 생성, 281곳: 상원 24 · 주지사 23 · 하원 234. 레이스 1곳 = 지지 후보 1명).
  우선순위는 call_alert 와 같음: &unendorsed=ID,ID > races[i].endorsed false > true > 명단 · &endorsed=ID,ID · data.endorsed.
  지지 후보 레이스의 콜 승자 R(공화) → ✅ 당선 / 승자 D·I(상대) → ❌ 낙선 / 콜 없음 → ⏳ 개표 중.
  개표 중 = 지지 후보 전체(281) − 확정(당선+낙선) — '레이스 수'이자 '후보 수'(한 레이스에 지지 후보 1명). 승률 = 당선 ÷ 확정(확정 0이면 '–').
  id: 상원 XX-SEN · 주지사 XX-GOV · 하원 XX-NN(2자리) · 단일구 XX-AL.  지지 아닌 레이스의 콜은 무시.
[보드 집계와 관계] 03_control_math(상원 비개선 R31/D32+무소속2 + 콜된 35석, 하원 data.house.R/D 합계)와는 별개의 집계: 이 오버레이는 '지지 후보가 나온 레이스의 콜'만 센다.

[저장] localStorage('endorse_tracker_v1')에 콜 결과(id→승자)와 계산된 숫자를 저장 → 새로고침/XSplit 소스 재로딩에도 유지(피드가 연결되면 그 상태로 교체).
  토픽·키는 저장하지 않음. 24시간 넘은 저장값은 무시(&maxage=시간). 예시(example) 데이터·데모는 저장 안 함.
  &reset=1 : 열 때 저장값을 지우고 0부터 (한 번 쓰고 주소에서 빼세요 — 안 빼면 소스를 다시 열 때마다 비워짐. 라이브 피드가 있으면 곧바로 다시 채워짐)

[옵션]
  &pos=tl|tr|bl|br   모서리(기본 br)   &mx=28 &my=110  모서리에서 떨어진 px(기본: 아래쪽이면 my=110, 위쪽이면 28)   &scale=1  크기 배율
  &nobg=1 패널 배경·테두리 없이 글자만   &static=1 모든 애니메이션 끔   &dur=900 카운트업 ms   &notag=1 '예시' 표시 숨김   &nolast=1 새 콜 한 줄 숨김
  &debug=1 패널 위에 연결 상태 표시(방송 땐 끄기)   &server=  &since=12h  &api=  &interval=  (call_alert 와 같은 의미)
  &endorsed=ID,ID 추가   &unendorsed=ID,ID 제외
[팝업 전용 모드] &popup=1  — 메인 보드 위에서 패널이 너무 많이 가려질 때. 평소엔 완전 투명(아무것도 안 보임), 새 지지 후보 레이스의 콜(당선/낙선)이 '라이브로 새로' 들어올 때만
  옆에서 미끄러져 들어와(페이드+슬라이드) → 숫자가 이전 값에서 새 값으로 카운트업 + 칸이 톡 튐 → 잠시 후 다시 사라짐.  &popup 이 없으면 기존 동작(항상 표시) 그대로.
  &popdur=10      보이는 시간(초, 기본 10. 들어오는 0.7초 포함)
  &popdelay=      콜이 들어온 뒤 표시까지 기다리는 초. 안 쓰면 '자동' = call_alert.html 의 콜 알림(공화 당선 7.4초 · 그 외 6초, 사이 0.35초)과 지지 후보 공화 당선의
                  '베가스' 배너(5.6초 + 0.35초)가 끝난 뒤 +0.6초 여유:  지지 후보 공화 당선 1건 ≈ 14.3초 · 낙선(민주/무소속 승) 1건 ≈ 7초. 콜이 여러 건 쌓이면 call_alert 가 하나씩 차례로 재생하는 것처럼
                  그 합만큼 뒤로 밀림(상원 51석·하원 218석 다수당 배너는 시점을 알 수 없어 반영 안 함 — 겹치면 &popdelay=20 처럼 직접 늘리세요). &popdelay=0 이면 바로.
                  (call_alert 값은 call_alert.html 의 T=(R?7.4:6), VG_T=5.6 에서 읽은 것. 그쪽 길이를 바꾸면 이 값도 맞춰야 함)
  · 트리거: 지지 후보 레이스의 당선/낙선이 새로 생기거나 승자가 바뀐 경우만. 첫 로드·저장값 복원(새로고침)·&reset=1·라이브 첫 스냅샷(앱을 닫은 사이 쌓인 콜)·파일 모드 첫 읽기·콜 취소·지지 아닌 레이스의 콜은 팝업 없음.
  · 연속 콜: 깜빡이지 않고 대기/표시 시간을 뒤로 미루며 가장 새 상태 하나로 표시. 이미 보이는 중이면 계속 보여주고(표시 종료 4초 안쪽이면 이어 붙임) 숫자만 새로 틱.
  · 새 콜 한 줄('✅ …')은 패널이 들어온 뒤 표시. 숨은 동안 숫자는 이전 값을 유지(보일 때 0.45초 뒤 새 값으로 올라감).  &static=1 이면 애니메이션 없이 즉시 켜짐/꺼짐.
  · &debug=1 이면 숨은 동안에도 패널 위치에 연결 상태 + 'POPUP 숨김/대기 N초/표시 N초 남음' 이 보임(방송 땐 끄기).  &pos= &scale= &mx= &my= 등 기존 옵션 그대로 (슬라이드는 가까운 쪽 가장자리에서).
  · 데모(&demo=1&popup=1): 콜마다 바로(&popdelay 기본 0) 나타났다 &popdur 뒤 사라짐 — 미리보기용. 예) endorse_tracker.html?popup=1&demo=1&dstart=6000&dint=30&popdur=8
  · 방송용 주소 예: endorse_tracker.html?topic=<보드 토픽>&pos=br&popup=1[&popdur=10][&popdelay=14]#k=<보드 키>   (&params 는 반드시 #k= 앞에)
    PC용 팝업 주소 파일: /workspace/backup/.endorse_tracker_url_popup_for_pc.txt (비밀 포함, 기존 .endorse_tracker_url_for_pc.txt 에 &popup=1 만 추가)
[데모] &demo=1 : 네트워크·저장 없이 지지 후보 레이스를 하나씩 콜(공화 승 약 72%)하며 숫자가 올라감, 끝나면 처음부터 반복.
  &dint=1.4 콜 간격(초)  &dstart=800 첫 콜까지 ms  &winp=0.72 공화 승 확률  &dn=60 콜 수  &seed=6 순서/결과 시드

[XSplit 2줄 요약]
  1) 웹페이지 소스 추가 → URL: endorse_tracker.html?topic=<보드 토픽>&pos=br#k=<보드 키> , 크기 1920×1080, 투명 배경(call_alert 와 같은 설정), 모든 장면 위에 배치.
  2) 방송 직전 한 번 &reset=1 로 열어 0 확인 → &reset=1 빼고 저장. 첫 화면에서 '예시' 표시가 보이면 아직 예시 데이터라는 뜻.

[파일]
  endorse_tracker.html       배포용 본체 (ENDORSED_LIST 내장)    fonts/BlackHanSans-Regular.ttf  제목·숫자 폰트(같은 폴더 fonts/ 와 같이 올려야 함)
  endorse_tracker.src.html   원본 템플릿 / build.py  = call_alert.html 의 ENDORSED_LIST 를 읽어(수정 안 함) endorse_tracker.html 재생성 (명단 갱신 후 실행)
  test_endorse_tracker.py    검증(팝업 모드 포함, 로컬 가짜 ntfy 서버 + 임시 테스트 키, 실제 ntfy 접속·실제 토픽/키 없음)   shot_preview.py  미리보기 생성
  shot_preview_popup.py / preview_popup.mp4(20초, 실제 메인 보드 위: 숨김→콜→팝업→사라짐) / preview_popup.png(팝업이 보이는 순간)
  preview.png / preview.mp4(10초) / preview_scene.png(실제 장면 위) / preview_alpha.png(투명 단독)

[한계·가정]
  · 하원: 보드 피드(call.py)는 레이스별 콜을 상원 35·주지사 36·하원 주요 6곳(NY-17 MI-07 NJ-07 PA-08 PA-07 NC-01)만 담음. 지지 하원 후보는 234명인데 그중 6곳만 콜이 들어옴
    → 나머지 하원 지지 후보는 피드에 id 가 들어오기 전까지 '개표 중'에 남아 하원 칸은 천천히 오르고 '개표 중' 숫자는 하원 때문에 크게 남음.
    하원 의석 합계(data.house R/D)는 어느 후보인지 알 수 없어 반영하지 못함. 다른 하원 id 콜(예: TX-21)이 같은 형식(c 또는 races/house_races 의 winner)으로 들어오면 자동으로 센다.
  · '지지 후보 = 공화 후보'로 가정(call_alert 의 베가스 배너와 같은 규칙): 승자가 R 이면 당선, D/I 면 낙선. 지지 후보가 비공화 레이스(예: 무소속)면 별도 필드로 &unendorsed 처리.
  · 지지 명단: call_alert 내장본(1103 명단, 281곳). 10/30 명단(280곳)은 MN-01 이 없는 차이뿐(1103 에서 추가).
  · 예시 data.json(example:true) 의 콜도 '예시' 표시와 함께 세어 보임(파일 모드). 방송은 라이브 모드 권장.
  · XSplit(CEF)·크롬에서 localStorage 가 막혀 있으면 저장만 건너뜀(표시는 정상).
