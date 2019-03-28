## python을 이용해서 시간요금계산기를 만들어보려고 한다.

#정책 
1. 시작시각과 종료시각을 입력받아 duration_time을 산출한다.
2. duration_time을 단위시간을 나눈 후, 단위시간을 요금으로 곱하여 총요금을 계산한다. 
3. (요금이 너무 많이 나오면 안되니...) 24시간 최대요금을 신설한다. 이용시간이 24시간을 초과할 경우, 계산요금을 24시간 최대요금으로 치환하여 적용한다.
4. 24시간 최대요금이라는 정책은, 반복하는 24시간을 최대요금으로 치환하는 것이니, 연박이 발생하면 24시간 최대요금이 연박만큼 추가된다. 


ver. 0328 ... 내가 뭘하고 있는지 모르겠다. 
```python
from datetime import datetime, timedelta #날짜 클래스를 가져와야겠지. 타임스탬프는 필요없나?
import math #올림 사용하려면 ??



#parking_lot_product / 주차장의 상품정보를 요일별로 저장해두자
extra_fare_time = [15, 15, 15, 15, 15, 15, 15, 15] #일월화수목금토일+공휴일 (8개)
extra_fare = [600, 600, 600, 600, 600, 600, 600, 600] #일월화수목금토일+공휴일 (8개)
basic_fare_time = [30, 30, 30, 30, 30, 30, 30, 30]
basic_fare = [1200, 1200, 1200, 1200, 1200, 1200, 1200, 1200] #일월화수목금토일+공휴일 (8개)
time_ticket_02 = [2000, 2000, 2000, 2000, 2000, 2000, 2000, 2000]
time_ticket_06 = [4000, 4000, 4000, 4000, 4000, 4000, 4000, 4000]
time_ticket_24 = [10000, 10000, 10000, 10000, 10000, 10000, 10000, 10000]
h24_cab_price = [15000, 15000, 15000, 15000, 15000, 15000, 15000, 15000]


price = list([0,0,0,0,0])
#요금합계는 1) 기본요금 or 시간권  + 2) 첫 24시간 요금 + 3) 마지막 24시간 요금 + 4) 중간일 24시간 요금으로 구성된다.

#주어져야 하는 값: 1) 선택요금 2) 입차, 출차시각

duration_time = 1200
selected_product = 0
if selected_product == 0:
    if duration_time <= 1440: # 24시간 미만인 경우
        first_period = basic_fare_time[0]
        first_period_fare = basic_fare[0]
        rest_f24_time = duration_time - first_period
        rest_f24_extra_period_cnt = math.ceil(rest_f24_time / extra_fare_time )
        rest_f24_fare = min(first_period_fare + rest_f24_extra_period_cnt * extra_fare[0] , h24_cab_price)
    else:
        print(1)
        
else:
    print(1)

```

ver. 0327 (째려만 보다가 끝났다....)
```
from datetime import datetime, timedelta #날짜 클래스를 가져와야겠지. 타임스탬프는 필요없나?
import math #올림 사용하려면 ??



#parking_lot_product / 주차장의 상품정보를 요일별로 저장해두자
extra_fare_time = [15, 15, 15, 15, 15, 15, 15, 15] #일월화수목금토일+공휴일 (8개)
extra_fare = [600, 600, 600, 600, 600, 600, 600, 600] #일월화수목금토일+공휴일 (8개)
basic_fare_time = [30, 30, 30, 30, 30, 30, 30, 30]
extra_fare = [1200, 1200, 1200, 1200, 1200, 1200, 1200, 1200] #일월화수목금토일+공휴일 (8개)
time_ticket_02 = [2000, 2000, 2000, 2000, 2000, 2000, 2000, 2000]
time_ticket_06 = [4000, 4000, 4000, 4000, 4000, 4000, 4000, 4000]
time_ticket_24 = [10000, 10000, 10000, 10000, 10000, 10000, 10000, 10000]
24h_cab_price = [15000, 15000, 15000, 15000, 15000, 15000, 15000, 15000]



duration_time = int(input("enter your duration_time:")) #정수로 만들자, 종료시각 - 시각시각 으로 duration_time을 구할 것인데,,, 종료시각, 시작시각은 timedate 사용법을 알아야하니 ... 나중에
24hs_cnt = 0 #24시간 이상인 구간이 몇개인지 카운트하자
24hs_cnt = duration_time // 1440
selected_option = 0 #basic_fare_time == 0 


24hs_cnt > 

period_time = int(10) #기본시간 설정
period_price = int(1000) #기본요금 설정
period_cnt = int(0) #duration_time 을 period_time으로 나눠서 몇 구간을 반복하는지 카운트할 거다. 우선 초기화 하자.
calculated_price = int(0)
max_24h_price = int(15000) #24시간 최대요금을 설정할 수 있다. 우선 15,000으로 설정하자.
n24h_cnt = int(0)
total_price = int(0)

if n24h_cnt == 0:
    period_cnt = math.ceil(duration_time / period_time)
    calculated_price = period_cnt * period_price
    calculated_price = min(calculated_price, max_24h_price)
elif n24h_cnt == 1:
    period_cnt = math.ceil((duration_time % 1440) / period_time)
    calculated_price = period_cnt * period_price
    calculated_price = min(calculated_price, max_24h_price) + max_24h_price
else :
    n = duration_time // 1440
    period_cnt = math.ceil((duration_time % 1440) / period_time)
    calculated_price = period_cnt * period_price
    calculated_price = min(calculated_price, max_24h_price) + (max_24h_price * n)

total_price = calculated_price

print("기간은:", duration_time)
print("n24h횟수:", n24h_cnt )
print("잔여구간반복수:", period_cnt)
print("계산요금:", calculated_price)
print("최종요금:", total_price)

```


