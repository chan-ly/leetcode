# 题目
leetcode：[142. 环形链表 II](https://leetcode-cn.com/problems/linked-list-cycle-ii/)
# 快慢指针
- 与[141. 环形链表](https://github.com/chan-ly/leetcode/tree/main/src/141-%E7%8E%AF%E5%BD%A2%E9%93%BE%E8%A1%A8)类似
- 快慢指针相遇后，将快指针置于头节点，快慢指针再次相遇则为环起点

```
public class Solution {
    public ListNode detectCycle(ListNode head) {
        ListNode fast = head;
        ListNode slow = head;
        while(fast != null && fast.next != null){
            fast = fast.next.next;
            slow = slow.next;
            if(fast == slow){
                break;
            }           
        }
        if(fast == null || fast.next == null){
            return null;
        }else{
            fast = head;
            while(fast != slow){
                slow = slow.next;
                fast = fast.next;               
            }
            return fast;
        }
    }
}

```
