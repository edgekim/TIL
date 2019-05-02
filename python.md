# Today-I-Learned-
Today I Learned 💚🤓🌱

<h3>Python</h3>

5/2 - py4e ch.12-5
```python
### urllib 를 이용하며 손쉽게 웹브라우저를 만드 수 있다 
import urllib.request, urllib.parse, urllib.error

fhand = urllib.request.urlopen('http://data.pr4e.org/romeo.txt')

counts = dict()
for line in fhand:
    words = line.decode().split()
    for word in words:
        counts[word] = counts.get(word, 0) + 1
print(counts)


```

4/29 - py4e ch.12-4
```python
### ASC2는 금방 한계에 도달했고, UNICODE는 너무 무겁ㄷ. 
### UTF-32는 한 글자에 4byte, UTF-16은 2byte라서 인터넷으로 전송할 때, 너무 무겁다.
### UTF-8은 한 글자에 1~4byte로 유동적이다.
### python3에서 모든 strings은 unicode 이다.
### 소켓으로 통신할 때는 보내기전에 encode 를 받은 것은 decode를 해야한다. 
```


4/28 - py4e ch.12-1
```python
### Network program 
### python에서 socket 을 이용하기, 소켓 라이브러리만 불러오면 된다. 
###python으로 간단한 웹브라우저를 만들어보자
import socket

mysock = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
mysock.connect(('data.pr4e.org', 80))
cmd = 'GET http://data.pr4e.org/romeo.txt HTTP/1.0\n\n'.encode()
mysock.send(cmd)

while True:
    data = mysock.recv(256)
    if (len(data) <1):
        break
    print(data.decode())
mysock.close()

### 근데 왜 400 bad Request로 응답하는지 ... 이유를 못 찾겠다 ㅠ.ㅠ 

```

4/26 - Python for kids/ch.2 
- EOL은 End-of-line 
- 문자열이 한 줄 이상의 여러 줄로 된 텍스트를 사용하려면 (multiline string) 세 개의 홑따옴표(''')를 사용하고 각 줄 사이에는 ENTER를 입력한다.
```python
fred = '''How do dinosaurs pay their bills? 
With tryannosaurus checks!''' 
```
- 문자열에서 세개의 홑따옴표 대신 홈따옴표나 겹따옴표를 쓰려면 따옴표 앞에 백슬래시(\)를 추가하면 된다. 이스케이핑(escaping).
```python
fred = 'He said, \"Aren\'t can\'t shouldn\'t wouldn\'t'
```
- 문자열에 값을 포함할 수 있다. "%s"를 이용하면 된다. 
```python 
my_score = 100
message = "I scored %s"
print(message % my_score)
```
- 2개 이상의 값을 넣고 싶다면 ()를 쓴다. * 이게 tupple 인가?
```python 
my_score = 100
my_turns = 5
message = "I scored %s points by %s"
print(message % (my_score, my_turns))
```





4/25 - py4e > chpater 11-3 
```python
### 데이타 파싱하여 이메일 호스팅 찾아내기 
data = 'From stephen.marquard@uct.ac.za Sat Jan 5 09:14:15 2009'
atpos = data.find('@')
print(atpos)

sppos = data.find(' ', atpos)
print(sppos)

host = data[atpos+1 : sppos]
print(host)


### 다른 방법
line = 'From stephen.marquard@uct.ac.za Sat Jan 5 09:14:15 2009'

words = line.split()
email = words[1]
pieces = email.split('@')
print(pieces[1])


### 정규식 이용하기
import re
lin = 'From stephen.marquard@uct.ac.za Sat Jan 5 09:14:15 2009'
y = re.findall('^From .*@([^ ]*)', lin)
print(y)




```


4/23 - py4e > chapter 11-2
```python 
### re.finall()은 빈 리스트 혹으 sub-strings의 리스트를 반환한다. regular expression 에 일치하는 ...
### [0-9]+ == " 한 자리 이상으로, 0~9 중 일치하는 숫자 찾기 
### [AEIOUM]+ == A, E, I, O, U, M 으로 시작한 한글자 이상의 문자열 

import re
x = 'My 2 favorite numbers are 19 and 42'
y = re.findall('[0-9]+', x)
print(y)

y = re.findall('[AEIOUM]+', x)
print(y)

### Greedy Matching 
### 동일 조건이라면 "더 긴" 문자열을 선택하게 된다.
### ^F.+: 

### Non-Greedy Matching 
### 동일 조건이라면 "더 짧은" 문자열을 선택하 된다. 
### ^F.+?: 

import re
x = 'My 2 favorite numbers are 19 and 42'
y = re.findall('[0-9]+', x)
print(y)

y = re.findall('[AEIOUM]+', x)
print(y)



### 
### \S+@\S+ 

import re
x = 'From stephen.marquard@uct.ac.za Sat Jan 5 09:13:16 2009'
y = re.findall('\S+@\S+', x)
print(y)

y = re.findall('^From (\S+@\S+)', x)
print(y)


```


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
