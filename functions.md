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

## The `global` statement {#global-statement}

If you want to assign a value to a name defined at the top level of the program (i.e. not inside any kind of scope such as functions or classes), then you have to tell Python that the name is not local, but it is *global*. We do this using the `global` statement. It is impossible to assign a value to a variable defined outside a function without the `global` statement.

You can use the values of such variables defined outside the function (assuming there is no variable with the same name within the function). However, this is not encouraged and should be avoided since it becomes unclear to the reader of the program as to where that variable's definition is. Using the `global` statement makes it amply clear that the variable is defined in an outermost block.

Example (save as `function_global.py`):

<pre><code class="lang-python">{% include "./programs/function_global.py" %}</code></pre>

Output:

<pre><code>{% include "./programs/function_global.txt" %}</code></pre>

**How It Works**

The `global` statement is used to declare that `x` is a global variable - hence, when we assign a value to `x` inside the function, that change is reflected when we use the value of `x` in the main block.

You can specify more than one global variable using the same `global` statement e.g. `global x, y, z`.

## Default Argument Values {#default-arguments}

For some functions, you may want to make some parameters *optional* and use default values in case the user does not want to provide values for them. This is done with the help of default argument values. You can specify default argument values for parameters by appending to the parameter name in the function definition the assignment operator (`=`) followed by the default value.

Note that the default argument value should be a constant. More precisely, the default argument value should be immutable - this is explained in detail in later chapters. For now, just remember this.

Example (save as `function_default.py`):

<pre><code class="lang-python">{% include "./programs/function_default.py" %}</code></pre>

Output:

<pre><code>{% include "./programs/function_default.txt" %}</code></pre>

**How It Works**

The function named `say` is used to print a string as many times as specified. If we don't supply a value, then by default, the string is printed just once. We achieve this by specifying a default argument value of `1` to the parameter `times`.

In the first usage of `say`, we supply only the string and it prints the string once. In the second usage of `say`, we supply both the string and an argument `5` stating that we want to *say* the string message 5 times.

> *CAUTION*
> 
> Only those parameters which are at the end of the parameter list can be given default argument
> values i.e. you cannot have a parameter with a default argument value preceding a parameter without
> a default argument value in the function's parameter list.
> 
> This is because the values are assigned to the parameters by position. For example,`def func(a,
> b=5)` is valid, but `def func(a=5, b)` is *not valid*.

## Keyword Arguments

If you have some functions with many parameters and you want to specify only some of them, then you can give values for such parameters by naming them - this is called *keyword arguments* - we use the name (keyword) instead of the position (which we have been using all along) to specify the arguments to the function.

There are two advantages - one, using the function is easier since we do not need to worry about the order of the arguments. Two, we can give values to only those parameters to which we want to, provided that the other parameters have default argument values.

Example (save as `function_keyword.py`):

<pre><code class="lang-python">{% include "./programs/function_keyword.py" %}</code></pre>

Output:

<pre><code>{% include "./programs/function_keyword.txt" %}</code></pre>

**How It Works**

The function named `func` has one parameter without a default argument value, followed by two parameters with default argument values.

In the first usage, `func(3, 7)`, the parameter `a` gets the value `3`, the parameter `b` gets the value `7` and `c` gets the default value of `10`.

In the second usage `func(25, c=24)`, the variable `a` gets the value of 25 due to the position of the argument. Then, the parameter `c` gets the value of `24` due to naming i.e. keyword arguments. The variable `b` gets the default value of `5`.

In the third usage `func(c=50, a=100)`, we use keyword arguments for all specified values. Notice that we are specifying the value for parameter `c` before that for `a` even though `a` is defined before `c` in the function definition.

## VarArgs parameters

Sometimes you might want to define a function that can take _any_ number of parameters, i.e. **var**iable number of **arg**uments, this can be achieved by using the stars (save as `function_varargs.py`):

<pre><code class="lang-python">{% include "./programs/function_varargs.py" %}</code></pre>

Output:

<pre><code>{% include "./programs/function_varargs.txt" %}</code></pre>

**How It Works**

When we declare a starred parameter such as `*param`, then all the positional arguments from that point till the end are collected as a tuple called 'param'.

Similarly, when we declare a double-starred parameter such as `**param`, then all the keyword arguments from that point till the end are collected as a dictionary called 'param'.

We will explore tuples and dictionaries in a [later chapter](./data_structures.md#data-structures).

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
