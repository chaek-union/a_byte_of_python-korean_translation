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

## `for` 반복문

`for..in`문은 객체의 열거형(Sequence)을 따라서 반복하여 실행할 때 사용되는 파이썬에 내장된 또 하나의 반복문으로, 열거형에 포함된 각 항목을 하나씩 거쳐가며 실행합니다. [열거형](./data_structures.md#sequence)에 대해서는 이후에 좀 더 자세히 다룰 것입니다. 일단 여기서는, 열거형이란 여러 항목이 나열된 어떤 목록을 의미한다고 생각하시기 바랍니다.

예제 (`for.py`로 저장하세요):

```python
for i in range(1, 5):
    print(i)
else:
    print('The for loop is over')
```

실행 결과:

```
$ python for.py
1
2
3
4
The for loop is over
```

**동작 원리**

이 프로그램은 화면상에 숫자의 나열을 출력합니다. 파이썬에 내장된 `range` 함수를 통해 이러한 숫자의 나열을 생성합니다.

여기서는 `range` 함수에 두 개의 숫자를 넣어 주었으며, 그러면 이 함수는 첫 번째 숫자 이상, 그리고 두 번째 숫자 미만까지의 숫자 목록(리스트)을 반환합니다 (리스트는 자료 구조 챕터에서 좀 더 자세히 설명할 것입니다). 예를 들어, `range(1,5)`는 리스트 `[1, 2, 3, 4]`를 반환합니다. 기본적으로, `range`는 1씩 증가하는 숫자의 리스트를 반환합니다. 그러나 `range`에 세 번째 숫자를 입력하면, 이 세 번째 숫자만큼씩 증가하는 숫자들의 리스트를 얻을 수 있습니다. 예를 들어, `range(1,5,2)`는 `[1,3]`을 반환합니다. 반환되는 리스트는 두번째 숫자 **미만**까지 반환되며, **이하**까지 반환되는 것이 아니라는 점을 꼭 기억하세요.

`range()` 함수는 호출될 때 해당 범위 내의 숫자를 하나만 생성하기 때문에 전체 리스트를 만들고 싶다면 `list()`와 `range()`를 함께 사용해야 합니다. 예를 들어 `list(range(5))`는 `[0, 1, 2, 3, 4]`를 반환합니다. 리스트는 [자료구조](./data_structures.md#data-structures)에서 상세히 설명합니다.

위 예제의 `for` 반복문은 `range` 함수에서 반환된 리스트를 따라 반복하여 실행됩니다. 즉, `for i in range(1,5)`는 `for i in [1, 2, 3, 4]`와 같습니다. 이것은 리스트에 들어 있는 각각의 숫자 (각 숫자는 곧 객체이기도 합니다)를 한번에 하나씩 `i`에 대입하고, 이렇게 대입된 각 `i`값을 이용하여 for에 딸린 블록을 실행합니다. 이 경우, for 블록에서 하는 일은 단순히 `i`값을 화면에 출력해 주는 것입니다.

`else` 절을 사용할 수도 있습니다. 만약 `else`가 포함된다면 [break](#break-statement) 문을 통해 `for` 반복문을 빠져나온 후 실행됩니다.

`for..in` 루프는 어떤 종류의 열거형 자료형과도 함께 사용될 수 있습니다. 여기서는 `range`라는 내장 함수를 통해 숫자 리스트를 생성하여 사용하였지만, 일반적으로는 객체를 담고 있는 어떤 종류의 열거형이나 모두 사용이 가능합니다! 추후에 이에 대해 좀 더 자세히 다뤄 보겠습니다.

> **C/C++/Java/C# 프로그래머를 위한 주석**
> 
> 파이썬의 `for` 반복문은 C/C++ 에서 제공하는 `for` 반복문과는 근본적으로 다릅니다. 파이썬의 `for`는 차라리 C#의 `foreach` 반복문과 비슷하며, Java 1.5의 `for (int i : IntArray)`와 비슷합니다.
> 
> C/C++처럼 `for (int i = 0; i < 5; i)`와 같이 사용하고 싶은 경우, 파이썬에서는 단순히 `for i in range(0,5)`라고 입력하기만 하면 됩니다. 보시다시피, 파이썬의 `for` 반복문은 더 단순하며, 더 보기 좋고 오류가 발생하기도 어렵습니다.

## break 문 {#break-statement}

`break`문은 루프 문을 강제로 빠져나올 때, 즉 아직 루프 조건이 `False`가 되지 않았거나 열거형의 끝까지 루프가 도달하지 않았을 경우에 루프 문의 실행을 강제로 정지시키고 싶을 때 사용됩니다.

중요한 점은 만약 여러분이 `break`문을 써서 `for` 반복문이나 `while` 반복문을 빠져나왔을 경우, 반복문에 딸린 `else` 블록은 실행되지 않습니다.

예제 (`break.py`로 저장하세요):

```python
while True:
    s = input('Enter something : ')
    if s == 'quit':
        break
    print('Length of the string is', len(s))
print('Done')
```

실행 결과:
```
$ python break.py
Enter something : Programming is fun
Length of the string is 18
Enter something : When the work is done
Length of the string is 21
Enter something : if you wanna make your work also fun:
Length of the string is 37
Enter something : use Python!
Length of the string is 11
Enter something : quit
Done
```

**동작 원리**

이 프로그램에서는 사용자의 입력을 반복해서 받고, 입력받은 문자열의 길이를 출력합니다. 다만 사용자가 입력한 문자열이 `'quit'`일 경우, `break`문으로 반복문을 빠져나와 프로그램을 정지하도록 특별한 조건을 넣어 주었습니다.

입력받은 문자열의 길이는 내장함수 `len`을 이용하여 계산할 수 있습니다.

`break`문은 `for` 반복문에서도 사용할 수 있습니다.

**Swaroop의 파이썬 시**

예제에서 입력한 것은 이 책의 저자가 작성한 작은 시입니다.

```
Programming is fun
When the work is done
if you wanna make your work also fun:
    use Python!
```

## `continue`문 {#continue-statement}

`continue`문은 현재 실행중인 반복문의 나머지 명령을 실행하지 않고 곧바로 다음 반복(iteration)으로 넘어가도록 합니다.

예제 (continue.py 로 저장하세요):

```python
while True:
    s = input('Enter something : ')
    if s == 'quit':
        break
    if len(s) < 3:
        print('Too small')
        continue
    print('Input is of sufficient length')
    # Do other kinds of processing here...
```

실행 결과:
```
$ python continue.py
Enter something : a
Too small
Enter something : 12
Too small
Enter something : abc
Input is of sufficient length
Enter something : quit
```

**동작 원리**

이 프로그램에서는 사용자로부터 입력을 받습니다만, 입력받은 문자열의 길이가 적어도 3 이상인 경우에만 문자열을 처리합니다. 즉, 내장함수 `len`을 통해 입력받은 문자열의 길이를 알아낸 후 그 길이가 3보다 작으면, `continue`문을 이용하여 그 이하의 명령문을 실행하지 않고 다음 루프로 넘어가도록 합니다. 입력받은 문자열의 길이가 3 이상일 경우에만 그 이하의 명령문이 실행되고, 지정된 작업이 실행됩니다.

`continue`문은 `for` 반복문에서도 사용할 수 있습니다.

## 요약

이 장에서는 `if`, `while`, `for` 세 종류의 흐름 제어문에 대해 배워 보았습니다. 또한 그와 같이 이용할 수 있는 `break`문과 `continue`문에 대해서도 배웠습니다. 이 명령문들은 파이썬에서 가장 많이 사용되기 때문에 익숙해질 필요가 있습니다.

다음으로, 함수를 만들고 사용하는 방법에 대해 배워 보겠습니다.
