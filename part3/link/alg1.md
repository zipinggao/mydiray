##题目描述
 给出两个 非空 的链表用来表示两个非负的整数。其中，它们各自的位数是按照 逆序 的方式存储的，并且它们的每个节点只能存储 一位 数字。

如果，我们将这两个数相加起来，则会返回一个新的链表来表示它们的和。

您可以假设除了数字 0 之外，这两个数都不会以 0 开头。

##示例：

输入：(2 -> 4 -> 3) + (5 -> 6 -> 4)
输出：7 -> 0 -> 8
原因：342 + 465 = 807

##题解：
        /**
         * Definition for singly-linked list.
         * public class ListNode {
         *     int val;
         *     ListNode next;
         *     ListNode(int x) { val = x; }
         * }
         */
        class Solution {
            public ListNode addTwoNumbers(ListNode l1, ListNode l2) {
                ListNode temp = new ListNode(0);
                ListNode p = l1 , q = l2, curr = temp;
                int carry = 0;
                while(p != null & q != null){
                    int x = (p!=null) ? p.val:0;
                    int y = (q!=null) ? q.val:0;
                    int num = carry + x + y;
                    carry = num / 10;
                    curr.next = new ListNode(num % 10);
                    curr = curr.next;
                    if(p!=null) p = p.next;
                    if(q!=null) q = q.next;  
                }
                if (carry > 0){
                    curr.next = new ListNode(carry);
                }
                return temp.next;
            }
        }

##复杂度分析：
**时间复杂度：** $$O(\max(m, n))$$，假设 $$m$$和$$n$$ 分别表示 $$l1$$ 和 $$l2$$ 的长度，上面的算法最多重复 $$max(m, n)$$次。

**空间复杂度:** $$O(max(m, n))$$， 新列表的长度最多为 $$max(m,n) + 1$$。