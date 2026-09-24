# Assignment #3: 计算机原理与位运算

*Updated: 2026-09-22 (GMT+8)*  
*完成学生：<mark>李佳颖、药学院</mark>*



>**说明：**
>
>截止日期：前三周作业统一于 9月29日 提交至 Canvas 平台。
>
>内容要求：每个题目包含：**解题思路**（可选）、**源代码**、**Accepted 截图**、**预估耗时**（可选）。
>
>本次作业配合第 3 周《计算机原理（1/2）》课程内容，围绕二进制表示与位运算展开，6 道题目难度递增。



## 1. 题目

### P1100: 高低位交换

位运算, 普及-, https://www.luogu.com.cn/problem/P1100

思路：



代码

```python
n=int(input())
m=n%(2**16)
t=n//(2**16)
print(m*2**16+t)

```



代码运行截图 <mark>（至少包含有"Accepted"）</mark>
<img width="1139" height="458" alt="屏幕截图 2026-09-24 155311" src="https://github.com/user-attachments/assets/44f18175-fd2a-455d-87ed-dec4db8bc91b" />





### LC136: 只出现一次的数字

bit manipulation, Easy, https://leetcode.cn/problems/single-number/

思路：



代码

```python
class Solution:
    def singleNumber(self, nums: List[int]) -> int:
        a=0
        for i in nums:
            a^=i

        return a
```



代码运行截图 <mark>（至少包含有"Accepted"）</mark>
<img width="1317" height="1074" alt="屏幕截图 2026-09-24 155557" src="https://github.com/user-attachments/assets/07714008-a3bf-4e03-ae0e-72f0a2c1811d" />





### LC191: 位1的个数

bit manipulation, divide and conquer, Easy, https://leetcode.cn/problems/number-of-1-bits/

思路：



代码

```python
class Solution:
    def hammingWeight(self, n: int) -> int:
        print(bin(n)[2:])
        a=0
        for i in bin(n)[2:]:
            a+=int(i)
        return a
```



代码运行截图 <mark>（至少包含有"Accepted"）</mark>

<img width="1376" height="1095" alt="屏幕截图 2026-09-24 155920" src="https://github.com/user-attachments/assets/f393b69f-ed79-45c9-92dd-1071ba79b6c4" />




### LC190: 颠倒二进制位

bit manipulation, Easy, https://leetcode.cn/problems/reverse-bits/

思路：



代码

```python
class Solution:
    def reverseBits(self, n: int) -> int:
        l=[]
        while n>=2:
            m=n%2
            l.append(m)
            n//=2
        l.append(n)
        if len(l)<32:
            l+=[0]*(32-len(l))
        num="".join(map(str,l))
        return int(num,2)<img width="1544" height="1283" alt="屏幕截图 2026-09-24 160034" src="https://github.com/user-attachments/assets/0d9282d9-d1a7-4e54-8f4a-684dca0983a4" />

```



代码运行截图 <mark>（至少包含有"Accepted"）</mark>

<img width="1544" height="1283" alt="屏幕截图 2026-09-24 160034" src="https://github.com/user-attachments/assets/b4d452b9-576a-4c53-857f-0fdeca0f2d1e" />




### LC356: 根据数字二进制下 1 的数目排序


思路：



代码

```python
class Solution:
    def sortByBits(self, arr: list[int]) -> list[int]:
        return sorted(arr,key=lambda x:(bin(x).count("1"),x))
```



代码运行截图 <mark>（至少包含有"Accepted"）</mark>
<img width="1360" height="993" alt="屏幕截图 2026-09-24 160143" src="https://github.com/user-attachments/assets/acd65412-fd3b-4404-8c84-82c106569aaa" />





### LC1404: 将二进制表示减到 1 的步骤数

bit manipulation, Medium, https://leetcode.cn/problems/number-of-steps-to-reduce-a-number-in-binary-representation-to-one/

思路：



代码

```python
class Solution:
    def numSteps(self, s: str) -> int:
        a=int(s,2)
        c=0
        while a!=1:
            if a%2==0:
                a//=2
                c+=1
            else:
                a+=1
                c+=1
        return c
```



代码运行截图 <mark>（至少包含有"Accepted"）</mark>

<img width="2125" height="1249" alt="image" src="https://github.com/user-attachments/assets/c242b545-fe35-4a27-83f9-36e74d4d290c" />





## 2. 学习总结和收获

<mark>如果作业题目简单，有否额外练习题目，比如：OJ“计概2026fall每日选做”、CF、LeetCode、洛谷等网站题目。</mark>



