# 함수

함수는 재사용 가능한 프로그램의 조각을 말합니다. 이것은 특정 블록의 명령어 덩어리를 묶어 이름을 짓고, 그 이름을 프로그램 어디에서건 사용함으로써 그 블록에 포함된 명령어들을 몇번이고 다시 실행할 수 있게 하는 것입니다. 이를 보고 함수를 **호출한다**라고 합니다. 사실 우리는 이미 앞에서 `len`이나 `range`와 같은 많은 내장 함수들을 사용해 왔습니다.

이러한 함수라는 것은 프로그램을 작성할 때 아마도 가장 중요한 단위가 될 것입니다 \(어떤 프로그래밍 언어에서라도\). 따라서 이 챕터에서는 함수라는 것을 다양한 관점에서 살펴보도록 하겠습니다.

함수는 `def` 키워드를 통해 정의됩니다. `def` 뒤에는 함수의 식별자 이름을 입력하고, 괄호로 감싸여진 함수에서 사용될 인자\(arguments\)의 목록을 입력하며 마지막으로 콜론을 입력하면 함수의 정의가 끝납니다. 새로운 블록이 시작되는 다음 줄부터는 이 함수에서 사용될 명령어들을 입력해 줍니다. 복잡해 보이지만, 아래 예제를 통해 함수를 정의하는 것이 얼마나 간단한지 알아봅시다.

예제 \(`function1.py`로 저장합니다\):

```python
def say_hello():
    # block belonging to the function
    print('hello world')
# End of function

say_hello()  # call the function
say_hello()  # call the function again
```

실행 결과:

```text
$ python function1.py
hello world
hello world
```

**동작 원리**

여기에서는 위에서 설명한 문법을 이용하여 `say_hello`라는 함수를 정의하였습니다. 이 함수는 어떤 인자도 넘겨받지 않으므로, 괄호 내에 매개 변수를 정의하지 않습니다. 함수의 인수란 함수로 넘겨지는 입력값들을 말하며, 함수는 이 값을 처리하여 결과를 넘겨줍니다.

함수를 두 번 호출하는 것은 같은 코드를 두 번 작성하는 것과 같은 효과를 가진다는 것을 알아두세요.

## 함수와 매개 변수

함수를 정의할 때 매개 변수를 지정할 수 있습니다. 매개 변수란 함수로 넘겨지는 값들의 이름을 말하며, 함수는 이 값들을 이용해 무언가를 할 수 있습니다. 매개 변수는 변수와 거의 같이 취급되지만, 매개 변수의 값들은 함수가 호출되어질때 넘겨받은 값들로 채워지며 함수가 실행되는 시점에서는 이미 할당이 완료되어 있다는 점이 다릅니다.

매개 변수는 함수를 정의할 때 괄호 안에 쉼표로 구분하여 지정합니다. 함수를 호출할 때에는, 동일한 방법으로 함수에 값을 넘겨 줍니다. 이 때 함수를 정의할 때 주어진 이름을 **매개변수**라 부르고, 함수에 넘겨준 값들을 **인자**라 부릅니다.

예제 \(function\_param.py 로 저장하세요\):

```python
def print_max(a, b):
    if a > b:
        print(a, 'is maximum')
    elif a == b:
        print(a, 'is equal to', b)
    else:
        print(b, 'is maximum')

# directly pass literal values
print_max(3, 4)

x = 5
y = 7

# pass variables as arguments
print_max(x, y)
```

실행 결과:

```text
$ python function_param.py
4 is maximum
7 is maximum
```

**동작 원리**

여기서는 두 매개 변수 `a`와 `b`를 사용하는 `print_max`라는 함수를 정의합니다. 그리고 간단한 `if..else`문을 이용하여 크기를 비교하고 둘 중에 더 큰 값을 출력합니다.

