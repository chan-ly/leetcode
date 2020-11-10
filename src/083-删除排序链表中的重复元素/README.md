# 题目
leetcode：[083 删除排序链表中的重复元素](https://leetcode-cn.com/problems/remove-duplicates-from-sorted-list/)
# 解法
直接解：比较当前结点与它之后的结点的值确定是否为重复结点
```
  class Solution {
      public ListNode deleteDuplicates(ListNode head) {
          ListNode pre = head;
          while(pre != null && pre.next != null){
              ListNode tmp = pre.next;
              while(tmp!= null && tmp.val == pre.val){
                  tmp = tmp.next;
              }
              pre.next = tmp;
              pre = pre.next;
          }
          return head;
      }
  }
```
