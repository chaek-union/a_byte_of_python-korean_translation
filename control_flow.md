# 흐름 제어 {#control-flow}

지금까지 우리가 본 파이썬 프로그램들은 전부 맨 윗줄부터 차례대로 한줄씩 실행되기만 하는 것들 뿐이었습니다. 이러한 실행 흐름을 바꿀 수 있다면 어떨까요? 예를 들어, 프로그램이 현재 시간에 따라 'Good Morning' 혹은 'Good Evening’을 출력하는 결정을 내리도록 할 수 있게 하면 좋지 않을까요?

흐름 제어문을 활용하면 이러한 프로그램을 제작할 수 있습니다. 파이썬에서는 `if`, `for`, `while` 이라는 세 종류의 흐름 제어문을 사용할 수 있습니다.

## `if`문

`if`문은 조건을 판별할 때 사용됩니다. *if*(만약) 조건이 참이라면, *if 블록의* 명령문을 실행하며 *else* (아니면) *else 블록의* 명령문을 실행합니다. 이 때 *else* 조건절은 생략이 가능합니다.

예제 (if.py 로 저장하세요):
```python
number = 23
guess = int(input('Enter an integer : '))

if guess == number:
    # New block starts here
    print('Congratulations, you guessed it.')
    print('(but you do not win any prizes!)')
    # New block ends here
elif guess < number:
    # Another block
    print('No, it is a little higher than that')
    # You can do whatever you want in a block ...
else:
    print('No, it is a little lower than that')
    # you must have guessed > number to reach here

print('Done')
# This last statement is always executed,
# after the if statement is executed.
```

실행 결과:
```
$ python if.py
Enter an integer : 50
No, it is a little lower than that
Done

$ python if.py
Enter an integer : 22
No, it is a little higher than that
Done

$ python if.py
Enter an integer : 23
Congratulations, you guessed it.
(but you do not win any prizes!)
Done
```

**동작 원리**