`print_max` 함수를 처음 호출할 때에는 값을 직접 인자로 입력하여 넘겨주었습니다. 반면 두 번째 호출시에는 변수를 인자로 입력하여 주었습니다. 이것은 `print_max(x, y)`는 변수 `x`에 지정된 값을 변수 `a`에 입력해 주고 변수 `y`의 값을 변수 `b`에 입력해 주는 것을 의미합니다. 따라서 이 함수는 두 경우 모두 동일하게 동작하게 됩니다.

## 지역 변수

여러분이 정의한 함수 안에서 변수를 선언하고 사용할 경우, 함수 밖에 있는 같은 이름의 변수들과 함수 안에 있는 변수들과는 서로 연관이 없습니다. 이러한 변수들을 함수의 **지역\(local\)변수**라고 하며, 그 범위를 변수의 **스코프\(scope\)**라고 부릅니다. 모든 변수들은 변수가 정의되는 시점에서의 블록을 스코프로 가지게 됩니다.

예제 \(function\_local.py 로 저장하세요\):

```python
x = 50

def func(x):
    print('x is', x)
    x = 2
    print('Changed local x to', x)

func(x)
print('x is still', x)
```

실행 결과:

```text
$ python function_local.py
x is 50
Changed local x to 2
x is still 50
```

**동작원리**

먼저 함수의 첫번째 줄에서 x 라는 이름을 가진 변수에 담긴 _값_을 출력합니다. 이 때 함수 정의 위에 정의된 변수의 값을 함수의 매개 변수 _x_로 넘겨받은 값이 출력됩니다.

다음으로, `x`에 값 `2`를 대입합니다. 그러나 `x`는 함수의 지역 변수이므로, 함수 안에서 `x`의 값이 대입된 값으로 변하는 반면 메인 블록의 `x`는 변하지 않고 그대로 남아 있습니다.

프로그램에서 사용된 마지막 `print` 문을 통해 메인 블록의 `x`값을 출력해 보면, 그 이전에 호출된 함수 안에서 시행된 지역 변수값의 변화가 적용되지 않았음을 확인할 수 있습니다.

## `global`문 <a id="global-statement"></a>

함수나 클래스 내부에서 상위 블록에서 선언된 변수의 값을 변경하고 싶을 경우, 파이썬에게 이 변수를 앞으로 지역 변수가 아닌 `전역(global)` 변수로 사용할 것임을 알려 주어야 합니다. 이때 `global`문을 이용합니다. `global`문을 사용하지 않으면, 함수 외부에서 선언된 변수의 값을 함수 내부에서 변경할 수 없습니다.

함수 안에서 동일한 이름으로 선언된 변수가 없을 경우, 함수 밖의 변수값을 함수 안에서 읽고 변경할 수도 있습니다. 그러나, 이것은 프로그램을 읽을 때 변수가 어디서 어떻게 선언되었는지 파악하기 힘들게 만들기 때문에 추천할만한 방법이 아니며, 가능한 이런 경우를 피하시기 바랍니다. `global`문을 사용하면 그 블록의 밖에서 그 변수가 선언되어 있음을 알려 주므로 좀 더 프로그램이 좀 더 명확해집니다.

예제 \(function\_global.py 로 저장하세요\):

```python
x = 50


def func():
    global x

    print('x is', x)
    x = 2
    print('Changed global x to', x)


func()
print('Value of x is', x)
```

실행 결과:

```text
$ python function_global.py
x is 50
Changed global x to 2
Value of x is 2
```

**동작 원리**

`global`문을 통해 `x`가 전역 변수임을 파이썬에게 알려 줍니다. 따라서, 이후로 `x`에 값을 대입하면 메인 블록의 `x`값 또한 변경됩니다.

하나의 `global`문으로 여러 개의 전역 변수를 동시에 지정해 줄 수도 있습니다. `global x, y, z`와 같이 하면 됩니다.

## 기본 인수 <a id="default-arguments"></a>

어떤 특별한 경우, 함수를 호출할 때 인수를 **선택적으로** 넘겨주게 하여 사용자가 값을 넘겨주지 않으면 자동으로 기본값을 사용하도록 하는 것이 편할 때가 있습니다. 이런 경우, 기본 인수값을 지정하면 됩니다. 함수를 선언할 때 원하는 매개 변수 뒤에 대입 연산자 \(`=`\)와 기본값을 입력하여 기본 인수값을 지정합니다.

