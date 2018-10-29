# 연산자와 수식 {#op-exp}

여러분이 앞으로 작성하게 될 모든 명령문 (논리적 명령행)은 _수식_을 포함하게 될 것입니다. 아주 간단한 수식의 한 예는 `2 + 3` 입니다. 수식은 연산자와 피연산자로 나눌 수 있습니다.

_연산자_란 무언가를 계산할 때 쓰이는 한 기능을 뜻하며, `+`와 같이 기호로 나타내어지거나 또는 특별한 키워드로 나타내어집니다. 또 연산자는 계산에 사용될 데이터를 필요로 하는데, 이들을 _피연산자_라고 부릅니다. 이 경우, 피연산자는 `2`와 `3`이 됩니다.

## 연산자

이제 연산자의 사용법에 대해 알아보도록 하겠습니다.

파이썬 인터프리터 프롬프트 상에서도 수식을 계산할 수 있습니다. 다음과 같이 파이썬 인터프리터 프롬프트 상에서 `2 + 3`이라는 수식을 입력해 봅시다.

```python
>>> 2 + 3
5
>>> 3 * 5
15
>>>
```

이제 파이썬에서 사용 가능한 연산자들의 종류에 대해 간단히 알아봅시다.

- `+` (덧셈 연산자)
    - 두 객체를 더합니다.
    - `3 + 5` 는 `8`을 반환합니다. `'a' + 'b'`는 `'ab'`를 반환합니다.

- `-` (뺄셈 연산자)
    - 한 숫자에서 다른 숫자를 뺍니다. 첫 번째 피연산자가 주어지지 않으면, 0으로 간주됩니다.
    - `-5.2`는 음수를 표현합니다. `50 - 24`는 `26`을 반환합니다.

- `*` (곱셈 연산자)
    - 두 숫자의 곱 혹은 지정된 숫자만큼 반복된 문자열을 반환합니다.
    - `2 * 3`은 `6`을 반환합니다. `'la' * 3`은 `'lalala'`를 반환합니다.

- `**` (거듭제곱 연산자)
    - x 의 y제곱을 반환합니다.
    - `3 ** 4`는 `81`을 반환합니다 (이 값은 `3 * 3 * 3 * 3`과 같습니다).

- `/` (나눗셈 연산자)
    - x를 y로 나눈 몫을 반환합니다.
    - `13 / 3`은 `4.333333333333333`를 반환합니다.

- `//` (정수 나눗셈 연산자)
    - x를 y로 나눈 몫의 소숫점을 내림해서 가장 가까운 정수를 반환합니다. 계산식에 실수가 하나 이상 포함되면 실수로 반환됩니다.
    - `13 // 3`은 `4`를 반환합니다.
    - `-13 // 3`은 `-5`를 반환합니다.
    - `9//1.81`은 `4.0`를 반환합니다.

- `%` (나머지 연산자)
    - x를 y로 나눈 나머지를 반환합니다.
    - `13 % 3`은 `1`을 반환합니다. `-25.5 % 2.25`는 `1.5`를 반환합니다.

- `<<` (왼쪽 시프트 연산자)
    - 지정된 숫자에 대해 지정된 비트 수 만큼 오른쪽 시프트 연산합니다.(각각의 수는 메모리에서 비트나 0과 1과 같은 이진수에 해당됩니다.)
    - `2 << 2`는 `8`을 반환합니다. `2`는 이진수 `10`으로 표현됩니다.
    - 이것을 왼쪽으로 2비트 시프트 연산하면 이진수 `1000`이 되고, 이것을 정수로 표현하면 `8`이 됩니다.

- `>>` (오른쪽 시프트 연산자)
    - 지정된 숫자에 대해 지정된 비트 수 만큼 오른쪽 시프트 연산합니다.
    - `11 >> 1`은 `5`를 반환합니다.
    - `11`은 이진수 `1011`로 표현됩니다. 이것으로 오른쪽으로 1비트 시프트 연산하면 이진수 `101`이 되고, 이것을 정수로 표현하면 `5`가 됩니다.

- `&` (비트 AND 연산자)
    - 비트 AND 연산값을 반환합니다.
    - `5 & 3`은 `1`을 반환합니다.

- `|` (비트 OR 연산자)
    - 비트 OR 연산값을 반환합니다.
    - `5 | 3`은 `7`을 반환합니다.

- `^` (비트 XOR 연산자)
    - 비트 XOR 연산값을 반환합니다.
    - `5 ^ 3`은 `6`을 반환합니다.

- `~` (비트 반전 연산자)
    - 숫자 x의 비트 반전 연산값 `-(x+1)`을 반환합니다.
    - `~5`는 `-6`을 반환합니다. 자세한 사항은 http://stackoverflow.com/a/11810203 을 읽어 보시기 바랍니다.

- `<` (작음)
    - x가 y보다 작은지 여부를 반환합니다. 모든 비교 연산자는 `True`또는 `False`을 반환합니다. 각 반환값의 첫글자는 대문자라는 점에 유의하세요.
    - `5 < 3`는 `False`를 반환합니다. `3 < 5`는 `True`를 반환합니다.
    - 다음과 같이 여러 숫자에 대해 한꺼번에 비교 연산을 수행할 수 있습니다. `3 < 5 < 7`은 `True`를 반환합니다.

- `>` (큼)
    - x가 y보다 큰지 여부를 반환합니다.
    - `5 > 3`은 `True`를 반환합니다. 만약 두 피연산자가 모두 숫자라면, 같은 숫자형으로 변환된 후 크기를 비교합니다. 피연산자가 숫자형이 아닐 경우, 항상 `False`를 반환합니다.

