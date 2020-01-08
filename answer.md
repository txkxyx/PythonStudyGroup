# Python勉強会問題集解答

## 問題1

次の⺟集団データがあります。

> x = [80, 82, 65, 45, 72, 66, 68, 90, 83, 77]

1. 合計を求めてください

```python
x = [80, 82, 65, 45, 72, 66, 68, 90, 83, 77]

# 解答1
result = 0
for num in x:
  result += num
print(result)

# 解答2
print(sum(x))
```

2. 平均値を求めてください

```python
x = [80, 82, 65, 45, 72, 66, 68, 90, 83, 77] 

# 解答1
result = 0
for num in x:
  result += num
print(result / len(x))

# 解答2
print(sum(x) / len(x))
```

3. 分散を求めてください

```python
x = [80, 82, 65, 45, 72, 66, 68, 90, 83, 77] 

# 平均
avarage = sum(x) / len(x)

# 平均との差の２乗のリスト
squared_diff = []
for num in x:
    squared_diff.append((num - avarage) ** 2)

# 分散
variance = sum(squared_diff) / len(squared_diff)
print(variance)
```

4. 標準偏差を求めてください

```python
x = [80, 82, 65, 45, 72, 66, 68, 90, 83, 77] 

# 平均
avarage = sum(x) / len(x)

# 平均との差の２乗のリスト
squared_diff = []
for num in x:
    squared_diff.append((num - avarage) ** 2)

# 分散
variance = sum(squared_diff) / len(squared_diff)
# 標準偏差
std = variance ** 0.5
print(std)
```

## 問題2 

次のリストがあります。

 > [ ['Python','2.7'],['Python','3.6'],['Python','3.8'],['Java','8'],['Java','11'] ] 

このリストを以下の辞書型に変換してください。

>  {'Python': ['2.7', '3.6', '3.8'], 'Java': ['8', '11']}

```python
x = [ ['Python','2.7'],['Python','3.6'],['Python','3.8'],['Java','8'],['Java','11'] ]

result = {}

for e in x:
    if e[0] in result:
        result[e[0]].append(e[1])
    else:
        result[e[0]] = [e[1]]

print(result)
```