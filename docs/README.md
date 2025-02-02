## 구현할 기능 목록

- Application 초기화 기능
  - 파일에서 크루 이름을 불러와 Repository 에 저장하는 기능

- 페어 매칭하는 기능
  - 매칭 정보가 있다면, 다시 메칭할지 물어봄
  - 주어진 방법 (`camp.nextstep.edu.missionutils.Randoms`의 shuffle 메서드를 활용 ...) 을 통해 페어 매칭 실시
  - 같은 레벨에서 매칭이 된 크루가 있었는지 확인 (있을 경우 3번까지 재실행)
    - 3번이 넘어갈 경우, 에러를 발생시킴
  - 페어 매칭이 되었다면 Repository에 저장함

- 페어 메칭 조회
  - Repository에 있는 정보를 가져와서 보여줌


## Class별 구현 기능 조회

- InputView : 입력 담당
  - [ ] 특정 기능을 선택하여 입력 #readFuntion()
    - 1,2,3,Q 가 아닌 경우 에러를 발생함
  - [ ] 과정, 레벨, 미션을 입력하는 기능 #readMission()
    - 형식에 맞지 않을 경우, 에러를 발생함
    - 형식 : 백엔드, 레벨1, 자동차경주
  - [ ] 매칭 정보가 있을 경우, 다시 매칭할 지 입력하는 기능 #readRetryMatching()
    - 네, 아니오 가 아닌 경우 에러를 발생함
  
- OutputView : 출력 담당
  - [x] 현재 가지고 있는 과정, 미션을 보여주는 기능 #printMissions()
  - [x] 초기화 완료 출력 #printFinishedInitializing()
  - [x] 에러 메세지 출력 #printErrorMessage()
  - [ ] 페어 매칭 결과를 보여주는 기능 #printMatchingResult()

- CrewReader : md 파일에 있는 Crew 정보를 읽어오는 기능
  - [x] 백엔드 크루를 읽어오는 기능 #readBackendCrews
  - [x] 프론트엔드 크루를 읽어오는 기능 #readFrontendCrews

- CrewRepository : Crew 정보를 저장
  - [x] 초기 정보를 통해 Repository를 설정
  - [x] 정보를 제공하는 기능 #get~

- MatchingRepository : 매칭 정보를 저장하는 역할
  - [x] 매칭 정보를 저장함
  - [x] 매칭 정보를 조회하는 역할
  - [x] 매칭 정보가 있는지 확인하는 기능

- Mission 
  - [x] MatchingRepository를 구분해주는 Mission enum 
    - 레벨 정보를 가지고 있음
  - [x] 동일한 레벨인지 확인 #isEqualLevel

- CrewSuffler : Crew를 섞어주는 역할
  - [x] Crew들을 입력 받아 섞음

- CrewMatcher : Crew를 매칭해주는 역할
  - [x] Crew들을 입력 받아 매칭을 해줌

- Crew : 회원의 정보를 가지고 있음
  - [x] equals()
  - [x] getName()

- Pair : 한 쌍(2~3명)의 매칭 정보를 가지고 있음
  - [x] 생성 시에 Crew 가 2~3명인지 확인하고 그렇지 않으면 에러를 발생시킴
  - [ ] 같은 인물이 있는지 확인하고 있다면 에러를 발생시킴
  - [x] 다른 페어를 받아 Crew가 곂치는지 확인함
    - 최소 2명의 공통 사람이 있을 경우 true를 반환함

- Matching : 매칭 정보를 가지고 있음
  - [x] 같은 코스, 과정인지 확인하는 기능 #isSameMatching
  - [x] 곂쳐있는 페어가 있는지 확인하는 기능 #isExistOverlappedPair
  - [x] 매칭 정보를 제공하는 기능 구현 #getMatchingDto()

- MatchingService
  - [ ] 페어 매칭 기능
  - [ ] 현재 매칭되어 있는지 조회하는 기능
  - [ ] 페어 조회 기능
  - [ ] 페어 초기화 기능

- Application
  - [ ] 전반적인 실행 로직 구현
    - [x] 예외가 발생한 경우 입력 부분부터 반복되도록 함
    - [x] 선택한 기능에 따라 다른 기능이 실행되도록 함
    - [ ] 페어 매칭 실시 및 조회 결과 출력
    - [ ] 페어 매칭 조회 및 결과 출력
    - [ ] 초기화 실시