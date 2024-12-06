# YTMusicBypass

## 목적

유튜브 뮤직은 한국 외 국가에서는 광고를 포함한 무료 서비스도 제공되나, 한국에서 프리미엄 없이 사용할 수 없습니다. 이러한 문제를 해결하기 위한 방법을 제시합니다.

## 원리

1. Custom DNS를 사용해 _.music.youtube.com, _.youtubei.googleapis.com의 ip주소를 유튜브 원본 서버가 아닌, 따로 호스팅 되고 있는 **한국이 아닌** 서버로 리턴합니다.
2. 호스팅 되고 있는 서버에서 haproxy를 사용해 마치 proxy처럼 작동하게 되고, 유튜브는 한국이 아닌 서버가 호스팅 되고 있는 나라로 인식하게 됩니다.

## 사용 방법

### 서버

1. **한국이 아닌** 서버에 해당 repository를 clone 한 후, `docker compose up -d`와 같은 명령어로 haproxy를 실행시킵니다.

### DNS

1. https://my.nextdns.io/login 에 접속해 회원가입 및 로그인을 합니다.
2. `New` 버튼을 클릭해 새로운 프로파일을 만듭니다.
3. `Settings` -> `Rewrites`에 도메인을 등록합니다.
   - Domain: `music.youtube.com`, `youtubei.googleapis.com`
   - Answer: 서버 아이피 주소
4. 휴대폰으로 NextDNS에 접속해 설정을 완료합니다.
