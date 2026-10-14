### Assignment #6: 矩阵、贪心

*Updated: 2026-10-13 (GMT+8)*  
*完成学生：<mark>李佳颖、药学院</mark>*



>**说明：**
>
>截止日期：第四到六周作业统一于 10月20日 提交至 Canvas 平台。
>
>内容要求：每个题目包含：**解题思路**（可选）、**源代码**、**Accepted 截图**、**预估耗时**（可选）。
>



## 1. 题目

### M21554: 排队做实验

greedy, http://cs101.openjudge.cn/pctbook/M21554/

思路：



代码

```python
n = int(input())
t = list(map(int, input().split()))

# 按实验时长从短到长安排，时长相同则按原编号先后
order = sorted(range(n), key=lambda i: (t[i], i))

wait = 0
total_wait = 0

for i in order:
    total_wait += wait
    wait += t[i]

print(*(i + 1 for i in order))
print(f"{total_wait / n:.2f}")
```



代码运行截图 <mark>（至少包含有"Accepted"）</mark>
<img width="1142" height="745" alt="image" src="https://github.com/user-attachments/assets/0d021ba1-60ed-4bc3-9a4c-20dc462765c8" />





### M18211: 军备竞赛

greedy, two pointers, http://cs101.openjudge.cn/pctbook/M18211

思路：



代码

```python
p=int(input())
a=list(map(int,input().split()))
a.sort()
if p<a[0]:
    print(0)
elif p>=sum(a):
    print(len(a))
else:
    l=len(a)-2
    while True:
        if p>=sum(a[:l+1]):
            print(l+1)
            break
        else:
            stop=False
            for i in range(len(a)-1,l,-1):
                r=i
                if p+sum(a[r:])>=sum(a[:l+1]):
                    stop=True
                    print(l+1-len(a)+r)
                    break
            if stop:
                break
            else:
                l-=1
```



代码运行截图 <mark>（至少包含有"Accepted"）</mark>
<img width="1378" height="1107" alt="image" src="https://github.com/user-attachments/assets/cf111c4a-a72e-405c-8f9b-da4a040f636e" />





### E23555: 节省存储的矩阵乘法

implementation, matrices, http://cs101.openjudge.cn/pctbook/E23555

思路：



代码

```python
n,m1,m2=map(int,input().split())
a=[[0 for i in range(n)] for j in range(n)]
b=[[0 for p in range(n)] for q in range(n)]
for i in range(m1):
    h,l,y=map(int,input().split())
    a[h][l]=y
for i in range(m2):
    h,l,y=map(int,input().split())
    b[h][l]=y
c=[[sum(a[i][k]*b[k][j] for k in range(n))for j in range(n)]for i in range(n)]
for i in range(n):
    for j in range(n):
        if c[i][j]>0:
            print(i,j,c[i][j])
```



代码运行截图 <mark>（至少包含有"Accepted"）</mark>
<img width="1300" height="743" alt="image" src="https://github.com/user-attachments/assets/f3898c98-90de-4816-b3b9-1a9d8fdb58d8" />





### M12558: 岛屿周⻓

matrices, http://cs101.openjudge.cn/pctbook/M12558

思路：



代码

```python
n,m=map(int,input().split())
l=[list(map(int,input().split())) for _ in range(n)]
c=0
b=[(1,0),(-1,0),(0,1),(0,-1)]
for i in range(n):
    for j in range(m):
        if l[i][j]==1:
            for ni,nj in b:
                mi=i+ni
                mj=j+nj
                if not(0<=mi<n and 0<=mj<m) or l[mi][mj]==0:
                    c+=1
print(c)
```



代码运行截图 <mark>（至少包含有"Accepted"）</mark>
<img width="1300" height="754" alt="image" src="https://github.com/user-attachments/assets/4160d96a-39a6-46fc-b9a2-e4e18bb4a2e9" />





### M01328: Radar Installation

greedy, http://cs101.openjudge.cn/practice/01328/

思路：



代码

```python
import sys
import math
data=list(map(int,sys.stdin.read().split()))
a=0
case=1
answers=[]
while True:
    n,d=data[a],data[a+1]
    if n==0:
        break
    else:
        num=0
        possible=True
        q=[]
        for i in range(n):
            a+=2
            x,y=data[a],data[a+1]
            if y>d:
                possible=False
            else:
                half=math.sqrt(d*d-y*y)
                q.append([x-half,x+half])
        if not possible:
            num=-1
        else:
            radar=-float("inf")
            q.sort(key=lambda b: b[1])
            for r,l in q:
                if radar<r:
                    radar=l
                    num+=1
        answers.append(f"Case {case}: {num}")
        a+=2
        case+=1
print(*answers,sep="\n")
```



代码运行截图 <mark>（至少包含有"Accepted"）</mark>
<img width="1290" height="1234" alt="image" src="https://github.com/user-attachments/assets/f4818d50-0aee-4bbd-87fc-caaea71bf426" />





### 545C. Woodcutters

dp, greedy, 1500, https://codeforces.com/problemset/problem/545/C

思路：



代码

```python
n = int(input())
trees = [tuple(map(int, input().split())) for _ in range(n)]

# 状态：(目前最右侧已占据的位置, 已砍倒的树数)
states = [(-float("inf"), 0)]

for i, (x, h) in enumerate(trees):
    next_x = trees[i + 1][0] if i + 1 < n else float("inf")
    best = {}

    def keep(rightmost, count):
        best[rightmost] = max(best.get(rightmost, -1), count)

    for rightmost, count in states:
        # 不砍，树的位置 x 也会被占据
        if rightmost < x:
            keep(x, count)

            # 向左倒：[x-h, x]
            if rightmost < x - h:
                keep(x, count + 1)

            # 向右倒：[x, x+h]
            if x + h < next_x:
                keep(x + h, count + 1)

    states = list(best.items())

print(max(count for _, count in states))
```



代码运行截图 <mark>（至少包含有"Accepted"）</mark>
<img width="2003" height="1058" alt="image" src="https://github.com/user-attachments/assets/f219ec02-9a56-4563-84d9-3b6cef957042" />





## 2. 学习总结和收获

<mark>如果作业题目简单，有否额外练习题目，比如：OJ“计概2026fall每日选做”、CF、LeetCode、洛谷等网站题目。</mark>