이 때, 기본 인수값은 반드시 상수이어야 합니다. 좀 더 정확히 말하자면, 불변값이어야 합니다. 불변값에 대해서는 뒤 챕터에서 다룰 것입니다. 일단 지금은, 그래야 한다는 것만 기억해 두기 바랍니다.

예제 \(function\_default.py 로 저장하세요\):

```python
def say(message, times=1):
    print(message * times)

say('Hello')
say('World', 5)
```

실행 결과:

```text
$ python function_default.py
Hello
WorldWorldWorldWorldWorld
```

**동작 원리**

함수 `say`는 지정된 숫자 만큼 문자열을 반복하여 출력하는 합수입니다. 숫자를 지정하지 않으면, 기본값이 적용되어, 문자열이 한 번 출력됩니다. 이 결과는 매개 변수 `times`의 기본 인수값을 `1`로 지정해 줌으로써 얻어집니다.

프로그램에서 처음 `say`를 호출할 때에는 함수에 문자열만 넘겨 주어 한번 출력하게 합니다. 두 번째 호출에서는 문자열과 인수 `5`를 넘겨 주어 함수가 문자열을 5번 반복하여 **말\(say\)**하게 합니다.

> _주의_
>
> 매개 변수 목록에서 마지막에 있는 매개 변수들에만 기본 인수값을 지정해 줄 수 있습니다. 즉, 기본 인수값을 지정하지 않은 매개 변수의 앞에 위치한 매개 변수에만 기본 인수값을 지정할 수 없습니다.
>
> 이것은 함수 를 호출할 때 매개 변수의 위치에 맞춰서 값이 지정되기 때문입니다. 예를 들어, `def func(a, b=5)`는 옳은 함수 정의이지만 `def func(a=5, b)`는 옳지 않습니다.

## 키워드 인수

여러 개의 매개 변수를 가지고 있는 함수를 호출할 때, 그 중 몇 개만 인수를 넘겨주고 싶을 때가 있습니다. 이때 매개 변수의 이름을 지정하여 직접 값을 넘겨줄 수 있는데 이것을 **키워드 인수라** 부릅니다. 함수 선언시 지정된 매개 변수의 순서대로 값을 넘겨주는 것 대신, 매개 변수의 이름\(키워드\)을 사용하여 각각의 매개 변수에 인수를 넘겨 주도록 지정해 줍니다.

키워드 인수를 사용하는 데 두 가지 장점이 있습니다. 첫째로, 인수의 순서를 신경쓰지 않고도 함수를 쉽게 호출할 수 있는 점입니다. 둘째로는, 특정한 매개 변수에만 값을 넘기도록 하여 나머지는 자동으로 기본 인수값으로 채워지게 할 수 있습니다.

예제 \(`function_keyword.py`로 저장하세요\):

```python
def func(a, b=5, c=10):
    print('a is', a, 'and b is', b, 'and c is', c)

func(3, 7)
func(25, c=24)
func(c=50, a=100)
```

실행 결과:

```text
$ python function_keyword.py
a is 3 and b is 7 and c is 10
a is 25 and b is 5 and c is 24
a is 100 and b is 5 and c is 50
```

**동작 원리**

위의 `func`라 이름 지어진 함수는 기본 인수값이 지정되지 않은 한 개의 매개 변수와, 기본 인수값이 지정된 두 개의 매개 변수, 총 세 개의 매개 변수를 가지고 있습니다.

첫 번째 호출 `func(3, 7)`에서, 매개 변수 `a`는 값 `3`, 매개 변수 `b`는 `7`을 넘겨 받으며, `c`에는 기본 인수값 `10`이 주어집니다.

