# 온라인 강의 학습 도우미 챗봇 <조교 딩> 


> - 시연 영상 : https://konkukackr-my.sharepoint.com/:v:/g/personal/tarahjjeon_konkuk_ac_kr/Ee-H4A3C4ehLr8kgGi7P1z8BHF1kFfe_ZOmVCgL5LVV-7w?e=mNlVS7
> - 소스 코드 설명 동영상 (pptx 파일 내 음성 설명 포함) : https://konkukackr-my.sharepoint.com/:p:/g/personal/tarahjjeon_konkuk_ac_kr/EWdjoj95DoNJvIcY37lFWJYBEldsYY8mZ5m5sRGDEEh0YQ?e=SIekv5



  1. 1개의 강의 동영상 + 동영상 강의 질의 응답용 챗봇 (QnA maker.ai 기반)
  > https://github.com/gywlssww/azure_chatbot_qnabot   
  
  2. 복습 퀴즈 & 학생 관리용 챗봇 (DB 연동, Complex Dialog bot 기반) 
  > https://github.com/gywlssww/azure_chatbot_quiz.git
  
  두 개 모듈이 임베드 된 .NET 기반 웹앱입니다.
  
## 사전 요구 사항

- [.NET Core SDK](https://dotnet.microsoft.com/download) version 3.1

  ```bash
  # determine dotnet version
  dotnet --version
  ```
- Azure Database for Postgresql 계정
- qnamaker.ai 계정 

## 실행 방법

1.직접 챗봇 실행
- Clone the repository

    ```bash
    git clone https://github.com/gywlssww/azure_chatbot.git
    ```
    ```bash
    git clone https://github.com/gywlssww/azure_chatbot_quiz.git
    ```
    ```bash
    git clone https://github.com/gywlssww/azure_chatbot_qnabot.git
    ```

- Run the bot from Visual Studio:

  - Card.cs : HeroCard, ThumbnailCard 생성을 위한 클래스
  - UserProfile.cs : 유저 상태 정보 관리를 위한 클래스

2.URL에서 직접 테스트
- https://oschatbot20200711031349.azurewebsites.net

## Testing the bot using Bot Framework Emulator

[Bot Framework Emulator](https://github.com/microsoft/botframework-emulator) is a desktop application that allows bot developers to test and debug their bots on localhost or running remotely through a tunnel.

- Install the latest Bot Framework Emulator from [here](https://github.com/Microsoft/BotFramework-Emulator/releases)

### Connect to the bot using Bot Framework Emulator

- Launch Bot Framework Emulator
- File -> Open Bot
- Enter a Bot URL of `http://localhost:3978/api/messages`


## 동영상 질의 응답 용 봇: 조교 딩의 인사가 담긴 AdaptiveCard 메세지가 출력되면 정상적으로 작동이 시작된 것 (Index.cshtml)

> 로딩에 시간이 오래 걸릴 경우 '하이!' '안녕' 등의 인사 메세지를 입력해보세요!

(1) 강의를 재생하며 생긴 의문점을 질문

(2) 강의록을 기반으로 QnA maker knowledge base 구성 > 답변 구성이 강의 내용을 바탕으로 이루어져 강의 효율을 증가시키는 효과. 강의 관련 질문에 대한 답변만 존재하는 한계.

(3) '졸립다', '피곤하다' 등의 일상 대화 가능

(4) 강의 수강 완료 후 퀴즈 응시 > '퀴즈' 입력 시 복습 퀴즈 화면으로 전환 > 복습 퀴즈용 챗봇 작동


## 복습 퀴즈 용 봇: 조교 딩 이미지가 담긴 카드 메세지가 출력되면 정상적으로 작동이 시작된 것 (Privacy.cshtml)

> 로딩이 오래 걸릴 경우 '서예지'를 입력해보세요!

>>***데이터 베이스에 저장되어있는 사용자
>>'서예지-201711343'
>>'김수현-201712345'

(안내에 따라)

   (1) 이름 입력
   
   (2) 학번 입력
   
   (3) 현재까지 출석률 조회
   
   (4) 퀴즈 시작 - 문제에 대해 답이라 생각하는 항목 클릭
   
                 - 정답 확인 후 <위키 백과로 이동> 버튼을 이용해 관련 사이트로 이동 가능.
                 
   (5) 퀴즈 종료 후 문항 별 채점 결과와 최종 점수 확인.
   
   (6) 데이터 베이스 상의 변경된 출석률 확인 후 프로그램 종료.
