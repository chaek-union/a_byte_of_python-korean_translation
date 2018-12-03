# 함수

함수는 재사용 가능한 프로그램의 조각을 말합니다. 이것은 특정 블록의 명령어 덩어리를 묶어 이름을 짓고, 그 이름을 프로그램 어디에서건 사용함으로써 그 블록에 포함된 명령어들을 몇번이고 다시 실행할 수 있게 하는 것입니다. 이를 보고 함수를 **호출한다**라고 합니다. 사실 우리는 이미 앞에서 `len`이나 `range`와 같은 많은 내장 함수들을 사용해 왔습니다.

이러한 함수라는 것은 프로그램을 작성할 때 아마도 가장 중요한 단위가 될 것입니다 (어떤 프로그래밍 언어에서라도). 따라서 이 챕터에서는 함수라는 것을 다양한 관점에서 살펴보도록 하겠습니다.

함수는 `def` 키워드를 통해 정의됩니다. `def` 뒤에는 함수의 식별자 이름을 입력하고, 괄호로 감싸여진 함수에서 사용될 인자(arguments)의 목록을 입력하며 마지막으로 콜론을 입력하면 함수의 정의가 끝납니다. 새로운 블록이 시작되는 다음 줄부터는 이 함수에서 사용될 명령어들을 입력해 줍니다. 복잡해 보이지만, 아래 예제를 통해 함수를 정의하는 것이 얼마나 간단한지 알아봅시다.

예제 (`function1.py`로 저장합니다):

```python
def say_hello():
    # block belonging to the function
    print('hello world')
# End of function

say_hello()  # call the function
say_hello()  # call the function again
```

실행 결과:

```
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

예제 (function_param.py 로 저장하세요):

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

```
$ python function_param.py
4 is maximum
7 is maximum
```

**동작 원리**

여기서는 두 매개 변수 `a`와 `b`를 사용하는 `print_max`라는 함수를 정의합니다. 그리고 간단한 `if..else`문을 이용하여 크기를 비교하고 둘 중에 더 큰 값을 출력합니다.

`print_max` 함수를 처음 호출할 때에는 값을 직접 인자로 입력하여 넘겨주었습니다. 반면 두 번째 호출시에는 변수를 인자로 입력하여 주었습니다. 이것은 `print_max(x, y)`는 변수 `x`에 지정된 값을 변수 `a`에 입력해 주고 변수 `y`의 값을 변수 `b`에 입력해 주는 것을 의미합니다. 따라서 이 함수는 두 경우 모두 동일하게 동작하게 됩니다.

## 지역 변수

여러분이 정의한 함수 안에서 변수를 선언하고 사용할 경우, 함수 밖에 있는 같은 이름의 변수들과 함수 안에 있는 변수들과는 서로 연관이 없습니다. 이러한 변수들을 함수의 **지역(local)변수**라고 하며, 그 범위를 변수의 **스코프(scope)**라고 부릅니다. 모든 변수들은 변수가 정의되는 시점에서의 블록을 스코프로 가지게 됩니다.

예제 (function_local.py 로 저장하세요):

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

```
$ python function_local.py
x is 50
Changed local x to 2
x is still 50
```

**동작원리**

먼저 함수의 첫번째 줄에서 x 라는 이름을 가진 변수에 담긴 *값*을 출력합니다. 이 때 함수 정의 위에 정의된 변수의 값을 함수의 매개 변수 *x*로 넘겨받은 값이 출력됩니다.

다음으로, `x`에 값 `2`를 대입합니다. 그러나 `x`는 함수의 지역 변수이므로, 함수 안에서 `x`의 값이 대입된 값으로 변하는 반면 메인 블록의 `x`는 변하지 않고 그대로 남아 있습니다.

프로그램에서 사용된 마지막 `print` 문을 통해 메인 블록의 `x`값을 출력해 보면, 그 이전에 호출된 함수 안에서 시행된 지역 변수값의 변화가 적용되지 않았음을 확인할 수 있습니다.

## `global`문 {#global-statement}

함수나 클래스 내부에서 상위 블록에서 선언된 변수의 값을 변경하고 싶을 경우, 파이썬에게 이 변수를 앞으로 지역 변수가 아닌 `전역(global)` 변수로 사용할 것임을 알려 주어야 합니다. 이때 `global`문을 이용합니다. `global`문을 사용하지 않으면, 함수 외부에서 선언된 변수의 값을 함수 내부에서 변경할 수 없습니다.

함수 안에서 동일한 이름으로 선언된 변수가 없을 경우, 함수 밖의 변수값을 함수 안에서 읽고 변경할 수도 있습니다. 그러나, 이것은 프로그램을 읽을 때 변수가 어디서 어떻게 선언되었는지 파악하기 힘들게 만들기 때문에 추천할만한 방법이 아니며, 가능한 이런 경우를 피하시기 바랍니다. `global`문을 사용하면 그 블록의 밖에서 그 변수가 선언되어 있음을 알려 주므로 좀 더 프로그램이 좀 더 명확해집니다.

예제 (function_global.py 로 저장하세요):

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

```
$ python function_global.py
x is 50
Changed global x to 2
Value of x is 2
```

**동작 원리**

`global`문을 통해 `x`가 전역 변수임을 파이썬에게 알려 줍니다. 따라서, 이후로 `x`에 값을 대입하면 메인 블록의 `x`값 또한 변경됩니다.

하나의 `global`문으로 여러 개의 전역 변수를 동시에 지정해 줄 수도 있습니다. `global x, y, z`와 같이 하면 됩니다.

## 기본 인수 {#default-arguments}

어떤 특별한 경우, 함수를 호출할 때 인수를 **선택적으로** 넘겨주게 하여 사용자가 값을 넘겨주지 않으면 자동으로 기본값을 사용하도록 하는 것이 편할 때가 있습니다. 이런 경우, 기본 인수값을 지정하면 됩니다. 함수를 선언할 때 원하는 매개 변수 뒤에 대입 연산자 (`=`)와 기본값을 입력하여 기본 인수값을 지정합니다.

이 때, 기본 인수값은 반드시 상수이어야 합니다. 좀 더 정확히 말하자면, 불변값이어야 합니다. 불변값에 대해서는 뒤 챕터에서 다룰 것입니다. 일단 지금은, 그래야 한다는 것만 기억해 두기 바랍니다.

예제 (function_default.py 로 저장하세요):

```python
def say(message, times=1):
    print(message * times)

