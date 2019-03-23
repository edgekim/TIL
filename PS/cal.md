## python을 이용해서 시간요금계산기를 만들어보려고 한다.

#정책 
1. 시작시각과 종료시각을 입력받아 duration_time을 산출한다.
2. duration_time을 단위시간을 나눈 후, 단위시간을 요금으로 곱하여 총요금을 계산한다. 

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

