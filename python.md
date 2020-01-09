# Python3勉強会

Google Colaboratoryで実行します。Pythonのバージョンは`3.6.9`です。

[Google Colaboratory](https://colab.research.google.com/notebooks/welcome.ipynb?hl=ja)

> command + Enter　→　実行
>
> command + M , B　→　新しいコードの作成
>
> command + M , D　→　現在のコードの削除

この資料以外の内容については公式ドキュメントを確認してください。

[pythonドキュメント](https://docs.python.org/ja/3/index.html)


## アジェンダ

1. Hello World
2. 基本文法
3. 変数とデータ型
4. 制御構文
5. データ構造
6. 関数
7. クラス
8. 演習問題


## Hello World

Pythonには組み込み関数として、インタープリタに出力する関数`print()`が用意されています。

```python
print('Hello World')
```


### 組み込み関数

先ほど使用した`print()`関数は組み込み関数として用意されており、ライブラリを読み込むこと(import)なく実行することができます。
このように、Pythonには型変換や計算式など多くの組み込み関数が用意されています。最新バージョンでは69個用意されています。

[Python組み込み関数](https://docs.python.org/ja/3/library/functions.html)


## 文法基本

### コメント

Pythonのコメントは`#`を使用します。

`#`から行末までがコメントとして認識されます。

```python
# Hello World
print('Hello World') # Hello World
print('Hello World') # Hello World # print('Hello World')
```

トリプルクォート(`'''`もしくは`"""`)によるコメントアウトを使用することもできますが、基本的にはpydocなどのドキュメント文字列にしか使用しません。

```python
def function(args):
    '''
    function
    args : str
    return : str
    '''
    return args
```


### インデント

Pythonの処理ブロックは`:`と空白で表現されます。
Pythonでは、`:`の次の行から同じ数の空白でインデントされたまとまりを1つのブロックとして認識します。

```python
a = 1
b = 1
if a == b:
    print(a)
    print(b)
else:
    print('not equals')
```

インデントが適切に設定されていないと、処理を続行することができなくなりエラーとなります。

```python
a = 1
b = 1

if a == b:
    print(a)
        print(b) # IndentationError
```

Pythonのコーディング規約であるPEP8には、１レベルのインデントにはスペースを4つ使用すると定められています。


### 命名規則

変数名や関数名は、スネークケースで宣言します。

クラス名は、キャメルケースで宣言するします。

```python
python_name = 'python'

def python_version():
    return '3.8.1'

class PythonClass():
    pass

```


### 標準モジュール（標準ライブラリ）

Pythonには標準モジュールライブラリと呼ばれるモジュール群が用意されています。
ライブラリを使用する場合は組み込み関数とは異なり、明示的にライブラリを読み込む(import)する必要があります。

```python
# 実行環境に関する情報を扱うライブラリ
import sys

print(sys.version)
```

[Python標準ライブラリ](https://docs.python.org/ja/3/library/index.html)


### コーディング規約

Pythonには`PEP8`というコーディング規約が用意されています。

[PEP8](https://pep8-ja.readthedocs.io/ja/latest/)

- インデントは半角スペース4つで統一する
- 1行の長さは半角79文字以内に制限する
- クラスや関数の宣言の前に2行分改行する

などの規約が定められている。


## 変数とデータ型

Pythonのデータ型は組み込み型として定義されています。

- 数値型
- 文字列型
- バイト型
- リスト型
- 辞書型
- タプル型
- 集合型
- ブール型

[Python組み込み型](https://docs.python.org/ja/3/library/stdtypes.html#)

### type()・isinstance()

変数やオブジェクトの型を取得し確認するために、組み込み関数として`type()`が用意されています。

```python
print(type(5)) # <class 'int'>

print(type('abc')) # <class 'str'>

print(type(True)) # <class 'bool'>
```

変数やオブジェクトの型を判定するために、組み込み関数`isinstance()`が用意されています。
第一引数のオブジェクトが、第二引数の型のインスタンスかもしくはサブクラスのインスタンスであれば`True`を返します。

```python
print(isinstance('10', int)) # False

print(isinstance(False, bool)) # True
```

### 数値型

Pythonの数値型には、整数・小数・複素数があります。

[Python数値型](https://docs.python.org/ja/3/library/stdtypes.html#numeric-types-int-float-complex)

```python

# 整数 int
i = 10
print(i)
print(type(i)) # <class 'int'>

# 小数 float
f = 3.14
print(f)
print(type(f)) # <class 'float'>

# 複素数 complex
c = 5 + 3j # 虚部はiではなくjで表現
print(c)
print(type(c)) # <class 'complex'>

```

数値の演算は以下の表のように行うことができます。

| 演算 | 結果 |
| --- | --- |
| x + y | xとyの和 |
| x - y | xとyの差 |
| x * y | xとyの積 |
| x / y | xとyの商 |
| x // y | xとyの切り捨てた商 |
| x % y | xをyで割った余り |
| x ** y | xのy乗 |
| x += 1 | xのインクリント |
| y -= 1 | yのデクリメント |

```python
x = 30
y = 1.5
z = 1.3

print(x + y) # 31.5
print(x - y) # 28.5
print(x * y) # 45.0
print(x / y) # 23.076923076923077
print(x // z) # 23.0
print(x % z) # 0.09999999999999898
print(x ** 2) # 900
x += 1
print(x) # 31
y -= 1
print(y) # 0.5
```

### 文字列

Pythonの文字列は`str`型として定義されています。

[Python文字列](https://docs.python.org/ja/3/library/stdtypes.html#text-sequence-type-str)

文字列の定義方法は以下の3つの方法があります。

- シングルコーテーション：`'abc'`
- ダブルコーテーション：`"abc"`
- トリプルクォート：`'''abc'''`、```"""abc"""```

シングルコーテーションで囲んだ文字列の中には、ダブルコーテーションを定義することができます。

ダブルコーテーションで囲んだ文字列の中には、シングルコーテーションを定義することができます。

トリプルクォートで囲まれた文字列は、リテラルとして扱われます。

文字列のエスケープは、`\`で行うことができます。リテラルの先頭の改行を消す際も、`\`を用います。

```python
a = '"abc"'
print(a) # "abc"

b = "'abc'"
print(b) # 'abc'

c = '''
abc
def
ghi
'''
print(c)
#
# abc
# def
# ghi
```

文字列のトリミングは`[:]`で行うことができます。

```python
a = 'abcdefg'

# 全て
print(a[:]) # abcdefg
# 2から4まで
print(a[2:5]) # cde
# 先頭から3まで
print(a[:4]) # abcd
# 3から末尾まで
print(a[3:]) # defg
# 先頭から末尾の1つ前まで
print(a[:-1]) # abcdef
```

文字列には、フォーマット指定・分割・置換などのメソッドが実装されています。

[文字列メソッド](https://docs.python.org/ja/3/library/stdtypes.html#string-methods)

### ブール値

Pythonの真偽値は`bool`型として定義されています。

| 真偽 | bool | int |
| --- | --- | --- |
| 真 | True | 1 |
| 偽 | False | 0 |

```python
t = True
f = False

print(t) # True
print(int(t)) # 1
print(f) # False
print(int(f)) # 0
```

#### ブール演算・比較演算子

| 演算 | 結果 |
| --- | --- |
| x or y | xまたはy |
| x and y | xかつy |
| not x | xの否定 |
| x < y | xはyより小さい |
| x <= y | xはy以下 |
| x > y | xはyより大きい |
| x >= y | xはy以上 |
| x == y | xとyは等しい |
| x != y | xとyは等しくない |
| x is y | xとyは同じオブジェクト |
| x is not y | xとyは同じオブジェクトではない |

```python
x = 10
y = 10.0

print(x) # 10
print(type(x)) # <class 'int'>
print(y) # 10.0
print(type(y)) # <class 'float'>

# 等価
print(x == y) # True
print(x != y) # False

# オブジェクトの比較
print(x is y) # False
print(x is not y) # True
```

### None

PythonでNullオブジェクトを表現する場合は、`None`を使用します。

```python
n = None

print(n) # None
print(bool(n)) # False

print(n is None) # True
```

Noneの比較は通常は比較演算子`is`を使用します。

## 制御構文

### if文

Pythonのif文の基本構文は以下のようになります。

```python
if '条件式':
    処理
elif '条件式':
    処理
else:
    処理
```

if文のスコープはインデントで表現します。
`else if`は`elif`と表現します。
比較演算子やブール演算子を用いて条件式を記述します。

```python
name = 'John'
age = 20
license = True

if age >= 20 and license:
    print(name + ' OK')
else:
    print(nae + ' NG')

# John OK
```

### for文

Pythonのfor文の基本構文は以下のようになります。

```python
for 変数 in シーケンス:
    処理
```

組み込み関数で用意されている`range`関数を使用することで、指定した数値の範囲のシーケンスを作成することができます。

組み込み関数の`enumerate`関数を使用することでインデックスと要素の順でを取り出すことができます。

```python
# 0 1 2 3 4
for num in range(5):
    print(num)

# 0:a 1:b 2:c 3:d 4:e 5:f 6:g
for i, string in enumerate('abcdefg'):
    print(str(i) + ':' + string)
```

ループで使用するテクニックがチュートリアルで紹介されています。

[ループのテクニック](https://docs.python.org/ja/3/tutorial/datastructures.html#looping-techniques)

### break・pass

ループ内で`break`文を使用することでループを中断することができます。

```python
for n in range(1,10):
    for x in range(1,n):
        print(x)
        if x > n:
            break
```

何も処理をしたくない場合は`pass`文を使用することで、処理をスキップすることができます。

```python
name = 'John'
age = 20
license = True

if age >= 20 and license:
    pass
else:
    print(name + ' NG')
```

## データ構造

### リスト

Pythonのリストは`list`型として定義されており、`[]`もしくは組み込み関数`list()`で宣言します。

インデックスでアクセスする場合は、`[index]`でアクセスすることができます。

文字列と同様に`[start:end]`でトリミングを行うことができます。

for文ではin文で要素を取り出すことができます。組み込み関数の`enumerate`関数を使用することでインデックスと要素を取り出すことができます。

ネストしたリストも作成可能です。

```python
# リストの宣言
num_list = [1,2,3,4,5]
str_list = list('abcdefg')

print(num_list) # [1, 2, 3, 4, 5]
print(str_list) # ['a', 'b', 'c', 'd', 'e', 'f', 'g']

print(num_list[4]) # 5
print(str_list[2:5]) # ['c', 'd', 'e']

for num in num_list:
    print(num)

for i, string in enumerate(str_list):
    print(i, string)

nest_list = [[1,2,3],['a','b','c']]
```

リストにも多数のメソッドが実装されています。

[list関数](https://docs.python.org/ja/3/tutorial/datastructures.html#more-on-lists)

```python
num_list = [1,2,3,4,5]

# 末尾に追加
num_list.append(6)
print(num_list)
# 指定インデックスに追加
num_list.insert(3,2)
print(num_list)
# 引数のデータに該当するデータの先頭を削除
num_list.remove(2)
print(num_list)
# 指定インデックスの取り出し（削除）
num_list.pop(0)
print(num_list)
# リストの長さを表示
len(num_list)

# コピー
# ディープコピー
x = [1,2,3,4,5]
y = x
y[2] = 4
print(x)
print(y)
# シャローコピー
z = x.copy()
z[-1] = 9
print(x)
print(z)
```

Pythonにはリストを作成する上でリスト内包表記という構文が用意されています。

[リスト内包表記](https://docs.python.org/ja/3/tutorial/datastructures.html#list-comprehensions)

```python
# 2乗のリストを作成
num_list = [1,2,3,4]
square_list= []
for num in num_list:
    square_list.append(num**2)
print(square_list)
# リスト内包表記
square_list = [e**2 for e in num_list]
print(square_list)

# 奇数は0に置換したリストを作成
num_list = [1,2,3,4,5,6,7,8,9]
env_list = [e if e % 2 ==0 else 0 for e in num_list]
print(env_list)
```

### 辞書

Key,Valueの組み合わせのデータ構造をPythonでは辞書型といい、`dict`型で定義されています。

`{key:value}`もしくは組み込み関数`dict(key=value)`で宣言します。

辞書型へのアクセスは、`dict[key]`で行うことができます。

for文ではin文で辞書型のKeyを取得することができます。

辞書型の`items()`関数を使用することでKeyとValueのイテレータが取得できます。

```python
# 辞書型の宣言
num_map = {5:1,4:2,3:3,2:4,1:5}
str_map = dict(a='abc', b='efg', c='hij')

print(num_map) # {5: 1, 4: 2, 3: 3, 2: 4, 1: 5}
print(str_map) # {'a': 'abc', 'b': 'efg', 'c': 'hij'}

print(num_map[2]) # 4
print(str_map['b']) # efg

for key in num_map:
    print(num_map[key])

for key, value in str_map.items():
    print(key, value)

# Keyのリストを取得
print(list(str_map))
# Keyが含まれているかをチェック
print('b' in str_map)
```

リスト同様に辞書型にも関数が用意されています。

[dict関数](https://docs.python.org/ja/3/library/stdtypes.html#mapping-types-dict)

辞書型内包表記もあります。

```python
num_list = [1,2,3,4,5]
num_dict = {}
for num in num_list:
    num_dict[str(num)] = num
print(num_dict)

# 辞書型内包表記
num_dict = {str(num):num for num in num_list}
print(num_dict)
```

### その他のデータ構造

イミュータブルなリストとしてタプルが用意されています。定数を定義する際に使用されます。

```python
t = 'abc', 123, True

print(t) # ('abc', 123, True)
print(t[2]) # True

for e in t:
    print(e)

# t[2] = False
```

重複する要素を持たない集合体として`set`オブジェクトが用意されています。

```python
s = {'abc', 'def', 1234}

print(s)
# print(s[2])

for e in s:
    print(e)

print('abc' in s)
print(5324 in s)
```

## 関数

Pythonではdefキーワードを使用して関数を定義します。defキーワードの後に、関数名と引数を宣言します。戻り値は宣言する必要はありません。

戻り値はreturn文で返します。戻り値の個数や型は固定する必要がありません。

```python
def func1(a, b):
    return a + b

print(func1('Hello', 'World')) # HelloWorld


def func2(a, b):
    if a % 2 == 0:
        return [a, b], 'OK'
    else:
        return 'NG'

print(func2(1,2)) # NG
print(func2(4,3)) # ([4,3],'OK')
l, s = func2(4,3)
```

### 引数

#### デフォルト引数

Pythonの関数の引数にはデフォルト値を設定することができます。

```python
def func1(num, string, option=True, message='default'):
    print(num, string, option, message)


func1(10, 'Hello') # 10 Hello True default
func1(20, 'World', False, 'function') # 20 World False function
```

#### キーワード引数

関数を呼び出す際に、'keyword=value'という形式で指定した引数に値を指定することができます。

```python
def func1(num, string, option=True, message='default'):
    print(num, string, option, message)

func1(string='Python', num=30, message='key word') # 30 Python True key word
```

#### 可変長引数

Pythonで可変長引数を指定する場合は`*`を使用します。引数はタプルとして受け取ります。

```python
def total(*args):
    result = 0
    for e in args:
        result += e
    return result

print(total(1,2,3,4,5))
```

#### 可変長キーワード引数

可変長なキーワード引数を`**`を使用することで指定することができます。引数を辞書型として引き取ります。

```python
def keywords(**args):
    for key, value in args.items():
        print(key, value)


keywords(a=1,b=2,c=3,d=4)
```

## クラス

Pythonのクラスclassキーワードを使用して、以下のように定義することができます。

`__init__`関数でコンストラクタを宣言することができます。コンストラクタでインスタンス変数を設定できます。

[Pythonクラス](https://docs.python.org/ja/3/tutorial/classes.html)

```python

class Car:
    CLASS_NAME = 'Car'

    def __init__(self, name, gas):
        self.name = name
        self.gas = gas
    
    def move(self):
        if self.gas > 0:
            self.gas -= 1
            print(self.name + ' move')
        else:
            print(self.name + ' stop')

car1 = Car('truck', 10)
car2 = Car('wagon', 3)

for i in range(5):
    car1.move()
    car2.move()
print(car1.CLASS_NAME)
```

### 継承

Pythonでクラスの継承を行う場合は、`class クラス名(基底クラス):`で宣言します。

```python

class Car:
    def __init__(self, name, gas):
        self.name = name
        self.gas = gas
    
    def move(self):
        if self.gas > 0:
            self.gas -= 1
            print(self.name + ' move')
        else:
            print(self.name + ' stop')

class Truck(Car):
    def move(self):
        if self.gas > 0:
            self.gas -= 2
            print(self.name + ' move')
        else:
            print(self.name + ' stop')

car = Car('car', 10)
truck = Truck('truck', 10)

car.move()
truck.move()

print(car.gas)
print(truck.gas)
```

基底クラスを継承したクラスは、基底クラスで宣言した変数と関数を引き継ぐことができます。
基底クラスと同じシグネチャで関数を宣言すると、オーバーライドすることができます。


### 多重継承

Pythonでは多重継承で複数の基底クラスを継承することができます。
多重継承をする場合は、基底クラス名を`,`区切りて定義します。

```python

class A:
    def func(self):
        print('A')

class B:
    def func(self):
        print('B')

class C(A,B):
    pass

class D(B,A):
    pass

c = C()
d = D()

c.func()
d.func()
```

多重継承した基底クラスの関数のシグネチャが等しい場合は、先に継承したクラスの関数が優先されます。

### private・publicな変数と関数

Pythonのクラスでは、変数と関数をカプセル化することができます。
Pythonで変数や関数を隠蔽する場合は、名前の前に`__`(_を2つ)をつけて定義します。

```python

class X:
    __private = 'private'
    public = 'public'

    def __private_method(self):
        print(self.__private)
        print(self.public)
    
    def public_method(self):
        self.__private_method()

x = X()

# print(x.__private) 
print(x.public)
# x.__private_method()
x.public_method()
```

## 演習問題

[演習問題](problem.md)

[演習問題解答](answer.md)