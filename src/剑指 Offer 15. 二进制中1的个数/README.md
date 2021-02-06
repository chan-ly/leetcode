# 题目
leetcode：[剑指 Offer 15. 二进制中1的个数](https://leetcode-cn.com/problems/er-jin-zhi-zhong-1de-ge-shu-lcof/)
# 解题思路
- 涉及二进制的题目可以从位运算和字符串入手
# 解法一
- 循环判断，对n作无符号右移，最后一位跟1与

```
public class Solution {
    public int hammingWeight(int n) {
        int res = 0;
        while(n != 0) {
            res += n & 1;
            n >>>= 1;
        }
        return res;
    }
}
```
# 解法二
- 将n与n-1与，相当于把n最右的1变成0
- 当n不为0时，令n=n&（n-1），消去n中最右边的一个1
- 循环的次数就是消去1的次数，就是n中1的个数

```
public class Solution {
    public int hammingWeight(int n) {
        int res = 0;
        while(n != 0) {
            res++;
            n &= n - 1;
        }
        return res;
    }
}
```
