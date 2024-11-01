# 자동차 경주
## 기능 요구 사항
- 주어진 횟수 동안 n대의 자동차는 전진 또는 멈출 수 있다.
- 각 자동차에 이름을 부여할 수 있다. 전진하는 자동차를 출력할 때 자동차 이름을 같이 출력한다.
- 자동차 이름은 쉼표(,)를 기준으로 구분하며 이름은 5자 이하만 가능하다.
- 사용자는 몇 번의 이동을 할 것인지를 입력할 수 있어야 한다.
- 전진하는 조건은 0에서 9 사이에서 무작위 값을 구한 후 무작위 값이 4 이상일 경우이다.
- 자동차 경주 게임을 완료한 후 누가 우승했는지를 알려준다. 우승자는 한 명 이상일 수 있다.
- 우승자가 여러 명일 경우 쉼표(,)를 이용하여 구분한다.
- 사용자가 잘못된 값을 입력할 경우 `IllegalArgumentException`을 발생시킨 후 애플리케이션은 종료되어야 한다.

## 체크포인트
- [x] 사용자 입력 및 결과 출력
- [x] 입력 유효성 검사
- [x] 자동차 경주 관련 기능 분리
- [x] 테스트 코드 작성

## 설계 및 구현
MVC 패턴에 기반하여 코드를 작성하였습니다.
### Model
- `Car` : 자동차를 나타내기 위한 클래스
- `CarList` : `Car` 객체 리스트를 멤버 변수로 갖고 있는 클래스
- `Round` : 난수 생성을 통해 자동차 전진 여부 결정
- `Referee` : `Car` 객체를 비교하여 가장 많이 전진한 자동차의 이름 반환
- `RacingStatus` : 라운드마다 각 자동차의 위치 반환
- `RandomNumberGenerator` : 난수 생성

객체 간의 결합도 및 응집도보다 책임 분리에 더 중점을 두고 설계하였습니다.. <br>
이러한 이유 때문에 아직까지 결합도 문제를 해결하지 못했습니다.

### View
- `InputView` : 입력 담당
- `OutputView` : 출력 담당

두 기능 모두 싱글톤 패턴을 위해 `object`를 사용했습니다.

### Controller
`RacingController` 객체의 상태를 최소화하기 위해서 필요할 때만 모델의 객체를 생성하고, <br>
해당 객체가 데이터만 반환하게끔 코드를 작성했습니다.

### util
- `Validator` : 입력에 대한 예외 처리
- `ErrorMessage` : 예외 발생 시 출력할 오류 메시지

## 테스트
![image](https://gist.github.com/user-attachments/assets/d949d41c-4025-4f69-a0a2-7fef20519bc3)
- 테스트 코드를 통해 코드 커버리지 100%를 확인하였습니다.
