
# <문제>
계좌에 들어있는 돈 일부를 은행에서 출금하고자 합니다. 돈 담을 지갑이 최대한 가볍도록 큰 금액의 화폐 위주로 받습니다. 돈의 액수 money가 매개변수로 주어질 때, 
오만 원권, 만 원권, 오천 원권, 천 원권, 오백원 동전, 백원 동전, 오십원 동전, 십원 동전, 일원 동전 각 몇개로 변환되는지 금액이 큰 순서대로 배열에 담아 return하도록 
solution 메소드를 원성하세요. 

<제한사항>
money는 1 이상 1,000,000 이하인 자연수입니다. 


<3/20>

``` python
money = input("Enter your money amount:") #input을 받는다.
money = int(money)#string 자료형을 int로 변경한다. 
result = list([0,0,0,0,0,0,0,0,0]) #list에 9개 항목을 각각 0으로 선언해두자.

if money >= 50000: #50,000원 이상인 경우
    result[0] = money//50000 #50,000으로 나눠서 몫을 list 에 저장한다.
    money = money%50000
if money >= 10000:
    result[1] = money//10000
    money = money%10000
if money >= 5000:
    result[2] = money//5000
    money = money%5000
if money >= 1000:
    result[3] = money//1000
    money = money%1000
if money >= 500:
    result[4] = money//500
    money = money%500
if money >= 100:
    result[5] = money//100
    money = money%100
if money >= 50:
    result[6] = money//50
    money = money%50
if money >= 10:
    result[7] = money//10
    money = money%10
else :
    result[8] = money
    money = 0

print (result)
```



<3/19>
```python
money = int(164353)
print(money) #최초 money 값을 체크하자.
result = list([0,0,0,0,0,0,0,0,0]) #list에 9개 항목을 각각 0으로 선언해두자.

while money != 0:  #잔액이 0원이 될 때까지 반복한다.
    if money >= 50000: #50,000원 이상인 경우
        result[0] = money//50000 #50,000으로 나눠서 몫을 list 에 저장한다.
        money = money%50000
    elif money >= 10000:
        result[1] = money//10000
        money = money%10000
    elif money >= 5000:
        result[2] = money//5000
        money = money%5000
    elif money >= 1000:
        result[3] = money//1000
        money = money%1000
    elif money >= 500:
        result[4] = money//500
        money = money%500
    elif money >= 100:
        result[5] = money//100
        money = money%100
    elif money >= 50:
        result[6] = money//50
        money = money%50
    elif money >= 10:
        result[7] = money//10
        money = money%10
    else :
        result[8] = money
        money = 0
```
