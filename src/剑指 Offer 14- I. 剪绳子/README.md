# 题目
leetcode：[剑指 Offer 14- I. 剪绳子](https://leetcode-cn.com/problems/jian-sheng-zi-lcof/)
# 解法
- 若切分方法合理，切分的段越多，乘积越大
- 数学推导：所有线段长度相等时乘积最大.最优线段长度为3

```
class Solution {
    public int cuttingRope(int n) {
        int sum = 1;
        if(n <= 3){
            return n - 1;
        }
        
        while(n > 4){
            sum = sum * 3;
            n = n - 3;
        }

        if(n != 0) {
            return sum * n;
        } 
        return sum;
    }
}
```

```
class Solution {
    public int cuttingRope(int n) {
        if(n <= 3) return n - 1;
        int a = n / 3, b = n % 3;
        if(b == 0) return (int)Math.pow(3, a);
        if(b == 1) return (int)Math.pow(3, a - 1) * 4;
        return (int)Math.pow(3, a) * 2;
    }
}
```
