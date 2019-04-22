# Today-I-Learned-
Today I Learned 💚🤓🌱

<h3>Python</h3>

4/22 - py4e > chapter 11-1
```python3
### 정규식 표현 
^X: X로 시작하는 것 
.: Match any character 
*: Many times, 횟수제한 없음 
\S: Match any non-whitespace character 
+: One or more times 

```


4/21 - py4e > chapter 11-1
```python3
### 정규식은 python은 아니지만 python고 함께 많이 사용되니 배웁니다.
### 정규식 라이브러리를 불러오기 위해서 import re를 합니다.
### 리뷰를 모아놓은 reviews.txt 파일에서 "주차장"이라는 단어로 시작하는 줄을 불러와 출력합니다. 
import re

hand = open('reviews.txt')
for line in hand:
    line = line.rstrip()
    if re.search('^주차장', line) :
        print(line)


```


4/18 - py4e > chapter 10-2 
``` python 
### 이용자들으 이용후기에서 가장 많이 사용된 단어를 카운팅 해보자.
### 1등은 "너무" 였다.

fhand = open('reviews.txt')
counts = dict()
for line in fhand:
    words = line.split()
    for word in words:
        counts[word] = counts.get(word, 0) + 1

lst = list()
for key, val in counts.items():
    newtup = (val, key)
    lst.append(newtup)

lst = sorted(lst, reverse=True)

for val, key in lst[:100] :
    print(key)

```


4/16 - py4e > chapter 10-1 
```python
### 튜플은 쓰고 버릴 수 있다. 
### 좌변에 변수를 가진 채 튜플로 선언을 할 수 있다. python만 가능하다

(x, y)  = (4, 'fred')
print(y)

(a, b) = (99, 88)
print(a)

###
d = dict()
d['csev'] = 2
d['cwen'] = 4
print(d)

for (k, v) in d.items():
    print(k,v)

tups = d.items()
print(tups)

### 튜플은 비교하는 것이 쉽다.
 


```



4/13 - py4e > chapter 10-1
```python
### tuple 이라는 것으 배워봅니다. 
### 튜플은 리스트와 비슷한데, 동작도 비슷하나,,, 소괄호를 쓴다는 것이 다르고 ... (리스트는 대괄호) 
### 튜플은 값을 변경하 수 없다. 순서만 변경할 수 있다. 리스트는 원소를 변경할 수 있다. 
### 튜플은 리스트에 비해 용량도 적게 차지하고 .... 

```


4/12 - py4e > chapter 9 -3 
```python
### dictionary 르 이용하여 for 문을 돌릴 수 있ㄷ. 
jjj = {'chuck':1, 'fred':43, 'jan': 100}
for aaa, bbb in jjj.items():
    print (aaa,bbb)

```


4/8 - py4e > chapter 9 - 3
```python
#get 메소드를 사용하는 법을 배웠다.

counts = dict()
names = ['csev','cwen', 'csev', 'zqian', 'cwen', 'zqian', 'zqian', 'zqian']
for name in names :
    counts[name] = counts.get(name, 0) + 1 #counts 에서 get() 메소드를 이용하여 if 이미 존재하는 key라며 key값으 name 이라는 변수에 반환하고, 그렇지 않다면 0으 반환한다. 그리고 이미 존재하는 것이면 + 1를 한다. 
print(counts)

```

4/6 - py4e > chapter 9 - 3
```python
counts = dict()
names = ['csev','cwen', 'csev', 'zqian', 'cwen', 'zqian', 'zqian', 'zqian']
for name in names :
    if name not in counts:
        counts[name] = 1
    else:
        counts[name] = counts[name] +1
print(counts)

```

딕션너리 와 for문으 이용한 이름 숫자세기 ...
for 문의 개념을 제대로 숙지하고 있지 못 했다는 걸 깨달았다.

그래서 ... 다시 찾아서 읽어보았다.
https://wikidocs.net/22





4/1 - py4e > chapter 9 - 3
```python
#loops를 이용한 dictionary 

counts = dict()
print ('Enter a line of text:')
line = input('')

words = line.split()
print ('Words:', words )

print ('Counting ...')
for word in words :
    counts[word] = counts.get(word,0) + 1
print('Counts', counts)

```
```
#키, 밸류를 짝을 지어서 출력해보자 
jjj = {'chuck': 1 , 'fred':42, 'jan': 100}
for aaa, bbb in jjj.items():
    print(aaa,bbb)

```



3/31 - py4e > chapter 9 - 1, 2 
```
#dictionary 
어제 저장한 것은 어디로 갔지?
dictionary 는 list와 다른다. key:value 로 짝지은 bag 같다. 순서도 없다. 
```


3/30 - py4e > chapter 8 - 3 
- split 은 공백을 기준으로 원소를 분리한다.

```
abc = 'With theree words'
stuff = abc.split()
print(stuff)

print(len(stuff))
print(stuff[0])

for w in stuff :
  print(w)
```
- Double split pattern 
ㄴ split 기준을 '@'으로 설정하면 이메일 주소의 도메인과 주소를 구분할 수 있다. 
```
words = line.split() #공백 기준으로 원소르 분리 
email = words[1]
pieces = email.split('@')
print(pieces[1])
```



3/18 > Lists
<li>PY4E > Ch.8 > Lists (https://www.py4e.com/lessons/lists)</li>
<li>리스트는 가장 간단한 자료구조, 콜레션의 한 종류이다.</li>
<li>리스트는 다른 리스트를 element로 가질 수 있다.</li>
<li>list[n] = "m" <- n 번째 element를 m으로 변경할 수 있다. </li>
<li>list Methods</li>
<li>append = object를 list 뒤 쪽에 추가한다.</li>
<li>extent = iterable object를 뒤 쪽에 추가한다. </li>
<li>count = 특정 요소의 갯수를 센다.</li>
<li>index = </li> 
<li>insert = list 중간에 object를 추가한다.</li>
<li>pop = list 마지막 원소를 꺼낸다. </li>
<li>remove = 특정원소를 삭제한다.</li>
<li>sort = 원소를 정렬한다. </li>
<li>reverse = 순서를 앞뒤로 뒤집는다.</li>
