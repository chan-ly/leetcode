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

```
class Solution {
    public ListNode deleteDuplicates(ListNode head) {
        if(head == null || head.next == null)
            return head;
        if(head.val == head.next.val){
            //如果头节点与头节点的下一节点值相等，跳过所有相等节点。递归调用函数判断最后一个跳过节点的后一节点
            while(head != null && head.next!= null && head.next.val == head.val){
                head = head.next;
            }
            return deleteDuplicates(head.next);           
        }else{
            //如果头节点与头节点的下一节点值不等，递归调用函数判断头节点的后一节点
            head.next = deleteDuplicates(head.next);
            return head;
        }
    }
}
```
