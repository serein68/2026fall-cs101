## Assignment #7: 矩阵、贪心

*Updated: 2026-10-19 (GMT+8)*  
*完成学生：<mark>同学的姓名、院系</mark>*



>要求：每个题目包含：**解题思路**（可选）、**源代码**、**Accepted 截图**、**预估耗时**（可选）。
>



## 1. 题目

### M12560: 生存游戏

matrices, http://cs101.openjudge.cn/pctbook/M12560/

思路：



代码

```python
n,m=map(int,input().split())
cell=[[0]*(m+2) for i in range(n+2)]
cells=[list(map(int,input().split())) for i in range(n)]
for i in range(n):
    for j in range(m):
        cell[i+1][j+1]=cells[i][j]
for i in range(1,n+1):
    for j in range(1,m+1):
        if cell[i][j]==1:
            l=0
            for p,q in [(0,1),(1,0),(-1,0),(0,-1),(1,1),(-1,-1),(1,-1),(-1,1)]:
                ii,jj=i+p,j+q
                if cell[ii][jj]==1:
                    l+=1
            if l==2 or l==3:
                cells[i-1][j-1]=1
            else:
                cells[i-1][j-1]=0
        else:
            l=0
            for p,q in [(0,1),(1,0),(-1,0),(0,-1),(1,1),(-1,-1),(1,-1),(-1,1)]:
                ii,jj=i+p,j+q
                if cell[ii][jj]==1:
                    l+=1
            if l==3:
                cells[i-1][j-1]=1
for i in range(n):
    print(*cells[i])
```



代码运行截图 <mark>（至少包含有"Accepted"）</mark>

<img width="1844" height="1290" alt="屏幕截图 2026-11-06 153335" src="https://github.com/user-attachments/assets/c36aba54-48f8-4a24-b455-63c2907b267b" />




### M04133:垃圾炸弹

matrices, http://cs101.openjudge.cn/pctbook/M04133/

思路：



代码

```python
d=int(input())
n=int(input())
g=[[0]*1025 for i in range(1025)]
for i in range(n):
    x,y,c=map(int,input().split())
    g[x][y]=c
perfix = [[0] * 1026 for _ in range(1026)]

for i in range(1025):
    s = 0
    for j in range(1025):
        s += g[i][j]
        perfix[i + 1][j + 1] = perfix[i][j + 1] + s
best=-1
ways=0
for i in range(1025):
    x1=max(0,i-d)
    x2=min(1024,i+d)
    for j in range(1025):
        y1=max(0,j-d)
        y2=min(1024,j+d)
        num = (
    perfix[x2 + 1][y2 + 1]
    - perfix[x1][y2 + 1]
    - perfix[x2 + 1][y1]
    + perfix[x1][y1]
)
        if num>best:
            best=num
            ways=1
        elif num==best:
            ways+=1
print(ways,best)

```



代码运行截图 <mark>（至少包含有"Accepted"）</mark>
<img width="1340" height="1400" alt="image" src="https://github.com/user-attachments/assets/48ec614d-f790-423d-89ef-16125897cf89" />





### M02746: 约瑟夫问题

implementation, queue, http://cs101.openjudge.cn/pctbook/M02746/

思路：



代码

```python
def josephus(n, k):
    survivor = 0  # 0-based 编号
    for size in range(2, n + 1):
        survivor = (survivor + k) % size
    return survivor + 1
while True:
    
    n,m=map(int,input().split())
    if n==0 and m==0:
        break
    print(josephus(n,m))
```



代码运行截图 <mark>（至少包含有"Accepted"）</mark>
<img width="1324" height="722" alt="image" src="https://github.com/user-attachments/assets/2065d59e-79ce-44ef-b9ac-42e47973986f" />





### M26976:摆动序列

greedy,dp, http://cs101.openjudge.cn/pctbook/M26976/

思路：



代码

```python
n = int(input())
nums = list(map(int, input().split()))

if n == 0:
    print(0)
else:
    length = 1
    prev_diff = 0

    for i in range(1, n):
        diff = nums[i] - nums[i - 1]

        if diff > 0 and prev_diff <= 0:
            length += 1
            prev_diff = diff
        elif diff < 0 and prev_diff >= 0:
            length += 1
            prev_diff = diff

    print(length)
```



代码运行截图 <mark>（至少包含有"Accepted"）</mark>
<img width="1500" height="1086" alt="image" src="https://github.com/user-attachments/assets/f83b8b6a-5cbb-4061-a44a-9f02d3931be5" />





### T26971:分发糖果

greedy, http://cs101.openjudge.cn/pctbook/T26971/

思路：



代码

```python
n=int(input())
a=list(map(int,input().split()))
c=[1]*n
for i in range(n-1):
    if a[i]<a[i+1]:
        c[i+1]=c[i]+1

for j in range(n-1,0,-1):
    if a[j-1]>a[j]:
        c[j-1]=max(c[j]+1,c[j-1])
print(sum(c))
```



代码运行截图 <mark>（至少包含有"Accepted"）</mark>
<img width="1552" height="1112" alt="image" src="https://github.com/user-attachments/assets/22772911-ef62-4460-b76b-d2ff6890ce5e" />





### 1868A. Fill in the Matrix

constructive algorithms, implementation, 1300, https://codeforces.com/problemset/problem/1868/A

思路：



代码

```python
import sys

data = list(map(int, sys.stdin.buffer.read().split()))
t = data[0]
idx = 1
out = []

for _ in range(t):
    n, m = data[idx], data[idx + 1]
    idx += 2

    beauty = 0 if m == 1 else min(n + 1, m)
    out.append(str(beauty))

    for i in range(min(n, m - 1)):
        out.append(" ".join(str((i + j) % m) for j in range(m)))

    for _ in range(n - min(n, m - 1)):
        out.append(" ".join(map(str, range(m))))

print("\n".join(out))
```



代码运行截图 <mark>（至少包含有"Accepted"）</mark>
<img width="1914" height="826" alt="屏幕截图 2026-11-06 154145" src="https://github.com/user-attachments/assets/3afe821a-0fcf-4298-ae5f-8f511272222a" />





## 2. 学习总结和收获

<mark>如果作业题目简单，有否额外练习题目，比如：OJ“计概2026fall每日选做”、CF、LeetCode、洛谷等网站题目。</mark>



