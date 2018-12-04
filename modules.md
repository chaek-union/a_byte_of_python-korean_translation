# 모듈

앞에서 함수를 통해 여러분의 프로그램 안에서 코드를 재사용하는 방법에 대해서 배워 보았습니다. 그러면 여러 함수들을 한꺼번에 불러들여 재사용하는 방법은 없을까요? 네, 이럴 때 모듈을 이용합니다.

모듈을 작성하는 데에는 여러가지 방법이 있습니다만, 가장 간단한 방법은 `.py` 확장자를 가진 파일을 하나 만들고 그 안에 함수들과 변수들을 정의해 두는 것입니다.

모듈을 작성하는 또 한 가지 방법은 여러분이 현재 사용중인 파이썬 인터프리터를 만드는데 사용되는 프로그래밍 언어로 모듈을 작성하는 것입니다. 예를 들어, 표준 파이썬 인터프리터를 사용 중인 경우 [C 언어](http://docs.python.org/3/extending/)를 이용하여 모듈을 작성하고 컴파일하면 파이썬에서 이것을 불러와 사용할 수 있습니다.

다른 프로그램에서 **import** 명령을 통해 모듈을 불러와 사용할 수 있습니다. 파이썬 표준 라이브러리 또한 동일한 방법을 통해 이용이 가능합니다. 일단, 표준 라이브러리를 불러와 사용하는 방법을 알아보도록 하겠습니다.

예제 (`module_using_sys.py`로 저장하세요):

```python
import sys

print('The command line arguments are:')
for i in sys.argv:
    print(i)

print('\n\nThe PYTHONPATH is', sys.path, '\n')
```

실행 결과:

```
$ python module_using_sys.py we are arguments
The command line arguments are:
module_using_sys.py
we
are
arguments


The PYTHONPATH is ['/tmp/py',
# many entries here, not shown here
'/Library/Python/2.7/site-packages',
'/usr/local/lib/python2.7/site-packages']
```

**동작 원리**

먼저, 표준 라이브러리 중 하나인 `sys` 모듈을 `import`문을 통해 불러왔습니다. 이것은 단순히 파이썬에게 이 모듈을 앞으로 사용할 것이라고 알려주는 과정이라고 생각하시면 편합니다. 여기서 사용된 `sys` 모듈은 파이썬 인터프리터와 인터프리터가 실행중인 환경, 즉 **시스템**(system)에 관련된 기능들이 담겨 있습니다.

파이썬이 `import sys`문을 실행하는 시점에서, 파이썬은 `sys` 모듈을 찾습니다. 이 경우에는 내장 모듈을 불러오는 것이므로, 파이썬이 이미 어디서 이것을 불러와야 하는지 알고 있습니다.

만약 그렇지 않은 경우, 예를 들어 파이썬으로 여러분이 직접 작성한 모듈인 경우 파이썬 인터프리터는 `sys.path` 변수 에 정의된 디렉토리들에 해당 모듈이 있는지 검색합니다. 그리고 나서 모듈을 찾아내면, 그 모듈 내부에 적혀있는 명령들이 읽어들여지게 되며 그 다음부터 모듈이 **사용가능하게** 됩니다. 이러한 초기화 과정은 **첫번째로** 모듈을 불러올 때만 이루어진다는 것을 기억하세요.

`sys` 모듈의 `argv` 변수를 불러올 때, 마침표를 이용하여 `sys.argv`와 같이 접근합니다. 이와 같이 마침표를 이용함으로써 뒤에 온 이름이 `sys` 모듈에 존재한다는 것을 명시적으로 알려 주고, 또한 여러분의 프로그램에 사용될지 모를 `argv`라는 이름을 가진 다른 변수와 충돌이 일어나지 않도록 합니다.

`sys.argv` 변수는 문자열의 **리스트** 입니다 \(리스트에 대해서는 [다음 장](./data_structures.md#data-structures))에서 좀 더 자세히 다룰 것입니다\). 좀 더 구체적으로 `sys.argv`가 담고 있는 것은 *명령줄 인수*들의 리스트인데, 이것은 명령줄로부터 프로그램을 실행시킬 때 함께 넘어온 인수들을 담고 있는 것입니다.

여러분이 프로그램을 작성하고 실행할 때 IDE(Integrated Development Environment, 통합 개발 환경를 이용하시는 경우, IDE 상에서 프로그램을 실행할 때 명령줄 인수를 지정하는 방법에 대해 알아보시기 바랍니다.

여기서는 명령줄에서 직접 `python module_using_sys.py we are arguments` 명령을 통해 실행하였습니다. 이것은 `python` 명령을 통해 `module_using_sys.py` 모듈을 실행시키고 함께 적어준 명령줄 인수들을 실행될 프로그램에 넘겨준 것입니다. 그러면 파이썬은 `sys.argv` 변수에 이것을 저장해 주며 프로그램에서 사용할 수 있도록 합니다.

이 때, 여러분이 실행한 스크립트의 이름이 `sys.argv` 리스트의 첫번째 항목이 됨을 기억하세요. 즉, 이 경우 `'module_using_sys.py'`가 `sys.argv[0]`에 해당하며, `'we'`는 `sys.argv[1]`에, `'are'`는 `sys.argv[2]`에, `'arguments'`는 `sys.argv[3]`에 해당합니다. 파이선은 숫자를 0부터 센다는 점을 기억하세요 (1이 아닙니다!).

`sys.path` 변수에는 모듈을 불러올 때 찾게 되는 디렉토리들의 리스트가 담겨 있습니다. `sys.path` 변수의 첫 번째 항목이 공백 문자열임을 확인하세요. 공백 문자열은 현재 디렉토리를 의미하는데, 따라서 이것은 현재 디렉토리 또한 `sys.path`의 일부임을 의미하며 이것은 `PYTHONPATH` 환경변수의 경우와도 같습니다. 즉, 여러분은 현재 디렉토리에 들어 있는 파이썬 모듈을 불러와 사용할 수 있는 것입니다. 그렇지 않은 경우, `sys.path`에 지정된 디렉토리들 중 하나에 해당 모듈이 들어 있어야 합니다.

이때 현재 디렉토리란 프로그램을 실행할 때 위치하고 있는 디렉토리를 말합니다. `import os; print(os.getcwd())`를 실행하여 여러분의 프로그램에서 현재 디렉토리가 어디인지 확인할 수 있습니다.

## Byte-compiled .pyc files {#pyc}

Importing a module is a relatively costly affair, so Python does some tricks to make it faster. One way is to create *byte-compiled* files with the extension `.pyc` which is an intermediate form that Python transforms the program into (remember the [introduction section](./about_python.md#interpreted) on how Python works?). This `.pyc` file is useful when you import the module the next time from a different program - it will be much faster since a portion of the processing required in importing a module is already done. Also, these byte-compiled files are platform-independent.

NOTE: These `.pyc` files are usually created in the same directory as the corresponding `.py` files. If Python does not have permission to write to files in that directory, then the `.pyc` files will _not_ be created.

## The from..import statement {#from-import-statement}

If you want to directly import the `argv` variable into your program (to avoid typing the `sys.` everytime for it), then you can use the `from sys import argv` statement.

> WARNING: In general, *avoid* using the `from..import` statement, use the `import` statement instead. This is because your program will avoid name clashes and will be more readable.

Example:

```python
from math import sqrt
print("Square root of 16 is", sqrt(16))
```

## A module's `__name__` {#module-name}

Every module has a name and statements in a module can find out the name of their module. This is handy for the particular purpose of figuring out whether the module is being run standalone or being imported. As mentioned previously, when a module is imported for the first time, the code it contains gets executed. We can use this to make the module behave in different ways depending on whether it is being used by itself or being imported from another module. This can be achieved using the `__name__` attribute of the module.

Example (save as `module_using_name.py`):

<pre><code class="lang-python">{% include "./programs/module_using_name.py" %}</code></pre>

Output:

<pre><code>{% include "./programs/module_using_name.txt" %}</code></pre>

**How It Works**

Every Python module has its `__name__` defined. If this is `'__main__'`, that implies that the module is being run standalone by the user and we can take appropriate actions.

## Making Your Own Modules

Creating your own modules is easy, you've been doing it all along!  This is because every Python program is also a module. You just have to make sure it has a `.py` extension. The following example should make it clear.

Example (save as `mymodule.py`):

<pre><code class="lang-python">{% include "./programs/mymodule.py" %}</code></pre>

The above was a sample *module*. As you can see, there is nothing particularly special about it compared to our usual Python program. We will next see how to use this module in our other Python programs.

Remember that the module should be placed either in the same directory as the program from which we import it, or in one of the directories listed in `sys.path`.

Another module (save as `mymodule_demo.py`):

<pre><code class="lang-python">{% include "./programs/mymodule_demo.py" %}</code></pre>

Output:

<pre><code>{% include "./programs/mymodule_demo.txt" %}</code></pre>

**How It Works**

Notice that we use the same dotted notation to access members of the module. Python makes good reuse of the same notation to give the distinctive 'Pythonic' feel to it so that we don't have to keep learning new ways to do things.

Here is a version utilising the `from..import` syntax (save as `mymodule_demo2.py`):

<pre><code class="lang-python">{% include "./programs/mymodule_demo2.py" %}</code></pre>

The output of `mymodule_demo2.py` is same as the output of `mymodule_demo.py`.

Notice that if there was already a `__version__` name declared in the module that imports mymodule, there would be a clash. This is also likely because it is common practice for each module to declare it's version number using this name. Hence, it is always recommended to prefer the `import` statement even though it might make your program a little longer.

You could also use:

```python
from mymodule import *
```

This will import all public names such as `say_hi` but would not import `__version__` because it starts with double underscores.

> WARNING: Remember that you should avoid using import-star, i.e. `from mymodule import *`.

<!-- -->

> **Zen of Python**
> 
> One of Python's guiding principles is that "Explicit is better than Implicit". Run `import this` in Python to learn more.

## The `dir` function {#dir-function}

The built-in `dir()` function returns the list of names defined by an object.
If the object is a module, this list includes functions, classes and variables, defined inside that module.

This function can accept arguments.
If the argument is the name of a module, the function returns the list of names from that specified module.
If there is no argument, the function returns the list of names from the current module.

Example:

```python
$ python
>>> import sys

# get names of attributes in sys module
>>> dir(sys)
['__displayhook__', '__doc__',
'argv', 'builtin_module_names',
'version', 'version_info']
# only few entries shown here

# get names of attributes for current module
>>> dir()
['__builtins__', '__doc__',
'__name__', '__package__', 'sys']

# create a new variable 'a'
>>> a = 5

>>> dir()
['__builtins__', '__doc__', '__name__', '__package__', 'sys', 'a']

# delete/remove a name
>>> del a

>>> dir()
['__builtins__', '__doc__', '__name__', '__package__', 'sys']
```

**How It Works**

First, we see the usage of `dir` on the imported `sys` module. We can see the huge list of attributes that it contains.

Next, we use the `dir` function without passing parameters to it. By default, it returns the list of attributes for the current module. Notice that the list of imported modules is also part of this list.

In order to observe `dir` in action, we define a new variable `a` and assign it a value and then check `dir` and we observe that there is an additional value in the list of the same name. We remove the variable/attribute of the current module using the `del` statement and the change is reflected again in the output of the `dir` function.

A note on `del`: This statement is used to *delete* a variable/name and after the statement has run, in this case `del a`, you can no longer access the variable `a` - it is as if it never existed before at all.

Note that the `dir()` function works on *any* object. For example, run `dir(str)` for the attributes of the `str` (string) class.

There is also a [`vars()`](http://docs.python.org/3/library/functions.html#vars) function which can potentially give you the attributes and their values, but it will not work for all cases.

## Packages

By now, you must have started observing the hierarchy of organizing your programs. Variables usually go inside functions. Functions and global variables usually go inside modules. What if you wanted to organize modules? That's where packages come into the picture.

Packages are just folders of modules with a special `__init__.py` file that indicates to Python that this folder is special because it contains Python modules.

Let's say you want to create a package called 'world' with subpackages 'asia', 'africa', etc. and these subpackages in turn contain modules like 'india', 'madagascar', etc.

This is how you would structure the folders:

```
- <some folder present in the sys.path>/
    - world/
        - __init__.py
        - asia/
            - __init__.py
            - india/
                - __init__.py
                - foo.py
        - africa/
            - __init__.py
            - madagascar/
                - __init__.py
                - bar.py
```

Packages are just a convenience to organize modules hierarchically. You will see many instances of this in the [standard library](./stdlib.md#stdlib).

## Summary

Just like functions are reusable parts of programs, modules are reusable programs. Packages are another hierarchy to organize modules. The standard library that comes with Python is an example of such a set of packages and modules.

We have seen how to use these modules and create our own modules.

Next, we will learn about some interesting concepts called data structures.
