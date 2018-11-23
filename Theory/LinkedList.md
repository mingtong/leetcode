#### 单链表数据结构：
```
//Definition for singly-linked list.
public class ListNode 
{
    public int val;
    public ListNode next;
    public ListNode(int x) { val = x; }
}
```

#### 题型：
- 从链表中删除一个结点
- 从链表中插入一个结点
- 反转链表
- 修改链表顺序，使链表中的奇数位排在前，偶数数排在后
- 合并两个有序链表
- 检测链表是否有环
- 删除链表中的倒数第n个结点
- 删除有序链表中的重复元素
- 判断链表是否是回文
- 找到两个链表的交点
- 将链表排序
- 将两个链表对位的结点值相加（从后向前），得到新链表
- 将k个有序链表合并成一个新链表

#### 链表通常要注意的case：
- 链表为空的情况（头结点为空）
- 链表只有1个结点的情况
- 链表只有2个结点的情况
- 要处理的结点是头结点的情况
- 要处理的结点是属结点的情况
- 可以用一个假的头结点(dummy)指向真的头结点，在返回时返回dummy.next