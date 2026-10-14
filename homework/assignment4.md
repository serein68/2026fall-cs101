# Assignment #4: T-primes + 贪心

*Updated: 2026-09-28 (GMT+8)*  
*完成学生：<mark>李佳颖、药学院</mark>*



>**说明：**
>
>截止日期：第四到六周作业统一于 10月20日 提交至 Canvas 平台。
>
>内容要求：每个题目包含：**解题思路**（可选）、**源代码**、**Accepted 截图**、**预估耗时**（可选）。
>



## 1. 题目

### 34B. Sale

greedy, sorting, 900, https://codeforces.com/problemset/problem/34/B

思路：



代码

```python
n, m = map(int, input().split())
prices = list(map(int, input().split()))
prices.sort()

profit = 0
for i in range(min(n, m)):
    if prices[i] < 0:
        profit += -prices[i]
    else:
        break

print(profit)

```



代码运行截图 <mark>（至少包含有"Accepted"）</mark>

<img width="1947" height="497" alt="image" src="https://github.com/user-attachments/assets/3662bd3a-fd85-4089-9b92-07f2d9bec1a7" />





### 160A. Twins

greedy, sortings, 900, https://codeforces.com/problemset/problem/160/A

思路：



代码

```python
n=int(input())
values=list(map(int,input().split()))
values.sort()
a=0
num=0
while a<= sum(values):
    a+=values[len(values)-1]
    values.pop(len(values)-1)
    num+=1
print(num)
```



代码运行截图 <mark>（至少包含有"Accepted"）</mark>

<img width="1493" height="412" alt="image" src="https://github.com/user-attachments/assets/eb251a17-a827-4724-8e21-beead711ca15" />





### 1879B. Chips on the Board

constructive algorithms, greedy, 900, https://codeforces.com/problemset/problem/1879/B

思路：



代码

```python
t = int(input())

for _ in range(t):
    n = int(input())
    a = list(map(int, input().split()))
    b = list(map(int, input().split()))

    cost_all_rows = sum(a) + n * min(b)
    cost_all_columns = sum(b) + n * min(a)

    print(min(cost_all_rows, cost_all_columns))
```



代码运行截图 <mark>（至少包含有"Accepted"）</mark>

<img width="1742" height="432" alt="image" src="https://github.com/user-attachments/assets/237ae0d4-e0b5-43ac-9d2f-706933bcb349" />





### M01017: 装箱问题

greedy, http://cs101.openjudge.cn/pctbook/M01017/

思路：



代码

```python
import math
while True:
    l=list(map(int,input().split()))
    a=l[1]*4+l[2]*9+l[3]*16+l[4]*25+l[5]*36
    if l[0]==l[1]==l[2]==l[3]==l[4]==l[5]==0:
        break
    boxes=l[5]+l[4]+l[3]+math.ceil(l[2]/4)

    l[1]=max(l[1]-l[3]*5,0)
    l[2]=l[2]%4
    if l[2]==1:
        
        l[1]=max(l[1]-5,0)
    elif l[2]==2:
        
        l[1]=max(l[1]-3,0)
    elif l[2]==3:
    
        l[1]=max(l[1]-1,0)
    boxes+=math.ceil(l[1]/9)
    l[0]=max(l[0]-boxes*36+a,0)
    boxes+=math.ceil(l[0]/36)
    print(boxes)
```



代码运行截图 <mark>（至少包含有"Accepted"）</mark>

<img width="1296" height="1056" alt="image" src="https://github.com/user-attachments/assets/e56cf31e-2f04-41b3-a238-740f5b2add17" />





### M01008: Maya Calendar

implementation, http://cs101.openjudge.cn/practice/01008/

思路：



代码

```python
n = int(input())

months = {
    "pop": 0, "no": 1, "zip": 2, "zotz": 3, "tzec": 4,
    "xul": 5, "yoxkin": 6, "mol": 7, "chen": 8, "yax": 9,
    "zac": 10, "ceh": 11, "mac": 12, "kankin": 13,
    "muan": 14, "pax": 15, "koyab": 16, "cumhu": 17,
    "uayet": 18
}

names = [
    "imix", "ik", "akbal", "kan", "chicchan",
    "cimi", "manik", "lamat", "muluk", "ok",
    "chuen", "eb", "ben", "ix", "mem",
    "cib", "caban", "eznab", "canac", "ahau"
]

answers = []

for _ in range(n):
    day_text, month, year_text = input().split()

    day = int(day_text.rstrip("."))
    year = int(year_text)

    total_days = year * 365 + months[month] * 20 + day

    tzolkin_year = total_days // 260
    day_in_cycle = total_days % 260
    number = day_in_cycle % 13 + 1
    name = names[day_in_cycle % 20]

    answers.append(f"{number} {name} {tzolkin_year}")

print(n)
for answer in answers:
    print(answer)
```



代码运行截图 <mark>（至少包含有"Accepted"）</mark>

<img width="1290" height="1300" alt="image" src="https://github.com/user-attachments/assets/acdcb500-d61a-4b96-9f7c-cba56cba1516" />





### 230B. T-primes（选做）

binary search, implementation, math, number theory, 1300, http://codeforces.com/problemset/problem/230/B

思路：



代码

```python
from math import isqrt

# 这题的数最大是 10^12，所以平方根最大是 10^6
limit = 10**6

# 先假设 0 到 limit 都是素数
prime = [True] * (limit + 1)
prime[0] = prime[1] = False

# 把合数标记为 False
for i in range(2, isqrt(limit) + 1):
    if prime[i]:
        for j in range(i * i, limit + 1, i):
            prime[j] = False

n = int(input())
numbers = list(map(int, input().split()))

for x in numbers:
    root = isqrt(x)
    if root * root == x and prime[root]:
        print("YES")
    else:
        print("NO")
```



代码运行截图 <mark>（至少包含有"Accepted"）</mark>

<img width="1520" height="823" alt="image" src="https://github.com/user-attachments/assets/e8f26419-8ed4-47c2-a38d-d1581e24d24d" />





## 2. 学习总结和收获

<mark>如果作业题目简单，有否额外练习题目，比如：OJ“计概2026fall每日选做”、CF、LeetCode、洛谷等网站题目。</mark>



