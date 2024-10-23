# 미션 - 자동차 경주

> [!NOTE]  
> 이 코드는 원래 [java-racingcar-6](https://github.com/woowacourse-precourse/java-racingcar-6)에서 제공된 **Java 기반의 자동차 경주 게임**을 **Python**에 맞게 변환한 과제입니다. 프로젝트 구조, 요구 사항, 기능 구현 방식은 원본 저장소를 바탕으로 Python 환경에 맞추어 수정하였습니다.

---

## 🔍 진행 방식

- 미션은 **기능 요구 사항, 프로그래밍 요구 사항, 과제 진행 요구 사항** 세 가지로 구성되어 있습니다.
- 세 가지 요구 사항을 만족하기 위해 노력해야 하며, 특히 기능을 구현하기 전에 기능 목록을 작성하고 기능 단위로 커밋하는 방식으로 진행해야 합니다.
- 기능 요구 사항에 명시되지 않은 부분은 스스로 판단하여 구현할 수 있습니다.

## 📮 미션 제출 방법

- 미션 구현을 완료한 후 GitHub을 통해 제출해야 합니다.
  - **Pull Request로 최종 제출**

## 🚨 과제 제출 전 체크 리스트 - 0점 방지

- 기능을 모두 정상적으로 구현했더라도 **요구 사항에 명시된 출력값 형식을 지키지 않을 경우 0점 처리**됩니다.
- 기능 구현을 완료한 뒤 아래 가이드에 따라 테스트를 실행하고 모든 테스트가 성공하는지 확인합니다.
- **테스트가 실패할 경우 0점 처리**되므로, 반드시 확인 후 제출해야 합니다.

---

### 테스트 실행 가이드

과제에서 구현한 기능이 정상적으로 동작하는지 확인하기 위해 Pytest를 사용하여 테스트를 실행합니다. 아래 단계에 따라 테스트 환경을 설정하고, 모든 테스트가 통과하는지 확인할 수 있습니다.

#### 1. Python 버전 확인

이 프로그램은 Python 3.9 이상에서 동작하도록 개발되었습니다. 먼저 Python 버전이 올바르게 설치되었는지 확인합니다.

```bash
python --version
```

출력 예시:
```bash
Python 3.9.x
```

Python 3.9 이상이 설치되어 있지 않다면, Python 공식 웹사이트([https://www.python.org/](https://www.python.org/))에서 최신 버전을 설치하세요.

#### 2. 의존성 패키지 설치

이 프로그램은 `pytest`를 사용해 테스트를 실행합니다. `requirements.txt` 파일에 명시된 의존성 패키지를 설치합니다. 아래 명령어를 터미널에 입력하여 필요한 패키지를 설치합니다.

```bash
pip install -r requirements.txt
```

#### 3. 테스트 실행

테스트 코드는 `tests/` 디렉터리에 위치해 있습니다. Pytest 명령어를 사용하여 프로젝트의 모든 테스트를 실행할 수 있습니다. 프로젝트 루트 디렉터리에서 아래 명령어를 실행합니다.

```bash
pytest
```

테스트 실행 시 출력 예시는 다음과 같습니다.

```bash
=========================== test session starts ============================
platform darwin -- Python 3.9.x, pytest-6.2.5, py-1.10.0, pluggy-0.13.1
rootdir: /path/to/project
collected 5 items

tests/racingcar/test_application.py ....                                   [ 80%]
tests/study/test_string.py ..                                              [100%]

============================ 100% passing in Xs =============================
```

#### 4. 테스트 결과 확인

테스트가 성공적으로 통과되었다면 위와 같이 **100% passing** 메시지가 출력됩니다. 만약 테스트가 실패하면, 실패한 테스트에 대한 상세한 정보가 제공되며, 이 정보를 바탕으로 문제를 해결할 수 있습니다.

#### 5. 개별 테스트 실행

특정 테스트 파일만 실행하고 싶다면, 해당 파일을 지정하여 Pytest를 실행할 수 있습니다. 예를 들어, `test_application.py` 파일만 테스트하려면 다음 명령어를 실행합니다.

```bash
pytest tests/racingcar/test_application.py
```

#### 6. 커버리지 테스트 (선택 사항)

테스트 커버리지를 확인하고 싶다면, `pytest-cov` 플러그인을 사용할 수 있습니다. 먼저 해당 플러그인을 설치한 후, 아래 명령어로 커버리지를 확인할 수 있습니다.

```bash
pip install pytest-cov
pytest --cov=src
```

---

## 🚀 기능 요구 사항

초간단 자동차 경주 게임을 구현해야 합니다.

- 주어진 횟수 동안 n대의 자동차는 전진 또는 멈출 수 있습니다.
- 각 자동차에 이름을 부여할 수 있으며, 전진하는 자동차를 출력할 때 자동차 이름도 함께 출력해야 합니다.
- 자동차 이름은 쉼표(,)를 기준으로 구분하며, 이름은 5자 이하만 가능합니다.
- 사용자는 몇 번의 이동을 할 것인지를 입력할 수 있어야 합니다.
- 전진하는 조건은 0에서 9 사이에서 무작위 값을 구한 후, 무작위 값이 4 이상일 경우입니다.
- 자동차 경주가 끝난 후 누가 우승했는지 알려주어야 하며, 우승자는 한 명 이상일 수 있습니다.
- 우승자가 여러 명일 경우 쉼표(,)를 이용하여 구분합니다.
- 사용자가 잘못된 값을 입력할 경우 `ValueError`를 발생시킨 후 프로그램을 종료해야 합니다.

### 입출력 요구 사항

#### 입력

- 경주할 자동차 이름 (쉼표로 구분)

```bash
pobi,woni,jun
```

- 시도할 횟수

```bash
5
```

#### 출력

- 각 차수별 실행 결과

```bash
pobi : --
woni : ----
jun : ---
```

- 단독 우승자 안내 문구

```bash
최종 우승자 : pobi
```

- 공동 우승자 안내 문구

```bash
최종 우승자 : pobi, jun
```

#### 실행 결과 예시

```bash
경주할 자동차 이름을 입력하세요.(이름은 쉼표로 구분)
pobi,woni,jun
시도할 횟수는 몇 회인가요?
5

실행 결과
pobi : -
woni :
jun : -

pobi : --
woni : -
jun : --

pobi : ---
woni : --
jun : ---

pobi : ----
woni : ---
jun : ----

pobi : -----
woni : ----
jun : -----

최종 우승자 : pobi, jun
```

---

## 🎯 프로그래밍 요구 사항

- Python 3.9 이상에서 실행 가능해야 합니다. **정상적으로 동작하지 않을 경우 0점 처리**됩니다.
- 프로그램 실행의 시작점은 `src/racingcar/main.py`의 `main()` 함수입니다.
- 외부 라이브러리는 사용하지 않습니다.
- [Python 코드 스타일 가이드(Python PEP8)](https://peps.python.org/pep-0008/)를 준수하며 프로그래밍합니다.
- 프로그램 종료 시 `sys.exit()`를 호출하지 않습니다.
- 프로그램 구현이 완료되면 `tests/racingcar/test_application.py`의 모든 테스트가 성공해야 합니다. **테스트가 실패할 경우 0점 처리**됩니다.
- 프로그래밍 요구 사항에서 별도로 명시하지 않는 한, 파일과 패키지 이름을 수정하거나 이동하지 않습니다.

### 추가된 요구 사항

- 인덴트(들여쓰기) 깊이를 3이 넘지 않도록 구현합니다. 2까지만 허용합니다.
  - 예를 들어, while문 안에 if문이 있으면 들여쓰기는 2입니다.
  - 힌트: 함수나 메서드로 분리하면 들여쓰기 깊이를 줄일 수 있습니다.
- 삼항 연산자를 사용하지 않습니다.
- 함수나 메서드가 한 가지 일만 하도록 최대한 작게 만들어야 합니다.
- Pytest와 Assert를 이용해 본인이 정리한 기능 목록이 정상 동작하는지 테스트 코드로 확인합니다.

---

## ✏️ 과제 진행 요구 사항

- 미션은 [python-racingcar](https://github.com/swthewhite/python-racingcar) 저장소를 Fork & Clone하여 시작합니다.
- **기능을 구현하기 전 `docs/README.md`에 구현할 기능 목록을 정리**해 추가합니다.
- **Git의 커밋 단위는 앞 단계에서 `docs/README.md`에 정리한 기능 목록 단위**로 추가합니다.
  - [커밋 메시지 컨벤션](https://gist.github.com/stephenparish/9941e89d80e2bc58a153) 가이드를 참고하여 커밋 메시지를 작성합니다.