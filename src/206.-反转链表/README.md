# 题目
leetcode：[206. 反转链表](https://leetcode-cn.com/problems/reverse-linked-list/)
# 递归法

```
class Solution {
    public ListNode reverseList(ListNode head) {
        if(head == null)
            return head;
        if(head.next == null) return head;
        ListNode last = reverseList(head.next);
        head.next.next = head;
        head.next = null;
        return last;
    }
}
```
