# Assignment #2: 语法练习

*Updated: 2026-09-14 13:34 (GMT+8)*  
*完成学生：<mark>李佳颖、药学院</mark>*



>**说明：**
>
>截止日期：前三周作业统一于 9月29日 提交至 Canvas 平台。
>
>内容要求：每个题目包含：**解题思路**（可选）、**源代码**、**Accepted 截图**、**预估耗时**（可选）。



## 1. 题目

### 31197: Police Recruits

implementation, 800, http://cs101.openjudge.cn/practice/31197/

思路：



代码

```python
n = int(input())
events=list(map(int,input().split()))
police=0
things=0
for event in events:
    if event>0:
        police+=event
    elif event<0:
        if police>0:
            police-=1
        else:
            things+=1
print(things)
```



代码运行截图 <mark>（至少包含有"Accepted"）</mark>
<img width="1307" height="861" alt="屏幕截图 2026-09-14 223943" src="https://github.com/user-attachments/assets/cb196a03-016f-45f7-8273-05773d24c174" />





### 31183: 一道题搞懂输入

http://cs101.openjudge.cn/practice/31183/

思路：



代码

```python
mode = int(input().strip())
if mode == 1:
        s = input()
        print(s)

elif mode == 2:
        x = int(input().strip())
        print(x * x)

elif mode == 3:
        parts = input().split()
        print(' '.join(parts[::-1]))

elif mode == 4:
        a, b = map(int, input().split())
        print(f"{a + b} {a * b}")

elif mode == 5:
        nums = list(map(int, input().split()))
        print(f"{len(nums)} {sum(nums)} {max(nums)}")

elif mode == 6:
        total = 0
        while True:
            line = input()
            if line == "END":
                break
            total += int(line)
        print(total)

elif mode == 7:
        n = int(input().strip())
        results = []
        for _ in range(n):
            a, b = map(int, input().split())
            results.append(str(a + b))
        print(' '.join(results))

elif mode == 8:
        parts = input().split(',')
        print(' '.join(parts[::-1]))
```



代码运行截图 <mark>（至少包含有"Accepted"）</mark>
<img width="1292" height="1089" alt="屏幕截图 2026-09-19 142803" src="https://github.com/user-attachments/assets/45e60fa4-b1f1-47ce-aae8-599d1e3d0932" />





### 31184: 一道题搞懂输出

http://cs101.openjudge.cn/practice/31184/

思路：



代码

```python
mode=int(input())
if mode==1:
    x=int(input())
    print(abs(x))
if mode==2:
    a,b,c=map(int,input().split())
    print(a+b,b+c,a+c)
if mode==3:
    a,b,c=map(int,input().split())
    print(f"[a+b]\n[b+c]\n[a+c]")
if mode==4:
    a,b,c=input().split()
    print(f"[a]->[b]->[c]")
if mode==5:
    n=int(input())
    a=list(map(int,input().split()))
    for i in a:
        print(i,end="#")
if mode==6:
    n=int(input())
    m=list(map(int,input().split()))
    m.sort(reverse=True)
    print(" ".join(map(str,m)))
if mode==7:
    a,b=map(int,input().split())
    print(f"{a}*{b}={a*b}")
if mode==8:
    a,b=map(int,input().split())
    result=a/b
    print(f"{result:.3f}")
if mode==9:
    n=int(input())
    m=list(map(int,input().split()))
    print(",".join(map(str,m)))
```



代码运行截图 <mark>（至少包含有"Accepted"）</mark>
<img width="2113" height="1187" alt="屏幕截图 2026-09-18 193748" src="https://github.com/user-attachments/assets/abe6f56c-1971-4a03-84ca-0f0d17f6b927" />





### 31198: Beautiful Matrix

implementation, 800, http://cs101.openjudge.cn/practice/31198/

思路：



代码

```python
found=False
m=0
for i in range(5):
    if found==True:
        break
    m+=1
    l=list(map(int,input().split()))
    n=0
    for j in l:
        n+=1
        if j==1:
            found=True
            break
print(abs(m-3)+abs(n-3))

```



代码运行截图 <mark>（至少包含有"Accepted"）</mark>
<img width="975" height="921" alt="屏幕截图 2026-09-19 101631" src="https://github.com/user-attachments/assets/567d3c8c-64c3-4965-a5c2-646c5fb34069" />





### E02808: 校门外的树

implementation, http://cs101.openjudge.cn/pctbook/E02808/

思路：



代码

```python
L,M=map(int,input().split())
trees
=[1]*(L+1)
for i in range(M):
    a
,b=map(int,input().split())
    trees
[a:b+1]=[0]*(b-a+1)
print(sum(trees))
```



代码运行截图 <mark>（至少包含有"Accepted"）</mark>
<img width="1295" height="830" alt="屏幕截图 2026-09-19 142218" src="https://github.com/user-attachments/assets/611f1562-b1c2-4cfc-8d37-a1a95f767525" />







### M01922: Ride to School

implementation, http://cs101.openjudge.cn/pctbook/M01922/

思路：



代码

```python
a=int(input())
for i in range(a):
    n=int(input())
    number=0


    def count_divisors(m):
        count = 0
        b = 1
        while b <= m:

            if m % b == 0:
                count += 1
            b += 1
        return count
    for j in range(1,n+1):


        if count_divisors(j)%2==1:
            number+=1
    print(number)
```



代码运行截图 <mark>（至少包含有"Accepted"）</mark>



<img width="1295" height="830" alt="屏幕截图 2026-09-19 142218" src="https://github.com/user-attachments/assets/b0f9e25a-aa17-469f-90ed-09ed93e9ccf0" />





## 2. 学习总结和收获

<mark>如果作业题目简单，有否额外练习题目，比如：OJ“计概2026fall每日选做”、CF、LeetCode、洛谷等网站题目。</mark>





