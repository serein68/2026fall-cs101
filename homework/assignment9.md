## Assignment #9: 11月考

*Updated: 2026-11-05 (GMT+8)*  
*完成学生：<mark>李佳颖、药学院</mark>*



>要求：每个题目包含：**解题思路**（可选）、**源代码**、**Accepted 截图**、**预估耗时**（可选）。
>



## 1. 题目

### E31529:双重回文

http://cs101.openjudge.cn/practice/31529/

思路：



代码

```python
n=int(input())
an=[]
for i in range(1,n+1):
    si=str(i)
    l=list(si)
    l_=list(reversed(l))
    bi=bin(i)[2:]
    bl=list(bi)
    bl_=list(reversed(bl))
    if l==l_ and bl==bl_:
        an.append(i)
print(len(an),max(an))
```



代码运行截图 <mark>（至少包含有"Accepted"）</mark>
<img width="1486" height="780" alt="image" src="https://github.com/user-attachments/assets/b180c63e-f756-4de6-8ba7-158a3dd633eb" />





### E31530:图书馆选座

http://cs101.openjudge.cn/practice/31530/

思路：



代码

```python
n, m = map(int, input().split())
s = list(input().strip())
p = 0

for i in range(n):
    if p == m:
        break

    if s[i] == "0":
        if (i == 0 or s[i - 1] == "0") and \
           (i == n - 1 or s[i + 1] == "0"):
            s[i] = "1"
            p += 1

print(p)
print("".join(s))
```



代码运行截图 <mark>（至少包含有"Accepted"）</mark>
<img width="1670" height="1008" alt="image" src="https://github.com/user-attachments/assets/03b7b87f-9a90-488b-96fc-7e66be7c6bfc" />




### M31531:箭头迷阵

http://cs101.openjudge.cn/practice/31531/

思路：



代码

```python
n,m=map(int,input().split())
l=[list(input().strip()) for _ in range(n)]

l_=[["0"]*m for _ in range(n)]
def f(a,b):
    if not (0<=a<n and 0<=b<m):
        return True
    if l_[a][b]=="y":
        return True
    if l_[a][b]=="n":
        return False
    if l_[a][b]=="1":
        return False
    if l_[a][b]=="0":
        l_[a][b]="1"
        if l[a][b]=="U":
            re=f(a-1,b)
        if l[a][b]=="D":
            re=f(a+1,b)
        if l[a][b]=="L":
            re=f(a,b-1)
        if l[a][b]=="R":
            re=f(a,b+1)
        l_[a][b]="y" if re else "n"
        return re
for i in range(n):
    for j in range(m):
        f(i,j)
p=0
for i in range(n):
    for j in range(m):
        if l_[i][j]=="y":
            p+=1
print(p)
```



代码运行截图 <mark>（至少包含有"Accepted"）</mark>
<img width="1384" height="1480" alt="image" src="https://github.com/user-attachments/assets/d6bdf1b4-95c3-4d58-a49a-5753306bd424" />





### M31532:牌堆魔术

http://cs101.openjudge.cn/practice/31532/

思路：



代码

```python
from collections import deque
n=int(input())
c=deque()
for i in range(n,0,-1):
    c.appendleft(i)
    c.appendleft(c.pop())
print(*c)
```



代码运行截图 <mark>（至少包含有"Accepted"）</mark>
<img width="1546" height="564" alt="image" src="https://github.com/user-attachments/assets/d352fac0-e5bd-45fa-b64d-e542f94c6c95" />





### M31533:渗透实验

http://cs101.openjudge.cn/practice/31533/

思路：



代码

```python
import sys

def main():
    input = sys.stdin.buffer.readline
    n, m, q = map(int, input().split())

    total = n * m
    parent = list(range(total))
    size = [1] * total
    touches_top = [False] * total
    touches_bottom = [False] * total
    opened = bytearray(total)

    def find(x):
        while parent[x] != x:
            parent[x] = parent[parent[x]]
            x = parent[x]
        return x

    def union(a, b):
        a = find(a)
        b = find(b)
        if a == b:
            return touches_top[a] and touches_bottom[a]

        if size[a] < size[b]:
            a, b = b, a

        parent[b] = a
        size[a] += size[b]
        touches_top[a] |= touches_top[b]
        touches_bottom[a] |= touches_bottom[b]
        return touches_top[a] and touches_bottom[a]

    for step in range(1, q + 1):
        r, c = map(int, input().split())
        r -= 1
        c -= 1
        cell = r * m + c

        opened[cell] = 1
        touches_top[cell] = (r == 0)
        touches_bottom[cell] = (r == n - 1)

        if touches_top[cell] and touches_bottom[cell]:
            print(step)
            return

        for dr, dc in ((-1, 0), (1, 0), (0, -1), (0, 1)):
            nr, nc = r + dr, c + dc
            if 0 <= nr < n and 0 <= nc < m:
                neighbor = nr * m + nc
                if opened[neighbor] and union(cell, neighbor):
                    print(step)
                    return

    print(-1)

if __name__ == "__main__":
    main()
```



代码运行截图 <mark>（至少包含有"Accepted"）</mark>
<img width="2188" height="1108" alt="image" src="https://github.com/user-attachments/assets/e8a0de31-71fd-409b-a2ef-9805c8b4d2b6" />





### T31534:括号区间审计

http://cs101.openjudge.cn/practice/31534/

思路：



代码

```python
import sys

input = sys.stdin.buffer.readline

s = input().strip().decode()
n = len(s)
q = int(input())

# prefix[i] 表示前 i 个字符的括号和
prefix = [0] * (n + 1)
for i, ch in enumerate(s, start=1):
    prefix[i] = prefix[i - 1] + (1 if ch == '(' else -1)

# 线段树：维护 prefix 数组区间最小值
size = 1
while size < n + 1:
    size *= 2

INF = 10**9
tree = [INF] * (2 * size)

for i, value in enumerate(prefix):
    tree[size + i] = value

for i in range(size - 1, 0, -1):
    tree[i] = min(tree[2 * i], tree[2 * i + 1])

def range_min(left, right):
    """查询 prefix[left:right+1] 的最小值"""
    left += size
    right += size
    result = INF

    while left <= right:
        if left % 2 == 1:
            result = min(result, tree[left])
            left += 1
        if right % 2 == 0:
            result = min(result, tree[right])
            right -= 1
        left //= 2
        right //= 2

    return result

answers = []
for _ in range(q):
    l, r = map(int, input().split())

    base = prefix[l - 1]
    if prefix[r] == base and range_min(l, r) >= base:
        answers.append("YES")
    else:
        answers.append("NO")

sys.stdout.write("\n".join(answers))
```



代码运行截图 <mark>（至少包含有"Accepted"）</mark>
<img width="2086" height="1074" alt="屏幕截图 2026-11-06 160251" src="https://github.com/user-attachments/assets/60c82c4b-8070-4c97-8747-5048bd7a6a68" />





## 2. 学习总结和收获

<mark>如果作业题目简单，有否额外练习题目，比如：OJ“计概2026fall每日选做”、CF、LeetCode、洛谷等网站题目。</mark>



