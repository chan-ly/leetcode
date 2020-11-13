# 题目
leetcode：[141. 环形链表](https://leetcode-cn.com/problems/linked-list-cycle/)
# 快慢指针
- 快指针：每次走两步
- 慢指针：每次走一步
- 如果有环 快慢指针会相遇

```
public class Solution {
    public boolean hasCycle(ListNode head) {
        ListNode fast = head;
        ListNode slow = head;
        while(fast != null && fast.next != null){
            slow = slow.next;
            fast = fast.next.next;
            if(fast == slow){
                return true;
            }
        }
        return false;
    }
}
```
