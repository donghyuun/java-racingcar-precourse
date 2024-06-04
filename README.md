# java-racingcar-precourse

## 기능 요구 사항

1. 사용자는 참가 자동차들의 이름을 입력(이름 5글자 이하, 쉼표 기준 구분)
2. 사용자는 경주를 시도할 횟수를 입력
3. 경주는 사용자가 입력한 횟수만큼 수행
4. 한번의 경주마다 0~9 의 무작위 값을 구함
5. 무작위 값이 4 이상일 경우 전진
6. 매 경주마다 자동차들의 현재 전진 거리를 출력
7. 경주 게임이 완료된 후 누가 우승했는지 출력(한 명 이상 가능, 쉼표로 구분)
8. 사용자가 잘못된 값을 입력할 경우 에러 발생 후 입력 다시 받음

MVC 패턴을 사용해 구현(Model, View, Controller, Service)
## Model

**Car 클래스**

- 필드
    - 이름 정보
    - 누적 전진 상태
- 메서드
    - getter, setter, 생성자
    - 전진 상태 업데이트 메서드 - 반환값 X, 누적 전진 상태 업데이트

## **Controller**

**GameController 클래스(사용자의 입력을 받아서 처리)**

- 필드
    - 스캐너(아래는 입력 받을 값들)
    - 자동차 이름들 저장할 배열
    - 시도할 횟수
- 메서드
    - 입력 받은 문자열을 파싱하여 차 이름들을 구분하여 배열에 저장하도록
    - getter, setter, 생성자
    - GameService 클래스의 GameStart 메서드 호출

## Service

**GameService 클래스(게임을 진행)**

- 필드
    - 참가 자동차들 담은 배열
    - 사용자가 입력하는 시도 횟수
    - 우승자(들) 저장 배열
- 메서드
    - getter, setter(이거 대신에 상태 업데이트 메서드 사용), 생성자(참가 자동차 담은 배열, 시도 횟수를 필드에 저장함)
    - 랜덤 값 선택 메서드 - 랜덤 값 반환
    - 랜덤 값 유효성(4이상) 검증 메서드 - T/F 반환
    - 게임 시작 메서드(for 문으로 게임 돌림)

## View

**GameView 클래스(화면 출력만을 담당)**

메서드

- 현재 전진 정보 출력(전진 상태 필드 사용) 메서드 - 반환값 X, 전진 상태 출력

  (ex) 자동차 이름: - - - )

- 최종 우승자 정보 출력

### 추가 고려 사항

Generic 으로 모든 클래스들 처리해보기(Car 클래스 제외)