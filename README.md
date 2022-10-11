# 자동차 경주 게임
## 진행 방법
* 자동차 경주 게임 요구사항을 파악한다.
* 요구사항에 대한 구현을 완료한 후 자신의 github 아이디에 해당하는 브랜치에 Pull Request(이하 PR)를 통해 과제를 제출한다.

## 과제 제출 과정
* [과제 제출 방법](https://github.com/next-step/nextstep-docs/tree/master/precourse)

## ︎📝 구현할 기능 목록
### ⌨️ 입력 및 입력 값의 유효성 검사
* Operator(컨트롤러) :  
  * 사용자로부터 경주 할 자동자 이름과 게임을 시도할 회수를 입력받는다.
* Validator : Operator(컨트롤러)가 사용자로부터 경주 할 자동자 이름을 입력받을 때, 이름이 5자 이하인지 검사한다.
  * 자동자 이름을 입력받을 때, 이름에 빈값이 입력되거나, 이름이 5자 초과이면 Operator(컨트롤러)에게 메시지를 보낸다.
  * 자동자 이름을 입력받을 때, 이름에 ','가 없다면 1대만 입력받은 것이므로, Operator(컨트롤러)에게 메시지를 보낸다.
  * 자동자 이름을 입력받을 때, 중복된 이름이 존재하면 Operator(컨트롤러)에게 메시지를 보낸다.
  * 시도할 회수를 입력받을 때, 빈값이 입력되거나, 입력값이 0이거나, 숫자가 아니라면 Operator(컨트롤러)에게 메시지를 보낸다.
* Operator(컨트롤러) : 
  * Validator가 자동자 이름을 입력받을 때, 빈값이 입력되거나, 1대만 입력받거나, 중복된 이름이 존재하거나, 이름이 5자 초과인 경우라고 알려주면,  
  "[ERROR]"로 시작하는 에러 메시지를 출력 후, 'IllegalArgumentException'을 발생시키고, 그 부분부터 입력을 다시 받는다.
  * Validator가 자동자 경주 게임을 몇 번 실행할 지, 시도할 회수를 입력받을 때, 빈값이 입력되거나, 입력값이 0이거나, 숫자가 아니라고 알려주면, 
  "[ERROR]"로 시작하는 에러 메시지를 출력 후, 'IllegalArgumentException'을 발생시키고, 그 부분부터 입력을 다시 받는다.

### 🧮 RacingCar게임의 데이터 처리 및 저장
* 개별 자동차의 이름과 자동차가 전진할 횟수를 가진 RacingCar를 RacingCarRepository에 보관한다.
* RacingCar : 
  * 각각의 개별 자동차 클래스
  * 개별 자동차의 이름과 자동차가 전진할 횟수를 가짐
  * Random 값(전진할 값) : camp.nextstep.edu.missionutils.Randoms의 pickNumberInRange() 사용
  * 전진하는 조건은 0에서 9 사이에서 random 값을 구한 후 random 값이 4 이상일 경우 전진하고, 3 이하의 값이면 멈춘다.
* RacingCarRepository(저장소 대역) : 
  * RacingCar를 가진 일급객체

### 🖨 출력
 * RacingCarRepository가 가진 RacingCar들의 이름과 전진한 값을 출력
 * RacingCarRepository가 가진 RacingCar들의 역순 정렬처리 멤버 함수 추가
 * RacingCarRepository가 가진 RacingCar들의 최종 우승자 출력 멤버 함수 추가

## ︎💡 구현할 기능 후보 목록(브레인 스토밍)
### ☕️ 객체 종류
* Operator(컨트롤러) : 
  * 마지막에 RacingCar를 순위별로 정렬
* Validator : 입력 값의 유효성 검증
* RacingCar(모델) : 경주할 자동차 이름, 전진한 회수를 가진 Bean
* RacingCarRepository(저장소 대역) : RacingCar를 가진 일급객체
* RacingInfo : 게임의 설정 정보(RacingCar가 몇 번의 이동을 할 것인지 사용자가 입력한 값을 저장)를 보관
* PrintGameState : 
  * 각각의 RacingCar의 이름과 각 차수별 실행 결과를 출력한다.
  * 최종 우승자를 출력한다.

## 💬 기능 요구사항
* 주어진 횟수 동안 n대의 자동차는 전진 또는 멈출 수 있다.
* 각 자동차에 이름을 부여할 수 있다. 전진하는 자동차를 출력할 때 자동차 이름을 같이 출력한다.
* 자동차 이름은 쉼표(,)를 기준으로 구분하며 이름은 5자 이하만 가능하다.
* 사용자는 몇 번의 이동을 할 것인지를 입력할 수 있어야 한다.
* 전진하는 조건은 0에서 9 사이에서 random 값을 구한 후 random 값이 4 이상일 경우 전진하고, 3 이하의 값이면 멈춘다.
* 자동차 경주 게임을 완료한 후 누가 우승했는지를 알려준다.
* 우승자가 한 명 이상일 경우, 쉼표(,)로 이름을 구분해 출력한다.
* 사용자가 잘못된 값을 입력할 경우 IllegalArgumentException를 발생시키고, "[ERROR]"로 시작하는 에러 메시지를
  출력 후 그 부분부터 입력을 다시 받는다.
* Exception이 아닌 IllegalArgumentException, IllegalStateException 등과 같은 명확한 유형을 처리한다.

## 💬 입출력 요구사항
### ⌨️ 입력
* 경주 할 자동차 이름(이름은 쉼표(,) 기준으로 구분) 
  > pobi,woni,jun
* 시도할 회수
  > 5

### 🖨 출력
* 각 차수별 실행 결과(PDF 문제지에서 아래 'pobi : ——' 부분이 잘못된 듯 합니다.)
  > pobi : —— woni : --- jun : ----
* 단독 우승자 안내 문구
  > 최종 우승자: pobi
*  공동 우승자 안내 문구
  > 최종 우승자: pobi, jun
*  예외 상황 시 에러 문구를 출력해야 한다. 단, 에러 문구는 [ERROR]로 시작해야 한다.
  > [ERROR] 시도 횟수는 숫자여야 한다.

## 🚀 프로그램 실행 결과 예시
### Run: RacingCar
* 경주할 자동차 이름을 입력하세요.(이름은 쉼표(,) 기준으로 구분)
  > pobi,crong,honux
* 시도할 회수는 몇회인가요?
  > 5
* 실행 결과
  > pobi : -  
  > crong :  
  > honux : -
  
  > pobi : --  
  > crong : -  
  > honux : --

  > pobi : ---  
  > crong : --  
  > honux : ---
  
  > pobi : ----  
  > crong : -- 
  > honux : ----
  
  > pobi : -----  
  > crong : ---- 
  > honux : -----

  > 최종 우승자: pobi, honux


## 💬 프로그래밍 요구사항 - 제약사항
* 시작점 : src/main/java/racinggame.Application.main()
* JDK 8에서 정상 동작
* Random 값 : camp.nextstep.edu.missionutils.Randoms의 pickNumberInRange() 사용
* 사용자의 값 입력 : camp.nextstep.edu.missionutils.Console의 readLine() 사용
* racingcar package의 ApplicationTest.전진_정지() Test Case 성공
* racingcar package의 ApplicationTest.이름에_대한_예외_처리() Test Case 성공
* 필수는 아니지만, 제공된 소스 코드를 참고해서 자동차 경주 게임을 위한 모든 Test Cast 추가
* [자바 코드 컨벤션](https://github.com/woowacourse/woowacourse-docs/tree/master/styleguide/java) 을 지키기
* indent(인덴트,들여쓰기) depth는 1까지만 허용 : depth를 줄이는 좋은 방법은 함수(또는메소드)를 분리
* 자바8에 추가된 stream api를 사용하지 않고 구현. 단, 람다는 사용 가능
* else, switch/case 예약어를 쓰지 않는다.
* 함수(또는 메소드)의 길이가 10라인을 넘어가지 않도록 구현 : 함수(또는메소드)가 한 가지 일만 잘 하도록 구현
* 일급콜렉션을 활용해 구현한다.
  * 참고문서: [https://developerfarm.wordpress.com/2012/02/01/object_calisthenics_/](https://developerfarm.wordpress.com/2012/02/01/object_calisthenics_/)
* 모든 원시값과 문자열을 포장한다.
  * 참고문서: [https://developerfarm.wordpress.com/2012/01/27/object_calisthenics_4](https://developerfarm.wordpress.com/2012/01/27/object_calisthenics_4)
* 도메인 로직에 단위 테스트를 구현. 단, UI(System.out, System.in, Scanner)로직은 제외
  * 핵심 로직을 구현하는 코드와 UI를 담당하는 로직을 분리해 구현
  * MVC의 Model에 대한 단위 테스트를 추가하는것에 집중
* JUnit5 기반 단위 테스트를 구현

## 💬 과제 진행 요구사항
* 미션은 [저장소](https://github.com/next-step/java-racingcar-precourse)를 fork/clone해 시작한다.
* 기능을 구현하기 전에 docs/README.md 파일에 구현할 기능 목록을 정리해 추가한다.
* git의 commit단위는 앞단계에서 docs/README.md 파일에 정리한 기능 목록 단위 또는 의미있는 단위로 Commit 한다.
* [커밋 메시지 컨벤션](https://gist.github.com/stephenparish/9941e89d80e2bc58a153)을 참고해 commit log를 남기려고 노력해 본다.

## ✅️ 과제 제출 전 체크리스트 - 0점 방지
* 자바 8로 실행이 되는지 확인
* 모든 테스트가 통과하는지 확인
  * Mac or Linux : "./gradlew clean test"
  * Windows : "gradlew.bat clean test"

## License
* 문제의 라이선스와 문제에 제공된 기본 소스의 라이선스는 [우아한테크캠프 pro](https://edu.nextstep.camp/c/lqsBs7x0/) 측에 있습니다.


