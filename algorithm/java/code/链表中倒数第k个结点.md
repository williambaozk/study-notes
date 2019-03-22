## 总结

> 先设置一个指针循环到第k个，然后再设一个头结点的指针，然后一起开始移动，知道第一个指针为空

## 代码

```java

    public ListNode FindKthToTail(ListNode head,int k) {
        if (head == null) {
            return null;
        }
        ListNode p1=head;
        while (p1 != null && k-- > 0) {
            p1=p1.next;
        }
        if (k > 0) {
            return null;
        }
        ListNode p2=head;
        while (p1 != null) {
            p1=p1.next;
            p2=p2.next;
        }
        return p2;
    }