say('Hello')
say('World', 5)
```

실행 결과:

```
$ python function_default.py
Hello
WorldWorldWorldWorldWorld
```

**동작 원리**

함수 `say`는 지정된 숫자 만큼 문자열을 반복하여 출력하는 합수입니다. 숫자를 지정하지 않으면, 기본값이 적용되어, 문자열이 한 번 출력됩니다. 이 결과는 매개 변수 `times`의 기본 인수값을 `1`로 지정해 줌으로써 얻어집니다.

프로그램에서 처음 `say`를 호출할 때에는 함수에 문자열만 넘겨 주어 한번 출력하게 합니다. 두 번째 호출에서는 문자열과 인수 `5`를 넘겨 주어 함수가 문자열을 5번 반복하여 **말(say)**하게 합니다.

> *주의*
>
> 매개 변수 목록에서 마지막에 있는 매개 변수들에만 기본 인수값을 지정해 줄 수 있습니다. 즉, 기본 인수값을 지정하지 않은 매개 변수의 앞에 위치한 매개 변수에만 기본 인수값을 지정할 수 없습니다.
>
> 이것은 함수 를 호출할 때 매개 변수의 위치에 맞춰서 값이 지정되기 때문입니다. 예를 들어, `def func(a, b=5)`는 옳은 함수 정의이지만 `def func(a=5, b)`는 옳지 않습니다.

## 키워드 인수

여러 개의 매개 변수를 가지고 있는 함수를 호출할 때, 그 중 몇 개만 인수를 넘겨주고 싶을 때가 있습니다. 이때 매개 변수의 이름을 지정하여 직접 값을 넘겨줄 수 있는데 이것을 **키워드 인수라** 부릅니다. 함수 선언시 지정된 매개 변수의 순서대로 값을 넘겨주는 것 대신, 매개 변수의 이름(키워드)을 사용하여 각각의 매개 변수에 인수를 넘겨 주도록 지정해 줍니다.

키워드 인수를 사용하는 데 두 가지 장점이 있습니다. 첫째로, 인수의 순서를 신경쓰지 않고도 함수를 쉽게 호출할 수 있는 점입니다. 둘째로는, 특정한 매개 변수에만 값을 넘기도록 하여 나머지는 자동으로 기본 인수값으로 채워지게 할 수 있습니다.

예제 (`function_keyword.py`로 저장하세요):

```python
def func(a, b=5, c=10):
    print('a is', a, 'and b is', b, 'and c is', c)

