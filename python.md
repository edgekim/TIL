# Today-I-Learned-
Today I Learned 💚🤓🌱

<h3>Python</h3>

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
