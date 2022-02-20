# BIG DRIFTER 2
BIG DRIFTER 2 IS WATCHING YOU

## How to use
현재 기준으로 한 개의 봇으로 한 개의 클랜에 대해서만 대응이 가능합니다.

`Python 3.8` 또는 그 이상의 버전을 권장합니다. `Python 3.6` 이상에서도 작동이 되는것을 확인했으나 권장하진 않습니다.

아래 과정대로 설치를 진행해주시면 됩니다. 편의상 가상 환경 설정은 건너뛰었습니다.
 1. `requirements.txt` 파일 내 모듈 설치 (`pip install -r requirements.txt`)
 2. `settings.json.example` 을 수정해 `settings.json`을 만들어줍니다.
    - `bungie_api_key`: 번지 API 키. [번지넷 개발자 포털](https://www.bungie.net/ko/Application) 참조.
    - `discord_token`: 디스코드 봇 토큰. [디스코드 개발자 포털](https://discord.com/developers/applications)
    - `group_id`: 클랜 id. 클랜 링크 맨 뒤에 붙는 숫자를 입력해주세요.
    - `offline_cut`: `$미접` 명령어에서 사용할 미접 커트라인 기본값. 1 이상의 정수를 입력해주세요.
 3. `push_list.json.example` 을 `push_list.json`으로 바꿔주세요. 해당 json 파일 내부의 `alert_target` 안에는 해당 클랜에서 들어오고 나간 사람을 1분 단위로 확인하여 전송해줄 디스코드 채널들의 id를 입력합니다. 귀찮으시다면 봇 가동 및 초대 이후 메시지를 받을 채널에서 `$등록`을 입력해주세요.
 4. 데몬 형태로 실행시켜주시면 됩니다. 로그는 `app.log`에 저장됩니다.

## Commands
명령어|설명
---|---
$정보|현재 봇의 버전, 작동 시간 등의 정보를 표시합니다.
$미접 [커트라인]|클랜 내부에서 일정 일 이상 접속하지 않은 플레이어를 모두 보여줍니다. 기본값은 `settings.json`의 `offline_cut`을 따릅니다. 단위는 **일** 입니다.
$온라인|접속중인 클랜원 목록을 표시합니다. 샤를마뉴의 `!clan online` 명령어와 유사합니다.
$등록|현재 체널에 클랜원 변동 알림을 받습니다. 디스코드 채널 관리자 권한이 필요합니다.
$휴가|클랜 내 유저를 휴가 목록에 등록하거나 해제합니다. 휴가 목록에 등록된 유저는 `$미접` 명령어 사용시 취소선이 생깁니다.
$차단|특정 유저를 차단 목록에 등록하거나 해제합니다. 차단 목록에 등록된 유저가 클랜에 가입한경우 경고를 해줍니다.

## TODO
- 여러 클랜 동시에 지원 (봇 1개, 여러 서버, 서버당 1개씩의 클랜)
- 다국어 지원
- prefix 변경 기능

## PatchNote
### v0.3.0
- 휴가 기능 대폭 개선
  - 휴가중인 클랜원 조회 기능 추가
  - 휴가 등록에 번지 이름 사용 (띄어쓰기 포함된 닉네임도 사용 가능)
- 미접 목록, 휴가중 클랜원 목록 조회 메시지에서 번지넷 연결 URL 추가
- 게임 닉네임과 번지넷 닉네임이 같은 경우 번지넷 닉네임을 숨김 (컴패니언 앱 알림과 유사)
- 닉네임 출력 기능을 비롯한 내부 기능들의 구조 개선

### v0.3.1
- hotfix

### v0.4.0 / v0.4.1
- 차단 목록 추가
  - 기본적으로 번지 이름 또는 스팀 ID로 등록 가능
  - URL 첨부, 개행이 포함된 설명 추가 가능
  - 등록한 유저가 클랜에 들어올 경우 클랜 가입 안내 메시지와 함께 추가 경고 메시지 전송
- 자잘한 버그 수정
- 기타 메시지 포맷 약간 개선