두 번째 호출 `func(25, c=24)`에서는, 첫 번째 인수인 `25`가 변수 `a`에 넘겨집니다. 그리고 매개 변수 `c`는 키워드 인수를 통해 값 `24`가 지정되며, 변수 `b`에는 기본값 `5`가 주어집니다.

세 번째 호출 `func(c=50, a=100)`에서는, 모든 값을 지정하는 데 키워드 인수가 사용됩니다. 함수 정의에는 `a`다음에 `c`가 정의되어 있지만, 키워드 인수를 사용하면 그 순서에 상관없이 `c`를 먼저 지정하고 `a`를 나중에 지정할 수도 있다는 점을 기억하세요.

## VarArgs 매개 변수

가끔 함수에 임의의 개수의 매개 변수를 지정해주고 싶을 때가 있습니다. 이때 VarArgs 매개 변수를 사용합니다. 아래 예제와 같이 별 기호를 사용하여 임의의\(Variable\) 개수의 인수\(Arguments\) 를 표현합니다.

예제 \(`function_varargs.py`로 저장하세요\):

```python
def total(a=5, *numbers, **phonebook):
    print('a', a)

    #iterate through all the items in tuple
    for single_item in numbers:
        print('single_item', single_item)

    #iterate through all the items in dictionary    
    for first_part, second_part in phonebook.items():
        print(first_part,second_part)

print(total(10,1,2,3,Jack=1123,John=2231,Inge=1560))
```

실행 결과:

```text
$ python function_varargs.py
a 10
single_item 1
single_item 2
single_item 3
Inge 1560
John 2231
Jack 1123
None
```

**동작 원리**

앞에 별 기호가 달린 매개 변수, 예를 들어 `*param`과 같이 매개 변수를 지정해 주면 함수에 넘겨진 모든 위치 기반 인수들이 'param' 이라는 이름의 튜플로 묶여서 넘어옵니다.

또 이와 비슷하게 앞에 별 두 개가 달린 매개 변수, 예를 들어 `**param`과 같이 매개 변수를 지정해 주면 함수에 넘겨진 모든 키워드 인수들이 'param' 이라는 이름의 사전으로 묶여서 넘어옵니다.

