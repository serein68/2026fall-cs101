### Assignment #5: cs101 Mock Exam 寒露

*Updated: 2026-10-08 (GMT+8)*  
*完成学生：<mark>李佳颖、药学院</mark>*



>**说明：**
>
>截止日期：第四到六周作业统一于 10月20日 提交至 Canvas 平台。
>
>内容要求：每个题目包含：**解题思路**（可选）、**源代码**、**Accepted 截图**、**预估耗时**（可选）。
>



## 1. 题目

### E31295:宿舍的空调

http://cs101.openjudge.cn/practice/31295/

思路：



代码

```python
n=int(input())
an=[]
bi=[]
for i in range(n):
    a,b=map(int,input().split())
    an.append(a)
    bi.append(b)
if max(an)>min(bi):
    print(-1)
else:
    print(max(an))
```



代码运行截图 <mark>（至少包含有"Accepted"）</mark>

<img width="959" height="639" alt="image" src="https://github.com/user-attachments/assets/39684cb0-49be-48ed-b3ec-f363c8c6321e" />





### E31294:大肥鱼卖白饭

http://cs101.openjudge.cn/practice/31294/

思路：



代码

```python
n=int(input())
l=list(map(int,input().split()))
r=0
m=0
for i in range(n):
    if l[i]==5:
        r+=1
    if l[i]==10:
        if r<=0:
            print("NO")
            break
        else:
            r-=1
            m+=1
    if l[i]==20:
        if r>=1 and m>=1:
            r-=1
            m-=1
        elif r>=3:
            r-=3
        else:
            print("NO")
            break
else:
    print("YES")
```



代码运行截图 <mark>（至少包含有"Accepted"）</mark>

<img width="905" height="1165" alt="image" src="https://github.com/user-attachments/assets/e7ea2a8b-c71a-4e1a-b3b5-fc58d5f90ff9" />





### E31293:双十一凑单大作战

http://cs101.openjudge.cn/practice/31293/

思路：



代码

```python
n=int(input())
p=list(map(int,input().split()))
p.sort(reverse=True)
m=0
if n%3==0:
    for i in range(2,n,3):
        m+=p[i]
    print(sum(p)-m)    
if n%3==1:
    for i in range(2,n-1,3):
        m+=p[i]
    print(sum(p)-m)    
if n%3==2:
    for i in range(2,n-2,3):
        m+=p[i]
    print(sum(p)-m)   


```



代码运行截图 <mark>（至少包含有"Accepted"）</mark>

<img width="1060" height="826" alt="image" src="https://github.com/user-attachments/assets/7af81321-ba28-42a5-8c0a-1bd2f65558ec" />





### M31297:恒星共振裂变

http://cs101.openjudge.cn/practice/31297/

思路：



代码

```python
n=int(input()) 
max=1000000
prime=[True]*(max+1)
prime[0]=prime[1]=False
for i in range(2,int(max*0.5)+1):
    if prime[i]:
        for j in range(i*i,max+1,i):
            prime[j]=False
    
b=0
for i in range (n):
    a=int(input())
    for j in range(a//2,1,-1):
        b=j 
        if prime[j] and prime[a-j]:
            break
    print(b,a-b) 
```



代码运行截图 <mark>（至少包含有"Accepted"）</mark>

<img width="1088" height="892" alt="image" src="https://github.com/user-attachments/assets/d971358c-01b5-4f25-bc1a-ca49de765387" />





### M31296:“淹园”救援

http://cs101.openjudge.cn/practice/31296/

思路：



代码

```python
n,c=map(int,input().split())
w
=list(map(int,input().split()))
w
.sort()
left
=0
right
=n-1
boats
=0
while left<=right:
    if w[left]+w[right]<=c:
        left
+=1
    right
-=1
    boats
+=1
print(boats)
```



代码运行截图 <mark>（至少包含有"Accepted"）</mark>

<img width="1197" height="700" alt="image" src="https://github.com/user-attachments/assets/4070fe32-4d08-4e64-b5fd-55e7c7ee6187" />





### T31298:警察招募又来了

http://cs101.openjudge.cn/practice/31298/

思路：



代码

```python
import sys

input = sys.stdin.buffer.readline

n, m = map(int, input().split())  # m：警员最大服役时长
a = list(map(int, input().split()))

retire = []  # 按招募顺序记录退休分钟
head = 0
crime = 0

for t, event in enumerate(a, start=1):
    # 清除已过期警员
    while head < len(retire) and retire[head] < t:
        head += 1

    if event > 0:
        # 新警员从第 t 分钟开始服役，到 t + m - 1 分钟为止
        retire.extend([t + m - 1] * event)

    elif event == -1:
        if head < len(retire):
            head += 1  # 派出队首警员
        else:
            crime += 1

print(crime)
```



代码运行截图 <mark>（至少包含有"Accepted"）</mark>

<img width="1228" height="1185" alt="image" src="https://github.com/user-attachments/assets/53f9d1d2-031d-4daa-96df-a63b6b0913e9" />





## 2. 学习总结和收获

<mark>如果作业题目简单，有否额外练习题目，比如：OJ“计概2026fall每日选做”、CF、LeetCode、洛谷等网站题目。</mark>