이 프로그램에서는, 사용자로부터 숫자를 입력받아 그 숫자가 프로그램에 지정된 숫자와 같은지 확인합니다. 먼저 `number` 변수에 원하는 숫자를 넣습니다. 여기서는 `23`입니다. 그리고, `input()` 함수를 통해 사용자로부터 입력을 받습니다. 여기서 함수란 재사용 가능한 프로그램 조각을 의미합니다. [다음 장](./functions.md#functions)에서, 함수에 대해 좀 더 자세히 배울 것입니다.

파이썬에 내장된 `input` 함수에 문자열을 넣어 주면 화면에 이 문자열이 출력되며, 또 사용자의 입력을 기다리게 됩니다. 이제 사용자가 무엇인가를 입력하고 enter 키를 누르면, `input()` 함수는 사용자가 입력한 것을 문자열의 형태로 반환해 줍니다. 이제 `int`를 이용하여 이것을 정수형으로 변환한 뒤, 그 값을 변수 `guess`에 대입합니다. 사실 여기에서 사용된 `int`는 클래스라고 불리우는 것입니다만, 일단 여기서는 이것이 문자열을 숫자형으로 변환해 준다는 것만 기억하셔도 됩니다 (다만 이 때 사용된 문자열은 올바른 숫자를 포함하고 있어야 합니다).

다음으로, 사용자가 입력한 숫자와 우리가 고른 숫자를 비교합니다. 만약 이 두 숫자가 같으면, 성공했다는 메시지를 화면에 출력합니다. 이때 들여쓰기를 이용하여 어디부터 어디까지가 이 블록에 해당하는지를 표시했다는 것을 확인하세요. 이러한 이유로 파이썬에서 들여쓰기는 굉장히 중요합니다. 앞서 말씀드렸듯이 여러분이 "일관성 있게 들여쓰는 습관"에 익숙해져 있었으면 좋겠네요. 이미 그렇게 하고 계시지요?

또한 `if`문의 뒷부분에 콜론(`:`)이 붙어 있는 것을 확인하세요. 콜론은 그 다음 줄부터 새로운 블록이 시작된다는 것을 의미합니다.

이제, 사용자가 입력한 숫자가 우리가 고른 숫자에 비해 작다면, 사용자에게 좀 더 큰 숫자를 입력하라고 알려 줍니다. 여기에 사용된 것은 `elif` 절인데, 이것은 두 개의 if 문을 중첩해서 사용해야 할 경우 (즉 `if else`를 쓰고 `else` 밑에 또 다시 `if else`를 써야 될 경우) 이것을 `if-elif-else`로 한번에 줄여서 쓸 수 있게 해 주는 것입니다. 즉 `elif`는 프로그래밍을 좀 더 쉽게 해 주고 더 많은 들여쓰기를 해야 하는 수고도 줄여 줍니다.

`elif`와 `else`문을 사용할 경우, 논리적 명령행의 마지막에는 항상 콜론이 붙어 있어야 하며 그 다음 줄에는 다른 들여쓰기 단계로 시작되는 새로운 명령문 블록이 시작되어야 합니다.

또한 `if`문의 if-block안에 또다른 `if`문을 넣고, 또 넣고 하는 식으로 작성할 수도 있습니다. 이 경우 이것을 중첩 `if`문이라 부릅니다.

`elif`와 `else`절은 생략이 가능합니다. 최소한의 올바른 `if`문 사용법은 다음과 같습니다.

```python
if True:
    print('Yes, it is true')
```

`if` - `elif` - `else` 문의 실행이 끝나면, 파이썬은 `if`문을 담고 있는 블록의 다음 줄부터 실행을 재개합니다. 위 예제의 경우 그 블록은 최상위 블록 (프로그램이 실행된 시점의 블록)이 되며, 따라서 그 다음에 실행될 명령문은 `print('Done')`이 됩니다. 그 이후는 프로그램의 끝이므로 실행이 종료됩니다.

지금 여러분이 본 것은 굉장히 간단한 프로그램이지만, 이를 통해서도 충분히 많은 것들에 대해 이야기했습니다. 하지만 이 모든 내용은 상당히 직관적입니다 (만약 여러분이 C/C++ 경험이 있다면 훨씬 더 쉽다고 느껴지기까지 할 것입니다). 지금 당장은 여러분이 이 모든 내용을 익혀야 하겠지만, 몇번 연습을 해보고 나면 아마 좀 더 편하게 받아들여질 것이며 곧 '자연스럽게' 여기게 될 것입니다.

> **C/C++ 프로그래머를 위한 주석**
>
> 파이썬에는 `switch`문이 없습니다. 대신 `if..elif..else` 문을 이용하여야 합니다. (몇몇 상황에서는 [사전](./data_structures.md#dictionary)을 이용하는 것이 편리합니다)

## while 문

The `while` statement allows you to repeatedly execute a block of statements as long as a condition is true. A `while` statement is an example of what is called a *looping* statement. A `while` statement can have an optional `else` clause.

`while`문은 특정 조건이 참일 경우 계속해서 블록의 명령문들을 반복하여 실행할 수 있도록 합니다. `while`문은 *반복문*의 한 예입니다. 또한 `while`문에는 `else` 절이 따라올 수 있습니다.

예제 (`while.py`로 저장하세요):

```python
number = 23
running = True

while running:
    guess = int(input('Enter an integer : '))

    if guess == number:
        print('Congratulations, you guessed it.')
        # this causes the while loop to stop
        running = False
    elif guess < number:
        print('No, it is a little higher than that.')
    else:
        print('No, it is a little lower than that.')
else:
    print('The while loop is over.')
    # Do anything else you want to do here

print('Done')
```

실행 결과:
```
$ python while.py
Enter an integer : 50
No, it is a little lower than that.
Enter an integer : 22
No, it is a little higher than that.
Enter an integer : 23
Congratulations, you guessed it.
The while loop is over.
Done
```


**동작 원리**

이 프로그램 또한 숫자 알아맞히기 게임이지만 더 나은 점은 사용자가 답을 맞출 때까지 계속 숫자를 입력할 수 있다는 것입니다. 즉, 이전 섹션에서 작성한 프로그램처럼 다른 숫자를 입력해 보기 위해 프로그램을 또 실행시킬 필요가 없습니다. 이 예제는 `while`문의 사용법을 잘 보여줍니다.

먼저 while 루프가 실행되기 전 변수 `running`이 `True`로 설정되어 있으므로, `while`문에 딸려 있는 *while 블록*이 실행되며 `raw_input`과 `if`문이 실행됩니다. 이 블록의 실행이 끝나면, `while` 문은 변수 `running`의 값을 다시 한번 확인합니다. 이 값이 참인 경우 while 블록을 다시 한번 실행하며, 거짓인 경우 else 블록을 실행한 뒤 루프를 빠져나와 다음 명령문이 실행됩니다.

`else` 블록은 `while` 루프 조건이 `False`인 경우 실행됩니다. 물론 루프 조건을 처음으로 확인했을 경우에도 이 블록이 실행될 수 있습니다. `while` 루프에 `else` 절이 딸려있는 경우, `break` 명령으로 루프를 강제로 빠져나오지 않는 이상 이 블록은 항상 실행되게 됩니다.

여기서 `True`와 `False`라는 값들은 불리언 형식이라고 불리우며, 각각은 숫자 `1`과 `0`으로 간주됩니다.

> **C/C++ 프로그래머를 위한 주석**
> 
> `while` 루프에 `else` 절이 사용될 수 있음을 기억하세요.

## The `for` loop

The `for..in` statement is another looping statement which *iterates* over a sequence of objects i.e. go through each item in a sequence. We will see more about [sequences](./data_structures.md#sequence) in detail in later chapters. What you need to know right now is that a sequence is just an ordered collection of items.

Example (save as `for.py`):

<pre><code class="lang-python">{% include "./programs/for.py" %}</code></pre>

Output:

<pre><code>{% include "./programs/for.txt" %}</code></pre>

**How It Works**

In this program, we are printing a *sequence* of numbers. We generate this sequence of numbers using the built-in `range` function.

What we do here is supply it two numbers and `range` returns a sequence of numbers starting from the first number and up to the second number. For example, `range(1,5)` gives the sequence `[1, 2, 3, 4]`. By default, `range` takes a step count of 1. If we supply a third number to `range`, then that becomes the step count. For example, `range(1,5,2)` gives `[1,3]`. Remember that the range extends *up to* the second number i.e. it does *not* include the second number.

Note that `range()` generates only one number at a time, if you want the full list of numbers, call `list()` on the `range()`, for example, `list(range(5))` will result in `[0, 1, 2, 3, 4]`. Lists are explained in the [data structures chapter](./data_structures.md#data-structures).

The `for` loop then iterates over this range - `for i in range(1,5)` is equivalent to `for i in [1, 2, 3, 4]` which is like assigning each number (or object) in the sequence to i, one at a time, and then executing the block of statements for each value of `i`.  In this case, we just print the value in the block of statements.

Remember that the `else` part is optional. When included, it is always executed once after the `for` loop is over unless a [break](#break-statement) statement is encountered.

Remember that the `for..in` loop works for any sequence. Here, we have a list of numbers generated by the built-in `range` function, but in general we can use any kind of sequence of any kind of objects! We will explore this idea in detail in later chapters.

> **Note for C/C++/Java/C# Programmers**
> 
> The Python `for` loop is radically different from the C/C++ `for` loop. C# programmers will note that the `for` loop in Python is similar to the `foreach` loop in C#. Java programmers will note that the same is similar to `for (int i : IntArray)` in Java 1.5.
> 
> In C/C++, if you want to write `for (int i = 0; i < 5; i++)`, then in Python you write just `for i in range(0,5)`. As you can see, the `for` loop is simpler, more expressive and less error prone in Python.

## The break Statement {#break-statement}

The `break` statement is used to *break* out of a loop statement i.e. stop the execution of a looping statement, even if the loop condition has not become `False` or the sequence of items has not been completely iterated over.

An important note is that if you *break* out of a `for` or `while` loop, any corresponding loop `else` block is **not** executed.

Example (save as `break.py`):

<pre><code class="lang-python">{% include "./programs/break.py" %}</code></pre>

Output:

<pre><code>{% include "./programs/break.txt" %}</code></pre>

**How It Works**

In this program, we repeatedly take the user's input and print the length of each input each
time. We are providing a special condition to stop the program by checking if the user input is
`'quit'`. We stop the program by *breaking* out of the loop and reach the end of the program.

The length of the input string can be found out using the built-in `len` function.

Remember that the `break` statement can be used with the `for` loop as well.

**Swaroop's Poetic Python**

The input I have used here is a mini poem I have written:

```
Programming is fun
When the work is done
if you wanna make your work also fun:
    use Python!
```

## The `continue` Statement {#continue-statement}

The `continue` statement is used to tell Python to skip the rest of the statements in the current loop block and to *continue* to the next iteration of the loop.

Example (save as `continue.py`):

<pre><code class="lang-python">{% include "./programs/continue.py" %}</code></pre>

Output:

<pre><code>{% include "./programs/continue.txt" %}</code></pre>

**How It Works**

In this program, we accept input from the user, but we process the input string only if it is at least 3 characters long. So, we use the built-in `len` function to get the length and if the length is less than 3, we skip the rest of the statements in the block by using the `continue` statement. Otherwise, the rest of the statements in the loop are executed, doing any kind of processing we want to do here.

Note that the `continue` statement works with the `for` loop as well.

## Summary

We have seen how to use the three control flow statements - `if`, `while` and `for` along with their associated `break` and `continue` statements. These are some of the most commonly used parts of Python and hence, becoming comfortable with them is essential.

Next, we will see how to create and use functions.