ver. 0326
시간요금 계산기의 구조를 이제야 깨달았다.
하나. 시간요금의 '기본요금'은 시간권과 동일한 것이라봐도 무방하다.
둘. 기본적으로 기본요금과 추가요금은 요일별로 상이하지 않지만 난이도를 높이기위해 요일별로 상이하다는 설정을 했다. 
https://docs.google.com/spreadsheets/d/1cA0sraApgQtyWQdBfBZ1sjhBVogtEhv2FQyQfIDtpPg/edit#gid=0

각항목의 값을 리스트로 만들어서 미리 넣어둬야겠다. 
아직 DB를 사용할 줄 모르니 ... 

```python
from datetime import datetime, timedelta #날짜 클래스를 가져와야겠지. 타임스탬프는 필요없나?
import math #올림 사용하려면 ??

#parking_lot_product / 주차장의 상품정보를 요일별로 저장해두자 
extra_fare_time = [15, 15, 15, 15, 15, 15, 15, 15] #일월화수목금토일+공휴일 (8개)
extra_fare = [600, 600, 600, 600, 600, 600, 600, 600] #일월화수목금토일+공휴일 (8개)
basic_fare_time = [30, 30, 30, 30, 30, 30, 30, 30]
extra_fare = [1200, 1200, 1200, 1200, 1200, 1200, 1200, 1200] #일월화수목금토일+공휴일 (8개)
time_ticket_02 = [2000, 2000, 2000, 2000, 2000, 2000, 2000, 2000]
time_ticket_06 = [4000, 4000, 4000, 4000, 4000, 4000, 4000, 4000]
time_ticket_24 = [10000, 10000, 10000, 10000, 10000, 10000, 10000, 10000]
24h_cab_price = [15000, 15000, 15000, 15000, 15000, 15000, 15000, 15000]





period_time = int(10) #기본시간 설정
period_price = int(1000) #기본요금 설정
period_cnt = int(0) #duration_time 을 period_time으로 나눠서 몇 구간을 반복하는지 카운트할 거다. 우선 초기화 하자.
calculated_price = int(0)
max_24h_price = int(15000) #24시간 최대요금을 설정할 수 있다. 우선 15,000으로 설정하자.
n24h_cnt = int(0)
total_price = int(0)

duration_time = int(input("enter your duration_time:")) #정수로 만들자, 종료시각 - 시각시각 으로 duration_time을 구할 것인데,,, 종료시각, 시작시각은 timedate 사용법을 알아야하니 ... 나중에
n24h_cnt = duration_time // 1440 #연박이용여부를 확인하자

if n24h_cnt == 0:
    period_cnt = math.ceil(duration_time / period_time)
    calculated_price = period_cnt * period_price
    calculated_price = min(calculated_price, max_24h_price)
elif n24h_cnt == 1:
    period_cnt = math.ceil((duration_time % 1440) / period_time)
    calculated_price = period_cnt * period_price
    calculated_price = min(calculated_price, max_24h_price) + max_24h_price
else :
    n = duration_time // 1440
    period_cnt = math.ceil((duration_time % 1440) / period_time)
    calculated_price = period_cnt * period_price
    calculated_price = min(calculated_price, max_24h_price) + (max_24h_price * n)

total_price = calculated_price

print("기간은:", duration_time)
print("n24h횟수:", n24h_cnt )
print("잔여구간반복수:", period_cnt)
print("계산요금:", calculated_price)
print("최종요금:", total_price)
```



