## Assignment #8: 递归

*Updated: 2026-10-27 (GMT+8)*  
*完成学生：<mark>同学的姓名、院系</mark>*



>要求：每个题目包含：**解题思路**（可选）、**源代码**、**Accepted 截图**、**预估耗时**（可选）。
>



## 1. 题目

### M04147: 汉诺塔问题(Tower of Hanoi)

dfs, http://cs101.openjudge.cn/pctbook/M04147

思路：



代码

```python
n,a,b,c=input().split()
n=int(n)
answers=[]
def f(n,a,b,c,answers):
    if n==0:
        return
    f(n-1,a,c,b,answers)
    answers.append(f"{n}:{a}->{c}")
    f(n-1,b,a,c,answers)

f(n,a,b,c,answers)


```



代码运行截图 <mark>（至少包含有"Accepted"）</mark>
<img width="1550" height="958" alt="屏幕截图 2026-11-06 154315" src="https://github.com/user-attachments/assets/7236ec7b-7a02-4a97-8a8c-e017f11e0067" />





### M05585: 晶矿的个数

matrices, dfs similar, http://cs101.openjudge.cn/pctbook/M05585

思路：



代码

```python
def f(a,b,color,list1,list2):
    d=[(0,1),(0,-1),(1,0),(-1,0)]
    n=len(list1)
    for x,y in d:
        ai,bi=a+x,b+y
        if ( 0 <= ai < n and 0 <= bi < n
                and list1[ai][bi] == color and not list2[ai][bi] ):
            list2[ai][bi]=True
            f(ai,bi,color,list1,list2)






k=int(input())
for i in range(1,k+1):
    n=int(input())
    grid=[list(input().strip()) for j in range(n)]
    visited=[[False]*n for _ in range(n)]
    red,black=0,0
    for p in range(n):
        for q in range(n):
            if grid[p][q]=="#"or visited[p][q]==True:
                continue
            visited[p][q]=True
            f(p,q,grid[p][q],grid,visited)
            if grid[p][q]=="r":
                red+=1
            elif grid[p][q]=="b":
                black+=1
    

```



代码运行截图 <mark>（至少包含有"Accepted"）</mark>
<img width="1568" height="1424" alt="屏幕截图 2026-11-06 154507" src="https://github.com/user-attachments/assets/3c7561fc-eae5-4b71-b643-b30c17ff9661" />





### M02786: Pell数列

dfs, dp, http://cs101.openjudge.cn/pctbook/M02786/

思路：



代码

```python
MOD = 32767

t = int(input())
ks = [int(input()) for _ in range(t)]

max_k = max(ks)
pell = [0] * (max_k + 1)

if max_k >= 1:
    pell[1] = 1
if max_k >= 2:
    pell[2] = 2

for i in range(3, max_k + 1):
    pell[i] = (2 * pell[i - 1] + pell[i - 2]) % MOD

for k in ks:
    print(pell[k])
```



代码运行截图 <mark>（至少包含有"Accepted"）</mark>
<img width="1544" height="1098" alt="屏幕截图 2026-11-06 154613" src="https://github.com/user-attachments/assets/490a57ab-5d76-4ccd-8486-6d84c9b8b26a" />





### M46.全排列

backtracking, https://leetcode.cn/problems/permutations/

思路：



代码

```python
class Solution:
    def permute(self, nums: list[int]) -> list[list[int]]:
        res=[]
        used=[False]*len(nums)
        path=[]
        def f():
            if len(res) == len(nums):
                path.append(res[:])
                

            for i in range(len(nums)):
                if used[i] == False:
                    used[i] = True
                    res.append(nums[i])
                    f()
                    res.pop()
                    used[i] = False
        f()
        return path
```



代码运行截图 <mark>（至少包含有"Accepted"）</mark>
<img width="2576" height="966" alt="image" src="https://github.com/user-attachments/assets/7ca68976-c628-4248-8ea8-2305b1ce5df9" />





### T02754: 八皇后

dfs and similar, http://cs101.openjudge.cn/pctbook/T02754

思路：



代码

```python
n = int(input())
queries = [int(input()) for _ in range(n)]

solutions = []
cols = []

def dfs(row):
    if row == 8:
        solutions.append("".join(map(str, cols)))
        return

    for col in range(1, 9):
        valid = True
        for r in range(row):
            if cols[r] == col or abs(cols[r] - col) == row - r:
                valid = False
                break

        if valid:
            cols.append(col)
            dfs(row + 1)
            cols.pop()

dfs(0)

for b in queries:
    print(solutions[b - 1])
```



代码运行截图 <mark>（至少包含有"Accepted"）</mark>
<img width="2006" height="1204" alt="image" src="https://github.com/user-attachments/assets/59e45612-7dcd-4197-b5dd-de89fc87110c" />





### T01958: Strange Towers of Hanoi

http://cs101.openjudge.cn/practice/01958/

思路：



代码

```python
h3 = [0] * 13
for n in range(1, 13):
    h3[n] = 2 * h3[n - 1] + 1

h4 = [0] * 13

for n in range(1, 13):
    h4[n] = min(
        2 * h4[n - k] + h3[k]
        for k in range(1, n + 1)
    )

for n in range(1, 13):
    print(h4[n])
```



代码运行截图 <mark>（至少包含有"Accepted"）</mark>
<img width="1618" height="738" alt="image" src="https://github.com/user-attachments/assets/65784c12-71bd-4fee-b07c-c4169ccc71ae" />





## 2. 学习总结和收获

<mark>如果作业题目简单，有否额外练习题目，比如：OJ“计概2026fall每日选做”、CF、LeetCode、洛谷等网站题目。</mark>