- `<=` (작거나 같음)
    - x가 y보다 작거나 같은지 여부를 반환합니다.
    - `x = 3; y = 6; x <= y`는 `True`를 반환합니다.

- `>=` (크거나 같음)
    - x가 y보다 크거나 같은지 여부를 반환합니다.
    - `x = 4; y = 3; x >= 3`는 `True`를 반환합니다.

- `==` (같음)
    - 두 객체가 같은지 여부를 반환합니다.
    - `x = 2; y = 2; x == y`는 `True`를 반환합니다.
    - `x = 'str'; y = 'stR'; x == y`는 `False`를 반환합니다.
    - `x = 'str'; y = 'str'; x == y`는 `True`를 반환합니다.

- `!=` (같지 않음)
    - 두 객체가 같지 않은지 여부를 반환합니다.
    - `x = 2; y = 3; x != y`는 `True`를 반환합니다.

- `not` (불리언 NOT 연산자)
    - x가 `True`라면, `False`를 반환합니다. x가 `False`라면, `True`를 반환합니다.
    - `x = True; not x`는 `False`를 반환합니다.

- `and` (불리언 AND 연산자)
    - x가 'False'일 때 `x and y`는 `False`를 반환하고 아니면 y와의 and 연산 결과를 반환합니다.
    - x가 `False`이기 때문에 `x = False; y = True; x and y`는 `False`를 반환합니다. `and` 연산에서 왼쪽의 값이 `False`면 전체 수식이 `False`가 되기 때문에 파이썬은 y의 값을 처리하지 않습니다. 이것을 단축 계산(short-circuit evalulation)이라고 부릅니다.

- `or` (불리언 OR 연산자)
    - x가 `True`이면 `True`가 반환되며, `False`이면 y와의 or 연산값을 반환합니다.
    - `x = True; y = False; x or y`는 `True`를 반환합니다. 여기서도 단축 계산이 적용됩니다.

## Shortcut for math operation and assignment

It is common to run a math operation on a variable and then assign the result of the operation back to the variable, hence there is a shortcut for such expressions:

```python
a = 2
a = a * 3
```

can be written as:

```python
a = 2
a *= 3
```

Notice that `var = var operation expression` becomes `var operation= expression`.

## Evaluation Order

If you had an expression such as `2 + 3 * 4`, is the addition done first or the multiplication? Our high school maths tells us that the multiplication should be done first. This means that the multiplication operator has higher precedence than the addition operator.

The following table gives the precedence table for Python, from the lowest precedence (least binding) to the highest precedence (most binding). This means that in a given expression, Python will first evaluate the operators and expressions lower in the table before the ones listed higher in the table.

The following table, taken from the [Python reference manual](http://docs.python.org/3/reference/expressions.html#operator-precedence), is provided for the sake of completeness. It is far better to use parentheses to group operators and operands appropriately in order to explicitly specify the precedence. This makes the program more readable. See [Changing the Order of Evaluation](#changing-order-of-evaluation) below for details.

- `lambda` : Lambda Expression
- `if - else` : Conditional expression
- `or` : Boolean OR
- `and` : Boolean AND
- `not x` : Boolean NOT
- `in, not in, is, is not, <, <=, >, >=, !=, ==` : Comparisons, including membership tests and identity tests
- `|` : Bitwise OR
- `^` : Bitwise XOR
- `&` : Bitwise AND
- `<<, >>` : Shifts
- `+, -` : Addition and subtraction
- `*, /, //, %` : Multiplication, Division, Floor Division and Remainder
- `+x, -x, ~x` : Positive, Negative, bitwise NOT
- `**` : Exponentiation
- `x[index], x[index:index], x(arguments...), x.attribute` : Subscription, slicing, call, attribute reference
- `(expressions...), [expressions...], {key: value...}, {expressions...}` : Binding or tuple display, list display, dictionary display, set display

The operators which we have not already come across will be explained in later chapters.

Operators with the _same precedence_ are listed in the same row in the above table. For example, `+` and `-` have the same precedence.

## Changing the Order Of Evaluation {#changing-order-of-evaluation}

To make the expressions more readable, we can use parentheses. For example, `2 + (3 * 4)` is definitely easier to understand than `2 + 3 * 4` which requires knowledge of the operator precedences. As with everything else, the parentheses should be used reasonably (do not overdo it) and should not be redundant, as in `(2 + (3 * 4))`.

There is an additional advantage to using parentheses - it helps us to change the order of evaluation. For example, if you want addition to be evaluated before multiplication in an expression, then you can write something like `(2 + 3) * 4`.

## Associativity

Operators are usually associated from left to right. This means that operators with the same precedence are evaluated in a left to right manner. For example, `2 + 3 + 4` is evaluated as `(2 + 3) + 4`.

## Expressions

Example (save as `expression.py`):

```python
length = 5
breadth = 2

area = length * breadth
print('Area is', area)
print('Perimeter is', 2 * (length + breadth))
```

Output:

```
$ python expression.py
Area is 10
Perimeter is 14
```

**How It Works**

The length and breadth of the rectangle are stored in variables by the same name. We use these to calculate the area and perimeter of the rectangle with the help of expressions. We store the result of the expression `length * breadth` in the variable `area` and then print it using the `print` function. In the second case, we directly use the value of the expression `2 * (length + breadth)` in the print function.

Also, notice how Python _pretty-prints_ the output. Even though we have not specified a space between `'Area is'` and the variable `area`, Python puts it for us so that we get a clean nice output and the program is much more readable this way (since we don't need to worry about spacing in the strings we use for output). This is an example of how Python makes life easy for the programmer.

## Summary

We have seen how to use operators, operands and expressions - these are the basic building blocks of any program. Next, we will see how to make use of these in our programs using statements.
