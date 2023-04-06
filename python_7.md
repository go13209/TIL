# ⭐ Python - 클래스, 인스턴스

## 💡 객체 지향 프로그래밍
> 파이썬은 모두 객체(object)로 이뤄져 있다. 모든 객체(object)는 특정 타입의 인스턴스(instance)이다.
- 객체의 특징
  - 타입(type): 어떤 연산자(operator)와 조작(method)이 가능한가?
  - 속성(attribute): 어떤 상태(데이터)를 가지는가?
  - 조작법(method): 어떤 행위(함수)를 할 수 있는가?
- 객체지향 프로그래밍이란?
  - 프로그램을 여러 개의 독립된 객체들과 그 객체들 간의 상호작용으로 파악하는 프로그래밍 방법
  - 프로그램을 유연하고 변경이 용이하게 만들기 때문에 대규모 소프트웨어 개발에 많이 사용됨
  - 소프트웨어 개발과 보수를 간편하게 하고 보다 직관적인 코드 분석을 가능하게 함
  ```python
  # 객체 지향 프로그래밍 예시
  class Rectangle:
    def __init__(self, x, y):
      self.x = x
      self.y = y
    
    def area(self):
      return self.x * self.y

    def circumference(self):
      return 2 * (self.x + self.y)
  
  r1 = Rectangle(10, 30)
  r1.area()
  r1.circumference()

  r2 = Rectangle(300, 20)
  r2.area()
  r2.circumference()
  ```
  ```
  - 사각형: 클래스(class)
  - 각 사각형(r1, r2): 인스턴스(instance)
  - 사각형의 정보: 속성(attribute)
    - 가로 길이, 세로 길이
  - 사각형의 행동/기능: 메소드(method)
    - 넓이를 구한다, 높이를 구한다
  ```

  ## 💡 사용자 정의 클래스
  - 객체의 틀(클래스)을 가지고 객체(인스턴스)를 생성한다.
  - 클래스: 객체들의 분류(class)
  - 인스턴스: 하나하나의 실체/예(instance)
  - 속성: 특정 데이터 타입/클래스의 객체들이 가지게 될 상태/데이터를 의미
  - 메소드: 특정 데이터 타입/클래스의 객체에 공통적으로 적용 가능한 행위(함수)
  - 객체 비교하기
    - ==
      - 동등한(equal)
      - 변수가 참조하는 객체가 동등한(내용이 같은) 경우 True
      - 두 객체가 같아 보이지만 실제로 동일한 대상을 가리키고 있다고 확인해주는 것은 아님
    - is
      - 동일한(identical)
      - 두 변수가 동일한 객체를 가리키는 경우 True
    ```python
    a = [1, 2, 3]
    b = [1, 2, 3]
    print(a == b, a is b)
    # True False

    a = [1, 2, 3]
    b = a
    print(a == b, a is b)
    # True True
    ```

## 💡 클래스
- 클래스 속성(attribute)
  - 한 클래스의 모든 인스턴스라도 똑같은 값을 가지고 있는 속성
  - 클래스 선언 내부에서 정의
  - \<classname>.\<name>으로 접근 및 할당
- 클래스 메서드
  - 클래스가 사용할 메서드
  - @classmethod 데코레이터를 사용하여 정의
    - 데코레이터: 함수를 어떤 함수로 꾸며서 새로운 기능을 부여
  - 호출 시 첫 번째 인자로 클래스(cls)가 전달됨
- 스태틱 메서드
  - 인스턴스나 클래스를 사용하지 않는 메서드
  - @staticmethod 데코레이터를 사용하여 정의
  - 호출 시 **어떠한 인자로 전달되지 않음**(클래스 및 인스턴스 정보에 접근/수정 불가)
  ```python
  class MyClass:
  
    def method(self):
      return 'instance method', self
    
    @classmethod
    def classmethod(cls):
      return 'class method', cls
    
    @staticmethod
    def staticmethod():
      return 'static method'
  ```
