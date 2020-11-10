# 题目
leetcode：[082. 删除排序链表中的重复元素 II](https://leetcode-cn.com/problems/remove-duplicates-from-sorted-list-ii/)
# 解法一
设置哑结点

```
  class Solution {
      public ListNode deleteDuplicates(ListNode head) {
          ListNode newHead = new ListNode(-1);
          ListNode pre = newHead;
          ListNode cur = head;
          while(cur != null){
              ListNode tmp = cur.next;
              //若当前结点与下一结点值相等
              if(tmp != null && tmp.val == cur.val){
                  //跳过当前结点直至下一与当前值不相等的结点
                  while(tmp != null && tmp.val == cur.val){
                      tmp = tmp.next;
                  }
                  cur = tmp;
                  pre.next = tmp;
              }else{
                  pre.next = cur;
                  pre = pre.next;
                  cur = cur.next;
              }
          }
          return newHead.next;

      }
  }
```
# 解法二
使用递归