튜플과 사전에 대해서는 [다음 장](data_structures.md#data-structures)에서 좀 더 자세히 다뤄보도록 하곘습니다.

## `return`문 <a id="return-statement"></a>

`return`문은 함수로부터 되돌아\(return\) 나올 때, 즉 함수를 빠져 나올 때 사용됩니다. 이 때 return 값 처럼 값을 지정해 주면, 함수가 종료될 때 그 값을 반환하도록 할 수 있습니다.

예제 \(`function_return.py`로 저장하세요\):

```python
def maximum(x, y):
    if x > y:
        return x
    elif x == y:
        return 'The numbers are equal'
    else:
        return y

print(maximum(2, 3))
```

실행 결과:

```text
$ python function_return.py
3
```

**동작 원리**

여기에서 사용된 `maximum` 함수는 매개 변수들 중 최대 값을 반환합니다. 위 경우에는 함수에 넘겨진 숫자들 중 최대값을 반환합니다. 간단한 `if..else` 구문을 통해 더 큰 값을 찾고, 최종 값을 **반환\(return\)** 합니다.

`return`문 뒤에 아무 값도 지정하지 않는 경우, `return None`을 실행하는 것과 같습니다. `None`이란 파이썬에서 사용되는 특별한 형식으로 아무것도 없음을 의미합니다. 예를 들면, 어떤 변수의 값이 `None`이라는 것은 변수에 할당된 값이 없다는 것을 의미합니다.

여러분이 `return`문을 함수에 지정하지 않으면, 함수는 끝날 때 자동으로 `return None` 구문을 암시적으로 호출합니다. 아래 예제에서 `return`문이 지정되지 않은 `some_function`이라는 함수를 선언하고 `print(some_function())`을 실행하여 그 결과를 확인해 보시기 바랍니다.

```python
def some_function():
    pass
```

`pass`문은 아무 기능이 없는 구문입니다. 이것은 빈 블록을 지정해 줄 때 사용됩니다.

> 팁: 사실 파이썬에는 '최대값을 찾는' 내장 함수 `max`가 이미 포함되어 있습니다. 따라서 가능하면 이 내장 함수를 사용하시기 바랍니다.

## DocStrings

파이썬은 설명\(Documentation\) 문자열\(String\) 이라고 불리우는, 짧게 줄여서 **DocStrings**라 불리우는 편리한 기능을 가지고 있습니다. DocStrings는 여러분이 만든 프로그램을 알아보기 쉽게 해 주고, 또 후에 프로그램에 대한 설명서를 작성할 때 유용하게 사용될 수 있는 중요한 도구입니다. 아래 예제와 같이, DocString은 프로그램이 실행중일 때도 읽어올 수 있습니다.

예제 \(`function_docstring.py`로 저장하세요\):

```python
def print_max(x, y):
    '''Prints the maximum of two numbers.

    The two values must be integers.'''
    # convert to integers, if possible
    x = int(x)
    y = int(y)

    if x > y:
        print(x, 'is maximum')
    else:
        print(y, 'is maximum')

print_max(3, 5)
print(print_max.__doc__)
```

실행 결과:

```text
$ python function_docstring.py
5 is maximum
Prints the maximum of two numbers.

    The two values must be integers.
```

**동작 원리**

함수에 포함된 첫 논리적 명령행에 적어둔 문자열은 함수의 **DocString**이라고 불리우는 것입니다. 여기에서 설명하는 DocString은 [모듈](modules.md#modules)과 [클래스](oop.md#oop)에도 똑같이 적용됩니다. 각각에 대해서는 각 챕터에서 좀 더 자세히 알아보도록 하겠습니다.

DocString은 일반적으로 첫째줄의 첫문자는 대문자로, 마지막 문자는 마침표로 끝나도록 작성합니다. 그리고 두번째 줄은 비워 두고, 세번째 줄부터는 이것이 어떤 기능을 하는지에 대해 상세하게 작성합니다. 저는 앞으로 여러분이 함수의 DocString를 작성할 때 이 규칙을 따르기를 **강력히 권합니다**.

`print_max` 함수의 DocString은 함수의 `__doc__` 속성을 통해 접근할 수 있습니다 \(**밑줄이 두 개** 임을 다시한번 확인하세요\). doc 은 함수 객체가 갖고 있는 기본 속성입니다. 파이썬에서는 함수를 포함한 모든 것이 객체로 다루어진다는 점을 기억하세요. 이에 대해서는 [클래스](oop.md#oop)에서 좀 더 자세히 알아볼 것입니다.

파이썬에서 `help()`를 이용해 보셨다면, 여러분은 이미 DocString을 본 적이 있는 것입니다! `help()`가 하는 일은 주어진 대상의 `__doc__` 속성을 가져와 화면에 보여주는 것 뿐입니다. 따라서 위에서 만든 함수에 대해서도 마찬가지로 동작합니다. 여러분의 프로그램에 `help(print_max)`라고 한 줄 추가해 보시기 바랍니다. `help`창을 닫으려면 `q`키를 누르세요.

이를 이용하여 여러분의 프로그램에 대한 명세서를 자동으로 만들어주는 프로그램들이 있습니다. 따라서, 저는 여러분이 어떤 함수를 작성하시던지 DocString을 작성할 것을 **강력히 권합니다**. 파이썬과 함께 설치되는 `pydoc` 또한 `help()`와 비슷한 방법으로 DocString을 이용하여 동작합니다.

## 요약

지금까지 함수에 대해 많은 것들을 알아 보았습니다만, 사실 아직 모든 기능을 다 알아본 것은 아닙니다. 그러나, 실제적으로 사용되는 기능에 대해서는 거의 모든 것을 설명해 드렸기 때문에 아마 앞으로 매일매일 프로그램을 작성할 때는 별 무리가 없을 것입니다.

다음으로는, 모듈을 작성하고 사용하는 방법에 대해 알아보도록 하겠습니다.