- 클래스 상속
  - 두 클래스 사이 부모-자식 관계를 정립하는 것
  - 부모에 정의된 속성이나 메서드를 활용하거나 `오버라이딩(재정의)`을 하여 활용
    > 메서드 오버라이딩: 상속받은 메서드를 재정의
    > - 상속받은 클래스에서 같은 이름의 메서드를 덮어씀
    > - 부모 클래스의 메서드를 실행시키고 싶은 경우 super를 활용
    - 코드의 재사용성을 높이고 클래스 간의 계층적 관계를 활용함
  - 상속 관련 함수와 메서드
    - isinstance(object, classinfo)
      - classinfo의 instance거나 subclass인 경우 True
    - issubclass(class, classinfo)
      - class가 classinfo의 subclass면 True
      - classinfo는 클래스 객체의 튜플일 수 있으며 classinfo의 모든 항목을 검사
    - super()
      - 자식 클래스에서 부모 클래스를 사용하고 싶은 경우 활용
  - 다중 상속
    - 파이썬은 두 개 이상의 클래스를 상속받을 수 있음
    - 상속받은 모든 클래스의 요소를 활용 가능함
    - 중복된 속성이나 메서드가 있는 경우 상속 순서에 의해 결정됨

## 💡 인스턴스
- 인스턴스 변수
  - 인스턴스가 개인적으로 가지고 있는 속성(attribute)
  - 각 인스턴스들의 고유한 변수
- 생성자 메소드에서 self.\<name>으로 정의
- 인스턴스가 생성된 이후 \<instance>.\<name>으로 접근 및 할당
  ```python
  class Person:
    def __init__(self, name):
      self.name = name # 인스턴스 변수 정의

  john = Person('john')
  print(john.name) # john # 인스턴스 변수 접근 및 할당

  john.name = 'John Kim'
  print(john.name) # John Kim # 인스턴스 변수 접근 및 할당
  ```
- 인스턴스 메소드
  - 인스턴스 변수를 사용하거나 인스턴스 변수에 값을 설정하는 메소드
  - 클래스 내부에 정의되는 메소드의 기본
  - 호출 시 첫 번째 인자로 인스턴스 자기 자신(self)이 전달됨
- self
  - 인스턴스 자기 자신
  - 파이썬에서 인스턴스 메소드는 호출 시 첫 번째 인자로 인스턴스 자신이 전달되게 설계
    - 매개변수 이름으로 self를 첫 번째 인자로 정의
    - 다른 단어로 써도 작동하지만 파이썬의 암묵적인 규칙
- **생성자(constructor) 메소드**
  - 인스턴스 객체가 생성될 때 자동으로 호출되는 메소드
  - 인스턴스 변수들의 초깃값을 설정
    - 인스턴스 생성
    - \_\_init__ 메소드 자동 호출
- **소멸자(destructor) 메소드**
  - 인스턴스 객체가 소멸(파괴)되기 직전에 호출되는 메소드
- 매직 메소드
  - Double underscore(__)가 있는 메소드는 특수한 동작을 위해 만들어진 메소드로 스페셜 메소드 혹은 매직 메소드라고 불림
  - 특정 상황에 자동으로 불리는 메소드
  - 예시
    - 객체의 특수 조작 행위를 지정(함수, 연산자 등)
      - \_\_str__ : 해당 객체의 출력 형태를 지어
        - 프린트 함수를 호출할 때 자동으로 호출
        - 어떤 인스턴스를 출력하면 \_\_str__의 return 값이 출력
      - \_\_gt__ : 부등호 연산자(>, greater than)
  ```python
  class Circle:
    
    def __init__(self, r):
      self.r = r
    
    def area(self):
      return 3.14 * self.r * self.r
    
    def __str__(self):
      return f'[원] radius: {self.r}
    
    def __gt__(self, other):
      return self.r > other.r

  c1 = circle(10)
  c2 = circle(1)
  
  print(c1) # [원] radius: 10
  print(c2) # [원] radius: 1

  c1 > c2 # True
  c1 < c2 # False
  ```