ver. 0325
```python
from datetime import datetime, timedelta #날짜 클래스를 가져와야겠지. 타임스탬프는 필요없나?
import math #올림 사용하려면 ??

period_time = int(10) #기본시간 설정
period_price = int(1000) #기본요금 설정
period_cnt = int(0) #duration_time 을 period_time으로 나눠서 몇 구간을 반복하는지 카운트할 거다. 우선 초기화 하자.
calculated_price = int(0)
max_24h_price = int(15000) #24시간 최대요금을 설정할 수 있다. 우선 15,000으로 설정하자.
n24h_cnt = int(0)
total_price = int(0)

duration_time = int(input("enter your duration_time:")) #정수로 만들자, 종료시각 - 시각시각 으로 duration_time을 구할 것인데,,, 종료시각, 시작시각은 timedate 사용법을 알아야하니 ... 나중에
n24h_cnt = duration_time // 1440 #연박이용여부를 확인하자

if n24h_cnt == 0:
    period_cnt = math.ceil(duration_time / period_time)
    calculated_price = period_cnt * period_price
    calculated_price = min(calculated_price, max_24h_price)
elif n24h_cnt == 1:
    period_cnt = math.ceil((duration_time % 1440) / period_time)
    calculated_price = period_cnt * period_price
    calculated_price = min(calculated_price, max_24h_price) + max_24h_price
else :
    n = duration_time // 1440 
    period_cnt = math.ceil((duration_time % 1440) / period_time)
    calculated_price = period_cnt * period_price
    calculated_price = min(calculated_price, max_24h_price) + (max_24h_price * n)

total_price = calculated_price

print("기간은:", duration_time)
print("n24h횟수:", n24h_cnt )
print("잔여구간반복수:", period_cnt)
print("계산요금:", calculated_price)
print("최종요금:", total_price)

```


ver. 0324
```python
from datetime import datetime, timedelta #날짜 클래스를 가져와야겠지. 타임스탬프는 필요없나?
import math #올림 사용하려면 ??

period_time = int(5) #기본시간 설정
period_price = int(1000) #기본요금 설정
period_cnt = int(0) #duration_time 을 period_time으로 나눠서 몇 구간을 반복하는지 카운트할 거다. 우선 초기화 하자.
calculated_price = int(0)
max_24h_price = int(15000) #24시간 최대요금을 설정할 수 있다. 우선 15,000으로 설정하자.
total_price = int(0)

duration_time = int(input("enter your duration_time:")) #정수로 만들자, 종료시각 - 시각시각 으로 duration_time을 구할 것인데,,, 종료시각, 시작시각은 timedate 사용법을 알아야하니 ... 나중에

period_cnt = math.ceil(duration_time / period_time) #나머지가 있다면 무조건 올림하자, 입력밧이 0이 될 수 있으니 이를 대비해 올림으로 처리하자
calculated_price = period_cnt * period_price

if calculated_price >= max_24h_price: #계산요금이 24시간 최대요금보다 크거나 같으면 최종요금을 24시간 최대요금으로 치환한다.
    total_price = max_24h_price
else:
    total_price = calculated_price


print("기간은:", duration_time)
print("구간반복수:", period_cnt)
print("계산요금:", calculated_price)
print("24h 최대요금:", max_24h_price)
print("최종요금:", total_price)

```


ver. 0323
```python
from datetime import datetime, timedelta #날짜 클래스를 가져와야겠지. 타임스탬프는 필요없나?
import math #올림 사용하려면 ??

period_time = int(5) #기본시간 설정
period_price = int(1000) #기본요금 설정
period_cnt = int(0) #duration_time 을 period_time으로 나눠서 몇 구간을 반복하는지 카운트할 거다. 우선 초기화 하자.
total_price = int(0)

duration_time = int(input("enter your duration_time:")) #정수로 만들자, 종료시각 - 시각시각 으로 duration_time을 구할 것인데,,, 종료시각, 시작시각은 timedate 사용법을 알아야하니 ... 나중에

period_cnt = math.ceil(duration_time / period_time) #나머지가 있다면 무조건 올림하자, 입력밧이 0이 될 수 있으니 이를 대비해 올림으로 처리하자
total_price = period_cnt * period_price

print("기간은:", duration_time)
print("구간반복수:", period_cnt)
print("최종요금:", total_price)
```