func(3, 7)
func(25, c=24)
func(c=50, a=100)
```

실행 결과:

```
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

가끔 함수에 임의의 개수의 매개 변수를 지정해주고 싶을 때가 있습니다. 이때 VarArgs 매개 변수를 사용합니다. 아래 예제와 같이 별 기호를 사용하여 임의의(Variable) 개수의 인수(Arguments) 를 표현합니다.

예제 (`function_varargs.py`로 저장하세요):

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

```
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

튜플과 사전에 대해서는 [다음 장](./data_structures.md#data-structures)에서 좀 더 자세히 다뤄보도록 하곘습니다.

## The `return` statement {#return-statement}

The `return` statement is used to *return* from a function i.e. break out of the function. We can optionally *return a value* from the function as well.

Example (save as `function_return.py`):

<pre><code class="lang-python">{% include "./programs/function_return.py" %}</code></pre>

Output:

<pre><code>{% include "./programs/function_return.txt" %}</code></pre>

**How It Works**

The `maximum` function returns the maximum of the parameters, in this case the numbers supplied to the function. It uses a simple `if..else` statement to find the greater value and then *returns* that value.

Note that a `return` statement without a value is equivalent to `return None`. `None` is a special type in Python that represents nothingness. For example, it is used to indicate that a variable has no value if it has a value of `None`.

Every function implicitly contains a `return None` statement at the end unless you have written your own `return` statement. You can see this by running `print(some_function())` where the function `some_function` does not use the `return` statement such as:

```python
def some_function():
    pass
```

The `pass` statement is used in Python to indicate an empty block of statements.

> TIP: There is a built-in function called `max` that already implements the 'find maximum' functionality, so use this built-in function whenever possible.

## DocStrings

Python has a nifty feature called *documentation strings*, usually referred to by its shorter name *docstrings*. DocStrings are an important tool that you should make use of since it helps to document the program better and makes it easier to understand. Amazingly, we can even get the docstring back from, say a function, when the program is actually running!

Example (save as `function_docstring.py`):

<pre><code class="lang-python">{% include "./programs/function_docstring.py" %}</code></pre>

Output:

<pre><code>{% include "./programs/function_docstring.txt" %}</code></pre>

**How It Works**

A string on the first logical line of a function is the *docstring* for that function. Note that DocStrings also apply to [modules](./modules.md#modules) and [classes](./oop.md#oop) which we will learn about in the respective chapters.

The convention followed for a docstring is a multi-line string where the first line starts with a capital letter and ends with a dot. Then the second line is blank followed by any detailed explanation starting from the third line. You are *strongly advised* to follow this convention for all your docstrings for all your non-trivial functions.

We can access the docstring of the `print_max` function using the `__doc__` (notice the *double underscores*) attribute (name belonging to) of the function. Just remember that Python treats *everything* as an object and this includes functions. We'll learn more about objects in the chapter on [classes](./oop.md#oop).

If you have used `help()` in Python, then you have already seen the usage of docstrings! What it does is just fetch the `__doc__` attribute of that function and displays it in a neat manner for you. You can try it out on the function above - just include `help(print_max)` in your program. Remember to press the `q` key to exit `help`.

Automated tools can retrieve the documentation from your program in this manner. Therefore, I *strongly recommend* that you use docstrings for any non-trivial function that you write. The `pydoc` command that comes with your Python distribution works similarly to `help()` using docstrings.

## Summary

We have seen so many aspects of functions but note that we still haven't covered all aspects of them. However, we have already covered most of what you'll use regarding Python functions on an everyday basis.

Next, we will see how to use as well as create Python modules.
