# 题目
leetcode：[086-分隔链表](https://leetcode-cn.com/problems/partition-list/)
# 思路
使用哑结点，遍历链表，将值小于x的结点前移链于pre后

```
class Solution {
    public ListNode partition(ListNode head, int x) {
        ListNode newHead = new ListNode(-1);
        //记录链表值小于x的最后一个结点
        ListNode pre = newHead;
        ListNode cur = head;
        //跳过前几个值比x小的结点
        while(cur != null && cur.val < x){
            pre.next = cur;
            pre =  pre.next;
            cur = cur.next;
        }
 
        while(cur != null && cur.next != null){
            ListNode tmp = cur.next;
            //若结点值小于x，链于pre后
            if(tmp.val < x){
                cur.next = tmp.next;
                if(pre == newHead){
                    tmp.next = head;
                }else{
                    tmp.next = pre.next;
                }
                pre.next = tmp;
                pre = pre.next;
            }else{
            //若结点值大于x，则跳过
                cur = cur.next;
            }

        }
        return newHead.next == null ? head : newHead.next;
    }
}
```
# 官方解法
使用两个链表，一个链表保存小于x的结点，一个链表保存大于等于x的结点，最后将两个链表连接在一起

```
class Solution {
    public ListNode partition(ListNode head, int x) {
        ListNode beforeHead = new ListNode(-1);//小链表
        ListNode before = beforeHead;
        ListNode afterHead = new ListNode(-1);//大链表
        ListNode after = afterHead;
        while(head != null){
            if(head.val < x){
                before.next = head;
                before = before.next;
            }else{
                after.next = head;
                after = after.next;
            }
            head = head.next;
        }
        //两个链表连接
        before.next = afterHead.next;
        after.next = null;
        
        return beforeHead.next;
    }
}
```
