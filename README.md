# stuAlgorithm
算法学习的 PDF （会持续更新）


# CodeTop:

> 频率50+网上的都穷啊一边

## 1.反转链表(**递归**)

>给你单链表的头节点 head ，请你反转链表，并返回反转后的链表。
>
>
>示例 1：
>
>输入：head = [1,2,3,4,5]
>输出：[5,4,3,2,1]
>示例 2：
>
>
>输入：head = [1,2]
>输出：[2,1]
>示例 3：
>
>输入：head = []
>输出：[]

leetcode版本:

````java
class Solution{
    public ListNode rerverseListNode(ListNode head){
		if(head ==null&& head.next == null){
            return head;
        }
        ListNode p = rerverseListNode(head.next);
        head.next.next = head;
        head.next = null;        
    }
    return p;
}
````

```java

```

### 面试(字节跳动):

实现一个大的俩单链表的**减法**:`单链表自己定义自己写`:

```java
//singly-linked list.

//{1,ListNode1} -> {2,ListNode2}

public class ListNode(ListNode node){
    int val;
    ListNode node;
    public ListNode(){}
    public ListNode(int val){
        this.val = val;
    }
    public ListNode(int val,ListNode next){
        this.val = val;
        this.next = next;
    }
}




/**
 * Definition for singly-linked list.
 * public class ListNode {
 *     int val;
 *     ListNode next;
 *     ListNode() {}
 *     ListNode(int val) { this.val = val; }
 *     ListNode(int val, ListNode next) { this.val = val; this.next = next; }
 * }
 */
```





## 2.[无重复字符的最长子串](https://leetcode-cn.com/problems/longest-substring-without-repeating-characters/)

### (**滑动窗口模板**)画图

>给定一个字符串 s ，请你找出其中不含有重复字符的 最长子串 的长度。
>
>示例 1:
>
>输入: s = "abcabcbb"
>输出: 3 
>解释: 因为无重复字符的最长子串是 "abc"，所以其长度为 3。
>示例 2:
>
>输入: s = "bbbbb"
>输出: 1
>解释: 因为无重复字符的最长子串是 "b"，所以其长度为 1。
>示例 3:
>
>输入: s = "pwwkew"
>输出: 3
>解释: 因为无重复字符的最长子串是 "wke"，所以其长度为 3。
>请注意，你的答案必须是 子串 的长度，"pwke" 是一个子序列，不是子串。
>示例 4:
>
>输入: s = ""
>输出: 0

````java
package test;

import com.sun.xml.internal.fastinfoset.tools.XML_SAX_StAX_FI;

import java.io.BufferedReader;
import java.io.IOException;
import java.io.InputStreamReader;
import java.util.HashMap;

/**
 * Created with IntelliJ IDEA.
 *
 * @Author: 张驰
 * @Date: 2021/09/08/14:19
 * @Description: 三尺秋水尘不染
 */


public class Main {
    static int max ,start,left;
    static HashMap<Character,Integer> hashMap = new HashMap<Character,Integer>();

    public static int lengthOfLongestSubstring(String s){
        if (s.length() == 0){
            return 0;
        }
        for (int i = 0;i < s.length(); i++){
            if(hashMap.containsKey(s.charAt(i))){
                left = Math.max(left,hashMap.get(s.charAt(i)));
            }
            hashMap.put(s.charAt(i),i);
            max = Math.max(max,i-left);
        }
        return max;
    }

    public static void main(String[] args) throws IOException {
        BufferedReader bufferedReader = new BufferedReader(new InputStreamReader(System.in));
        String s = bufferedReader.readLine();
        StringBuilder sb = new StringBuilder(s);
        String str1 =  sb.substring(1,s.length()-1);

//        String s1 = bufferedReader.readLine();
//        StringBuilder sb1 = new StringBuilder(s);
//        String str2 =  sb.substring(1,s.length()-1);
        System.out.println(str1);
        System.out.println(lengthOfLongestSubstring(str1));

    }
}

````



## [215. 数组中的第K个最大元素](https://leetcode-cn.com/problems/kth-largest-element-in-an-array/)

### 快排,堆排

难度中等1285

给定整数数组 `nums` 和整数 `k`，请返回数组中第 `**k**` 个最大的元素。

请注意，你需要找的是数组排序后的第 `k` 个最大的元素，而不是第 `k` 个不同的元素。

 

**示例 1:**

```
输入: [3,2,1,5,6,4] 和 k = 2
输出: 5
```

**示例 2:**

```
输入: [3,2,3,1,2,4,5,5,6] 和 k = 4
输出: 4
```

 

````java

````

## [25. K 个一组翻转链表](https://leetcode-cn.com/problems/reverse-nodes-in-k-group/)

### 重点在优化长度直接模拟就好

难度困难1297

给你一个链表，每 *k* 个节点一组进行翻转，请你返回翻转后的链表。

*k* 是一个正整数，它的值小于或等于链表的长度。

如果节点总数不是 *k* 的整数倍，那么请将最后剩余的节点保持原有顺序。

**进阶：**

- 你可以设计一个只使用常数额外空间的算法来解决此问题吗？
- **你不能只是单纯的改变节点内部的值**，而是需要实际进行节点交换。

 

**示例 1：**

![img](https://assets.leetcode.com/uploads/2020/10/03/reverse_ex1.jpg)

```
输入：head = [1,2,3,4,5], k = 2
输出：[2,1,4,3,5]
```

**示例 2：**

![img](https://assets.leetcode.com/uploads/2020/10/03/reverse_ex2.jpg)

```
输入：head = [1,2,3,4,5], k = 3输出：[3,2,1,4,5]
```

**示例 3：**

```
输入：head = [1,2,3,4,5], k = 1输出：[1,2,3,4,5]
```

**示例 4：**

```
输入：head = [1], k = 1输出：[1]
```



**提示：**

- 列表中节点的数量在范围 `sz` 内
- `1 <= sz <= 5000`
- `0 <= Node.val <= 1000`
- `1 <= k <= sz`

````java

````

#### [143. 重排链表](https://leetcode-cn.com/problems/reorder-list/)

难度中等669

给定一个单链表 `L` 的头节点 `head` ，单链表 `L` 表示为：

` L0 → L1 → … → Ln-1 → Ln `
请将其重新排列后变为：

```
L0 → Ln → L1 → Ln-1 → L2 → Ln-2 → …
```

不能只是单纯的改变节点内部的值，而是需要实际的进行节点交换。

 

**示例 1:**

![img](https://pic.leetcode-cn.com/1626420311-PkUiGI-image.png)

```
输入: head = [1,2,3,4]输出: [1,4,2,3]
```

**示例 2:**

![img](https://pic.leetcode-cn.com/1626420320-YUiulT-image.png)

```
输入: head = [1,2,3,4,5]输出: [1,5,2,4,3]
```

```java
//方法1 arraylist  模拟法:/** * Definition for singly-linked list. * public class ListNode { *     int val; *     ListNode next; *     ListNode() {} *     ListNode(int val) { this.val = val; } *     ListNode(int val, ListNode next) { this.val = val; this.next = next; } * } */class Solution {    public void reorderList(ListNode head) {		List<Interger> list =  new ArrayList<>();         ListNode node = head;         while(node != null){             list.add(node);             node = node.next;         }        int left = 0,right = list.size() - 1;		while(left < right){            //最后的加入            list.get(left).next = list.get(right);            //缩小界限            left++;            if(left == right ){                break;            }            // 缩小界限后的加入            list.get(right).next = list.get(left);            right--;        }                list.get(left).next = null;    }}
```

````java
/** * Definition for singly-linked list. * public class ListNode { *     int val; *     ListNode next; *     ListNode() {} *     ListNode(int val) { this.val = val; } *     ListNode(int val, ListNode next) { this.val = val; this.next = next; } * } *///方法2:链表二分在街上:class Solution {   public void reorderList(ListNode head) {    if (head == null || head.next == null || head.next.next == null) {        return;    }    //找中点，链表分成两个    ListNode slow = head;    ListNode fast = head;    while (fast.next != null && fast.next.next != null) {        slow = slow.next;        fast = fast.next.next;    }    ListNode newHead = slow.next;    slow.next = null;        //第二个链表倒置    newHead = reverseList(newHead);        //链表节点依次连接    while (newHead != null) {        ListNode temp = newHead.next;        newHead.next = head.next;        head.next = newHead;        head = newHead.next;        newHead = temp;    }}private ListNode reverseList(ListNode head) {    if (head == null) {        return null;    }    ListNode tail = head;    head = head.next;    tail.next = null;    while (head != null) {        ListNode temp = head.next;        head.next = tail;        tail = head;        head = temp;    }    return tail;}}
````

## [5. 最长回文子串](https://leetcode-cn.com/problems/longest-palindromic-substring/)

难度中等4109

给你一个字符串 `s`，找到 `s` 中最长的回文子串。

 

**示例 1：**

```
输入：s = "babad"输出："bab"解释："aba" 同样是符合题意的答案。
```

**示例 2：**

```
输入：s = "cbbd"输出："bb"
```

**示例 3：**

```
输入：s = "a"输出："a"
```

**示例 4：**

```
输入：s = "ac"输出："a"
```



 ````java
//中心扩散法:public class Solution {    public String longestPalindrome(String s) {	int len = s.length();        if(len < 2){		return s;        }        //长度和下表就是最长的        int maxLen = 1, int start = 0;        char[] array = s.toCharrArray();            }}
 ````

## [15. 三数之和](https://leetcode-cn.com/problems/3sum/)

难度中等3805

给你一个包含 `n` 个整数的数组 `nums`，判断 `nums` 中是否存在三个元素 *a，b，c ，*使得 *a + b + c =* 0 ？请你找出所有和为 `0` 且不重复的三元组。

**注意：**答案中不可以包含重复的三元组。

 

**示例 1：**

```
输入：nums = [-1,0,1,2,-1,-4]输出：[[-1,-1,2],[-1,0,1]]
```

**示例 2：**

```
输入：nums = []输出：[]
```

**示例 3：**

```
输入：nums = [0]输出：[]
```

```java
排序加双指针class Solution {    public List<List<Integer>> threeSum(int[] nums) {  		int length = nums.length;        Arrays.sort(nums);        List<List<Integer>> ans = new ArrayList<>();                //便利        for (int i = 0; i < length; i++) {            //特殊条件这个已经有序了,就不要主元后面的            if(nums[i] > 0){                break;            }            //去重和前一个一样吗???i代表主元pivot其他左右指针都要去重            if(i > 0 && nums[i] == nums[i-1]){                continue;            }            //左右移动指针            //left在pivot后, right是右边界            int left = i+1,right = length-1;            while(left < right){                int sum = nums[i]+ nums[left] +nums[right];                //全部区间大于小于等于                if(sum ==0){                    ans.add(Arrays.asList(nums[i],nums[left],nums[right]));                    //避免重复,策略不同left是忘右走看右边+1                    while (left < right && nums[left] == nums[left+1]) left++;                    //right往左走-1                    while (left < right && nums[right] == nums[right-1]) right--;                    left++;                    right--;                }                else if(sum < 0){ left++;}                else if(sum > 0){ right--;}            }        }            return  ans;}}
```

时间复杂度为o(n^2);

## [141. 环形链表](https://leetcode-cn.com/problems/linked-list-cycle/)

难度简单1214

给定一个链表，判断链表中是否有环。

如果链表中有某个节点，可以通过连续跟踪 `next` 指针再次到达，则链表中存在环。 为了表示给定链表中的环，我们使用整数 `pos` 来表示链表尾连接到链表中的位置（索引从 0 开始）。 如果 `pos` 是 `-1`，则在该链表中没有环。**注意：`pos` 不作为参数进行传递**，仅仅是为了标识链表的实际情况。

如果链表中存在环，则返回 `true` 。 否则，返回 `false` 。

 

**进阶：**

你能用 *O(1)*（即，常量）内存解决此问题吗？

 

**示例 1：**

![img](https://assets.leetcode-cn.com/aliyun-lc-upload/uploads/2018/12/07/circularlinkedlist.png)

```
输入：head = [3,2,0,-4], pos = 1输出：true解释：链表中有一个环，其尾部连接到第二个节点。
```

**示例 2：**

![img](https://assets.leetcode-cn.com/aliyun-lc-upload/uploads/2018/12/07/circularlinkedlist_test2.png)

```
输入：head = [1,2], pos = 0输出：true解释：链表中有一个环，其尾部连接到第一个节点。
```

**示例 3：**

![img](https://assets.leetcode-cn.com/aliyun-lc-upload/uploads/2018/12/07/circularlinkedlist_test3.png)

```
输入：head = [1], pos = -1输出：false解释：链表中没有环。
```

 

![image-20210926153552731](C:\Users\HaRiJi\AppData\Roaming\Typora\typora-user-images\image-20210926153552731.png)



![image-20210926153645926](C:\Users\HaRiJi\AppData\Roaming\Typora\typora-user-images\image-20210926153645926.png)

## [21. 合并两个有序链表](https://leetcode-cn.com/problems/merge-two-sorted-lists/)

难度简单1931

将两个升序链表合并为一个新的 **升序** 链表并返回。新链表是通过拼接给定的两个链表的所有节点组成的。 

 

**示例 1：**

![img](https://assets.leetcode.com/uploads/2020/10/03/merge_ex1.jpg)

```
输入：l1 = [1,2,4], l2 = [1,3,4]输出：[1,1,2,3,4,4]
```

**示例 2：**

```
输入：l1 = [], l2 = []输出：[]
```

**示例 3：**

```
输入：l1 = [], l2 = [0]输出：[0]
```

 ````java
package DiGui;/** * Created with IntelliJ IDEA. * * @Author: 张驰 * @Date: 2021/09/26/16:58 * @Description: 三尺秋水尘不染 */public class mergeTwoLists {        public ListNode mergeTwoLists(ListNode l1, ListNode l2) {            if(l1 == null){                return l2;            }else if(l2 == null){                return l1;            }            if(l1.val < l2.val){                l1.next = mergeTwoLists(l1.next,l2);                return l1;            }else{                l2.next = mergeTwoLists(l1,l2.next);                return l2;            }        }    public static void main(String[] args) {           }    }  class ListNode {      int val;      ListNode next;      ListNode() {}      ListNode(int val) { this.val = val; }      ListNode(int val, ListNode next) { this.val = val; this.next = next; }  }
 ````

## [102. 二叉树的层序遍历](https://leetcode-cn.com/problems/binary-tree-level-order-traversal/)

难度中等1028

给你一个二叉树，请你返回其按 **层序遍历** 得到的节点值。 （即逐层地，从左到右访问所有节点）。

 

**示例：**
二叉树：`[3,9,20,null,null,15,7]`,

```
    3   / \  9  20    /  \   15   7
```

返回其层序遍历结果：

```
[  [3],  [9,20],  [15,7]]
```

````java
package DFSandBFS.TreeNode;import java.util.ArrayList;import java.util.List;/** * Created with IntelliJ IDEA. * * @Author: 张驰 * @Date: 2021/09/26/17:09 * @Description: 三尺秋水尘不染 */public class levelOrder {    //Definition for a binary tree node.    public class TreeNode {        int val;        TreeNode left;        TreeNode right;        TreeNode() {}        TreeNode(int val) { this.val = val; }        TreeNode(int val, TreeNode left, TreeNode right) {            this.val = val;            this.left = left;            this.right = right;        }    }       class Solution {        public List<List<Integer>> levelOrder(TreeNode root) {            //终止条件        if(root == null){            return new ArrayList<List<Integer>>();        }        //结果集        List<List<Integer>> ans = new ArrayList();        //层        int index = 0;        dfs(index,ans,root);        return  ans;        }        public void dfs(int index, List<List<Integer>>ans, TreeNode root){            //终止条件 输出的数组大小要小于 当前索引的大小+1            if(ans.size() < index + 1 ){               ans.add(new ArrayList<Integer>()) ;            }            ans.get(index).add(root.val);            if(!(root.left == null)){                dfs(index+1,ans,root.left);            }            if(root.right != null){                dfs(index+1,ans,root.right);            }        }    }}
````

#### [1162. 地图分析](https://leetcode-cn.com/problems/as-far-from-land-as-possible/)

难度中等218

你现在手里有一份大小为 N x N 的 网格 `grid`，上面的每个 单元格 都用 `0` 和 `1` 标记好了。其中 `0` 代表海洋，`1` 代表陆地，请你找出一个海洋单元格，这个海洋单元格到离它最近的陆地单元格的距离是最大的。

我们这里说的距离是「曼哈顿距离」（ Manhattan Distance）：`(x0, y0)` 和 `(x1, y1)` 这两个单元格之间的距离是 `|x0 - x1| + |y0 - y1|` 。

如果网格上只有陆地或者海洋，请返回 `-1`。

 

**示例 1：**

**![img](https://assets.leetcode-cn.com/aliyun-lc-upload/uploads/2019/08/17/1336_ex1.jpeg)**

```
输入：[[1,0,1],[0,0,0],[1,0,1]]输出：2解释： 海洋单元格 (1, 1) 和所有陆地单元格之间的距离都达到最大，最大距离为 2。
```

**示例 2：**

**![img](https://assets.leetcode-cn.com/aliyun-lc-upload/uploads/2019/08/17/1336_ex2.jpeg)**

```
输入：[[1,0,0],[0,0,0],[0,0,0]]输出：4解释： 海洋单元格 (2, 2) 和所有陆地单元格之间的距离都达到最大，最大距离为 4。
```

 

相信对于Tree的BFS大家都已经轻车熟路了：

**要把root节点先入队，然后再一层一层的无脑遍历就行了。**

对于图的BFS也是一样滴～ 与Tree的BFS区别如下：
1、tree只有1个root，而图可以有多个源点，所以首先**需要把多个源点都入队。**
2、tree是有向的因此不需要标志是否访问过，而对于无向图来说，必须得**标志是否访问过！**
并且为了防止某个节点多次入队，需要在入队之前就将其设置成已访问！

这是一道典型的BFS基础应用，为什么这么说呢？
因为我们只要先把所有的陆地都入队，然后从各个陆地同时开**始一层一层的向海洋扩散**，那么最后扩散到的海洋就是最远的海洋！
并且这个海洋肯定是被离他最近的陆地给扩散到的！
下面是扩散的图示，1表示陆地，0表示海洋。每次扩散的时候会标记相邻的4个位置的海洋：


你可以想象成你从每个陆地上派了很多支船去踏上伟大航道，踏遍所有的海洋。每当船到了新的海洋，就会分裂成4条新的船，向新的未知海洋前进（访问过的海洋就不去了）。如果船到达了某个未访问过的海洋，那他们是第一个到这片海洋的。很明显，这么多船最后访问到的海洋，肯定是离陆地最远的海洋。

二、代码实现

自己跑一下就懂了（靠后缩进的都是便于理解的）

```java
package DFSandBFS.GraphBFS;import java.util.ArrayDeque;import java.util.Arrays;/** * Created with IntelliJ IDEA. * * @Author: 张驰 * @Date: 2021/09/26/20:03 * @Description: 三尺秋水尘不染 *//*你现在手里有一份大小为N x N 的 网格 grid，上面的每个 单元格 都用0和1标记好了。其中0代表海洋，1代表陆地，请你找出一个海洋单元格，这个海洋单元格到离它最近的陆地单元格的距离是最大的。        我们这里说的距离是「曼哈顿距离」（Manhattan Distance）：(x0, y0) 和(x1, y1)这两个单元格之间的距离是|x0 - x1| + |y0 - y1|。        如果网格上只有陆地或者海洋，请返回-1。        示例 1：        输入：[[1,0,1],[0,0,0],[1,0,1]]        输出：2        解释：        海洋单元格 (1, 1) 和所有陆地单元格之间的距离都达到最大，最大距离为 2。        示例 2：        输入：[[1,0,0],[0,0,0],[0,0,0]]        输出：4        解释：        海洋单元格 (2, 2) 和所有陆地单元格之间的距离都达到最大，最大距离为 4。 */public class maxDistance {    public static int maxDistance(int[][] grid) {//                  左   右   下  上        int[] dx = {0,   0,  -1,  1};        int[] dy = {1,  -1,  0,  0};        ArrayDeque<int[]> queue = new ArrayDeque<>();        int m = grid.length, n = grid[0].length ;        // 先把所有的陆地都入队。        for (int i = 0; i < m; i++) {            for (int j = 0; j < n; j++) {             if(grid[i][j] == 1){                 //拷贝防止丢失                 queue.offer(new int[] {i,j});             }            }        }        // 从各个陆地开始，一圈一圈的遍历海洋，最后遍历到的海洋就是离陆地最远的海洋。        boolean hasOcean = false;        int[] point = null;        while(!queue.isEmpty()){            point = queue.poll();            int x = point[0];            int y = point[1];                                                        System.out.println("出队元素为：X="+x+"Y="+y);  System.out.println();            //上下左右便利  （扩散）            for (int i = 0; i < 4; i++) {                                                        System.out.println("扩散中:....");                                                        System.out.println("0,1,2,3对应左   右   下  上");                                                        System.out.println("第"+i+"次");                                                        System.out.println();               int newX = x + dx[i];               int newY = y + dy[i];               //边界情况 (越界或者  里面不是海洋）                if(newX < 0 || newX >= m || newY < 0|| newY >= n || grid[newX][newY] != 0){                    continue;                }                grid[newX][newY] = grid[x][y] + 1;                hasOcean = true;                queue.offer(new int[] {newX,newY});                                                            System.out.println("如对元素为:"+newX+"和"+newY);                                                            System.out.println("第 "+i+"次操作原数组为");                                                            for (int[] data:grid                                                                 ) {                                                                System.out.println(Arrays.toString(data));                                                            }                                                            System.out.println();                }            }    if(point == null || !hasOcean){        return  -1;    }        System.out.println("队列中现在还有");        System.out.println(point[0]+""+point[1]);    return grid[point[0]][point[1]] - 1;    }    public static void main(String[] args) {        int[][] grid = {{1,0,1},                        {0,0,0},                        {1,0,1}};        System.out.println(maxDistance(grid));    }}
```










# fucking -算法

# 树部分:

## 1.根据前序遍历和中序遍历的结果还原一棵二叉树

````java
class Solution {    private Map<Integer, Integer> indexMap;    public TreeNode myBuildTree(int[] preorder, int[] inorder, int preorder_left, int preorder_right, int inorder_left, int inorder_right) {        if (preorder_left > preorder_right) {            return null;        }        // 前序遍历中的第一个节点就是根节点        int preorder_root = preorder_left;        // 在中序遍历中定位根节点        int inorder_root = indexMap.get(preorder[preorder_root]);                // 先把根节点建立出来        TreeNode root = new TreeNode(preorder[preorder_root]);        // 得到左子树中的节点数目        int size_left_subtree = inorder_root - inorder_left;        // 递归地构造左子树，并连接到根节点        // 先序遍历中「从 左边界+1 开始的 size_left_subtree」个元素就对应了中序遍历中「从 左边界 开始到 根节点定位-1」的元素        root.left = myBuildTree(preorder, inorder, preorder_left + 1, preorder_left + size_left_subtree, inorder_left, inorder_root - 1);        // 递归地构造右子树，并连接到根节点        // 先序遍历中「从 左边界+1+左子树节点数目 开始到 右边界」的元素就对应了中序遍历中「从 根节点定位+1 到 右边界」的元素        root.right = myBuildTree(preorder, inorder, preorder_left + size_left_subtree + 1, preorder_right, inorder_root + 1, inorder_right);        return root;    }    public TreeNode buildTree(int[] preorder, int[] inorder) {        int n = preorder.length;        // 构造哈希映射，帮助我们快速定位根节点        indexMap = new HashMap<Integer, Integer>();        for (int i = 0; i < n; i++) {            indexMap.put(inorder[i], i);        }        return myBuildTree(preorder, inorder, 0, n - 1, 0, n - 1);    }}
````



## 2.LeetCode 124 题，难度 Hard，让你求二叉树中最大路径和:

````java
class Solution {    int maxSum = Integer.MIN_VALUE;    public int maxPathSum(TreeNode root) {        maxGain(root);        return maxSum;    }    public int maxGain(TreeNode node) {        if (node == null) {            return 0;        }                // 递归计算左右子节点的最大贡献值        // 只有在最大贡献值大于 0 时，才会选取对应子节点        int leftGain = Math.max(maxGain(node.left), 0);        int rightGain = Math.max(maxGain(node.right), 0);        // 节点的最大路径和取决于该节点的值与该节点的左右子节点的最大贡献值        int priceNewpath = node.val + leftGain + rightGain;        // 更新答案        maxSum = Math.max(maxSum, priceNewpath);        // 返回节点的最大贡献值        return node.val + Math.max(leftGain, rightGain);    }}
````

## 修改BTS使之有序:

````java
class Solution {    public void recoverTree(TreeNode root) {        List<Integer> nums = new ArrayList<Integer>();        inorder(root, nums);        int[] swapped = findTwoSwapped(nums);        recover(root, 2, swapped[0], swapped[1]);    }    public void inorder(TreeNode root, List<Integer> nums) {        if (root == null) {            return;        }        inorder(root.left, nums);        nums.add(root.val);        inorder(root.right, nums);    }    public int[] findTwoSwapped(List<Integer> nums) {        int n = nums.size();        int index1 = -1, index2 = -1;        for (int i = 0; i < n - 1; ++i) {            if (nums.get(i + 1) < nums.get(i)) {                index2 = i + 1;                if (index1 == -1) {                    index1 = i;                } else {                    break;                }            }        }        int x = nums.get(index1), y = nums.get(index2);        return new int[]{x, y};    }    public void recover(TreeNode root, int count, int x, int y) {        if (root != null) {            if (root.val == x || root.val == y) {                root.val = root.val == x ? y : x;                if (--count == 0) {                    return;                }            }            recover(root.right, count, x, y);            recover(root.left, count, x, y);        }    }}作者：LeetCode-Solution链接：https://leetcode-cn.com/problems/recover-binary-search-tree/solution/hui-fu-er-cha-sou-suo-shu-by-leetcode-solution/来源：力扣（LeetCode）著作权归作者所有。商业转载请联系作者获得授权，非商业转载请注明出处。
````

方法二:

````java
class Solution {    public void recoverTree(TreeNode root) {        Deque<TreeNode> stack = new ArrayDeque<TreeNode>();        TreeNode x = null, y = null, pred = null;        while (!stack.isEmpty() || root != null) {            while (root != null) {                stack.push(root);                root = root.left;            }            root = stack.pop();            if (pred != null && root.val < pred.val) {                y = root;                if (x == null) {                    x = pred;                } else {                    break;                }            }            pred = root;            root = root.right;        }        swap(x, y);    }    public void swap(TreeNode x, TreeNode y) {        int tmp = x.val;        x.val = y.val;        y.val = tmp;    }}作者：LeetCode-Solution链接：https://leetcode-cn.com/problems/recover-binary-search-tree/solution/hui-fu-er-cha-sou-suo-shu-by-leetcode-solution/来源：力扣（LeetCode）著作权归作者所有。商业转载请联系作者获得授权，非商业转载请注明出处。
````

方法3:

````java
class Solution {    public void recoverTree(TreeNode root) {        TreeNode x = null, y = null, pred = null, predecessor = null;        while (root != null) {            if (root.left != null) {                // predecessor 节点就是当前 root 节点向左走一步，然后一直向右走至无法走为止                predecessor = root.left;                while (predecessor.right != null && predecessor.right != root) {                    predecessor = predecessor.right;                }                                // 让 predecessor 的右指针指向 root，继续遍历左子树                if (predecessor.right == null) {                    predecessor.right = root;                    root = root.left;                }                // 说明左子树已经访问完了，我们需要断开链接                else {                    if (pred != null && root.val < pred.val) {                        y = root;                        if (x == null) {                            x = pred;                        }                    }                    pred = root;                    predecessor.right = null;                    root = root.right;                }            }            // 如果没有左孩子，则直接访问右孩子            else {                if (pred != null && root.val < pred.val) {                    y = root;                    if (x == null) {                        x = pred;                    }                }                pred = root;                root = root.right;            }        }        swap(x, y);    }    public void swap(TreeNode x, TreeNode y) {        int tmp = x.val;        x.val = y.val;        y.val = tmp;    }}作者：LeetCode-Solution链接：https://leetcode-cn.com/problems/recover-binary-search-tree/solution/hui-fu-er-cha-sou-suo-shu-by-leetcode-solution/来源：力扣（LeetCode）著作权归作者所有。商业转载请联系作者获得授权，非商业转载请注明出处。
````

## 二叉树的便利：

### [199. 二叉树的右视图](https://leetcode-cn.com/problems/binary-tree-right-side-view/)

难度中等542

给定一个二叉树的 **根节点** `root`，想象自己站在它的右侧，按照从顶部到底部的顺序，返回从右侧所能看到的节点值。

 

**示例 1:**

![img](https://assets.leetcode.com/uploads/2021/02/14/tree.jpg)

```
输入: [1,2,3,null,5,null,4]输出: [1,3,4]
```

**示例 2:**

```
输入: [1,null,3]输出: [1,3]
```

**示例 3:**

```
输入: []输出: []
```

```java
/** * Definition for a binary tree node. * public class TreeNode { *     int val; *     TreeNode left; *     TreeNode right; *     TreeNode() {} *     TreeNode(int val) { this.val = val; } *     TreeNode(int val, TreeNode left, TreeNode right) { *         this.val = val; *         this.left = left; *         this.right = right; *     } * } */class Solution {    List<Integer> ans = new ArrayList<>();    public List<Integer> rightSideView(TreeNode root) {        int index = 0;        dfs(root,index);        return ans;    }        public void dfs(TreeNode root,int index){        //条件        if(root == null){            return;        }        //添加ans动态的        if(index == ans.size()){            ans.add(root.val);        }        index += 1;        dfs(root.right,index);        dfs(root.left,index);    }}
```

## 层序遍历：

方法1：dfs（）

```java
package DFSandBFS.TreeNode;import java.util.ArrayList;import java.util.List;/** * Created with IntelliJ IDEA. * * @Author: 张驰 * @Date: 2021/09/26/17:09 * @Description: 三尺秋水尘不染 *///二叉树的层序便利public class levelOrder {    //Definition for a binary tree node.    public class TreeNode {        int val;        TreeNode left;        TreeNode right;        TreeNode() {}        TreeNode(int val) { this.val = val; }        TreeNode(int val, TreeNode left, TreeNode right) {            this.val = val;            this.left = left;            this.right = right;        }    }    class Solution {        public List<List<Integer>> levelOrder(TreeNode root) {            //终止条件        if(root == null){            return new ArrayList<List<Integer>>();        }        //结果集        List<List<Integer>> ans = new ArrayList();        //层        int index = 0;        dfs(index,ans,root);        return  ans;        }        /*         * @Method: dfs         * @Description: 三尺秋水尘不染         *  * @param index         * @param ans         * @param root         * @paramType:         [int, java.util.List<java.util.List<java.lang.Integer>>, DFSandBFS.TreeNode.levelOrder.TreeNode]         * @return：void         * @Author: HaRiJi         * @Date: 2021/9/26         */        public void dfs(int index, List<List<Integer>>ans, TreeNode root){            //终止条件 输出的数组大小要小于 当前索引的大小+1            if(ans.size() < index + 1 ){               ans.add(new ArrayList<Integer>()) ;            }            //第零层的更节电直接加入            ans.get(index).add(root.val);            if(!(root.left == null)){                dfs(index+1,ans,root.left);            }            if(root.right != null){                dfs(index+1,ans,root.right);            }        }    }}
```

方法二:bfs(借助队列实现)

```java
package DFSandBFS.TreeNode;import java.util.ArrayDeque;import java.util.ArrayList;import java.util.Deque;import java.util.List;//  Created with IntelliJ IDEA.////  @Author: 张驰//  @Date: 2021/09/27/9:15//  @Description: 三尺秋水尘不染// //*给定一棵二叉树的根节点root ，请找出该二叉树中每一层的最大值。        示例1：        输入: root = [1,3,2,5,3,null,9]        输出: [1,3,9]        解释:        1        / \        3   2        / \   \        5   3   9        示例2：        输入: root = [1,2,3]        输出: [1,3]        解释:        1        / \        2   3        示例3：        输入: root = [1]        输出: [1]        示例4：        输入: root = [1,null,2]        输出: [1,2]        解释:                  1                   \                    2        示例5：        输入: root = []        输出: [] */public class largestValues {        // Definition for a binary tree node.      public class TreeNode {          int val;          TreeNode left;          TreeNode right;          TreeNode() {}          TreeNode(int val) { this.val = val; }          TreeNode(int val, TreeNode left, TreeNode right) {              this.val = val;              this.left = left;              this.right = right;          }      }         class Solution{        public List<Integer> largestValues(TreeNode root) {            //需要打印结果            List<Integer> ans = new ArrayList<>();            if(root == null){                return new ArrayList<>();            }            //队列是为了  添加  Tree Node            ArrayDeque<TreeNode> deque = new ArrayDeque<>();            //将根节点加入deque            deque.offer(root);            int index = 0;            while(!deque.isEmpty()){                //size  为  当前的动态队列的大小                int size = deque.size();                //维护 最大值  在每次遍历的时候                int max = Integer.MIN_VALUE;                for (int i = 0; i < size; i++) {                    TreeNode node = deque.poll();                    max = Math.max(max, node.val);                    //添加下一层的节点                    if( node.left != null){                        deque.offer(node.left);                    }                    if(node.right != null){                        deque.offer(node.right);                    }                }                ans.add(max);            }            return  ans;        }    }    }
```

#### [103. 二叉树的锯齿形层序遍历](https://leetcode-cn.com/problems/binary-tree-zigzag-level-order-traversal/)

难度中等526

给定一个二叉树，返回其节点值的锯齿形层序遍历。（即先从左往右，再从右往左进行下一层遍历，以此类推，层与层之间交替进行）。

例如：
给定二叉树 `[3,9,20,null,null,15,7]`,

```
    3   / \  9  20    /  \   15   7
```

返回锯齿形层序遍历如下：

```
[  [3],  [20,9],  [15,7]]
```

shhi用方法二:

````java
/** * Definition for a binary tree node. * public class TreeNode { *     int val; *     TreeNode left; *     TreeNode right; *     TreeNode() {} *     TreeNode(int val) { this.val = val; } *     TreeNode(int val, TreeNode left, TreeNode right) { *         this.val = val; *         this.left = left; *         this.right = right; *     } * } */class Solution {    public List<List<Integer>> zigzagLevelOrder(TreeNode root) {        LinkedList<List<Integer>> result = new LinkedList<>();        if (root == null) {            return result;        }                Queue<TreeNode> q = new LinkedList<>();        q.offer(root);                // 开始层序遍历        while (!q.isEmpty()) {            int sz = q.size();            LinkedList<Integer> level = new LinkedList<>();  // 存储每一层的数据            // 遍历每一层中的元素            for (int i = 0; i < sz; i++) {                                                                                TreeNode cur = q.poll();                                                                                if (result.size() % 2 == 0) {                    level.addLast(cur.val);                } else {                    level.addFirst(cur.val);                }                // 添加下一层的元素                if (cur.left != null) {                    q.offer(cur.left);                }                if (cur.right != null) {                    q.offer(cur.right);                }            }            // 将每一层添加到结果变量中            result.addLast(level);        }        return result;    }}
````





# DP:

#### [72. 编辑距离](https://leetcode-cn.com/problems/edit-distance/)

难度困难1826

给你两个单词 `word1` 和 `word2`，请你计算出将 `word1` 转换成 `word2` 所使用的最少操作数 。

你可以对一个单词进行如下三种操作：

- 插入一个字符
- 删除一个字符
- 替换一个字符

 

**示例 1：**

```
输入：word1 = "horse", word2 = "ros"输出：3解释：horse -> rorse (将 'h' 替换为 'r')rorse -> rose (删除 'r')rose -> ros (删除 'e')
```

**示例 2：**

```
输入：word1 = "intention", word2 = "execution"输出：5解释：intention -> inention (删除 't')inention -> enention (将 'i' 替换为 'e')enention -> exention (将 'n' 替换为 'x')exention -> exection (将 'n' 替换为 'c')exection -> execution (插入 'u')
```

 ````java

 ````

#### [53. 最大子序和](https://leetcode-cn.com/problems/maximum-subarray/)

难度简单3760

给定一个整数数组 `nums` ，找到一个具有最大和的连续子数组（子数组最少包含一个元素），返回其最大和。

 

**示例 1：**

```
输入：nums = [-2,1,-3,4,-1,2,1,-5,4]输出：6解释：连续子数组 [4,-1,2,1] 的和最大，为 6 。
```

**示例 2：**

```
输入：nums = [1]输出：1
```

**示例 3：**

```
输入：nums = [0]输出：0
```

**示例 4：**

```
输入：nums = [-1]输出：-1
```

**示例 5：**

```
输入：nums = [-100000]输出：-100000
```

```java
class Solution {    public int maxSubArray(int[] nums) {        int ans = nums[0], sum = 0;        for(int i : nums){            if(sum > 0){                sum+=i;            }else{                sum = i;            }            //判断最大            ans = Math.max(sum,ans);        }        return ans;    }}
```

![image-20210926154555418](C:\Users\HaRiJi\AppData\Roaming\Typora\typora-user-images\image-20210926154555418.png)







# **BFS**

适合找最短,数据结构就是个**数组**就可以了或者**列表****链表**

我觉得就是**dfs(比较优秀**,主要是对于结构做判断的剪枝台费脑子了)(递归yyds>?)

我不要你觉得我要我觉得

?/??/???(等差问号疑惑)

### 模板

````java
啦啦啦啦啦啦lalalal
````

````python
for 选择 in 选择列表:    # 做选择    将该选择从选择列表移除    路径.add(选择)    backtrack(路径, 选择列表)    # 撤销选择    路径.remove(选择)    将该选择再加入选择列表
````

````go

````

重复的

````java
1方法:排序    Arrays.sort(传入的);2方法: //一样的话写一样的条件            if((i > 0&& nums[i] == nums[i-1]) || nums[i] == 100){                //走就完事不影响                continue;
````



















>[40. 组合总和 II](https://leetcode-cn.com/problems/combination-sum-ii/)

> [46. 全排列](https://leetcode-cn.com/problems/permutations/)

> [47. 全排列 II](https://leetcode-cn.com/problems/permutations-ii/)

> [77.组合](https://leetcode-cn.com/problems/combinations)

> [78. 子集](https://leetcode-cn.com/problems/subsets/)

> [90. 子集 II](https://leetcode-cn.com/problems/subsets-ii/)



### [46. 全排列](https://leetcode-cn.com/problems/permutations/)

难度中等1554

给定一个不含重复数字的数组 `nums` ，返回其 **所有可能的全排列** 。你可以 **按任意顺序** 返回答案。

 

**示例 1：**

```
输入：nums = [1,2,3]输出：[[1,2,3],[1,3,2],[2,1,3],[2,3,1],[3,1,2],[3,2,1]]
```

**示例 2：**

```
输入：nums = [0,1]输出：[[0,1],[1,0]]
```

**示例 3：**

```
输入：nums = [1]输出：[[1]]
```

 

````java
class Solution{    public List<List<Integer>> permute (int[] nums){//1.保存结果        List<List<Integer>> res = new ArrayList<>();        List<Integer> output = new ArrayList<>();        //将输入保留在output        for(int num : nums){            output.add(num);        }        int n = nums.length;        //参数解读:有              //长度   输入数组,   结果结合  起始位置        backtrack(n,   output,   res,    0);        return res;            }    public void backtrack(int n,List<Integer> output, List<List<Integer>> res,int first){        //首先终止条件        if( first == n){		res.add(new ArratList<Integer>(output));        }        for(int i = first; i < n; i++){            Collections.swap(output, first, i);            backtrack(n, output,res,first + 1);            Collections.swap(output,first,i);        }    }        }
````

## (重复的):

## [47. 全排列 II](https://leetcode-cn.com/problems/permutations-ii/)

难度中等805

给定一个可包含重复数字的序列 `nums` ，**按任意顺序** 返回所有不重复的全排列。

 

**示例 1：**

```
输入：nums = [1,1,2]输出：[[1,1,2], [1,2,1], [2,1,1]]
```

**示例 2：**

```
输入：nums = [1,2,3]输出：[[1,2,3],[1,3,2],[2,1,3],[2,3,1],[3,1,2],[3,2,1]]
```

 **奇淫技巧:**(适用于三位数多了gg)

```java
class Solution{    public List<List<Integer>> permuteUnique(int[] nums){//排序使其有序帮助后续连续看看一样吗会不会重复        Arrays.sort(nums);        //lists作为结果保存         List<List<Integer>> Lists = new ArrayList<>();        //调用dfs;(什么都可以dfs什么都可以???)        dfs(lists , new ArrayList<>(),nums,0);        //返回结果集合        return lists;    }    //有什么参数放就行    private void dfs(List<List<Integer>> lists, List<Integer> list, int[] nums, int index){        //递归条件为索引到了最后	if(index == nums.length){        //拷贝一份list放入lists;        lists.add(new ArrayList<>(list));        return;    }        for(int i = 0;i < nums.length; i++){            //一样的话            if((i > 0&& nums[i] == nums[i-1]) || nums[i] == 100){                //走就完事不影响                continue;            }else{                int temp = nums[i];                list.add(temp);                                //省略了标记数组这里是适合三位的奇淫技巧                nums[i] = 100;                                                                dfs(lists,list,nums,index + 1);                nums[i] = temp;                list.remove(list.size() - 1);            }        }    }}
```

**套路版**

```java
class Solution {    //标记    boolean[] vis;    public List<List<Integer>> permuteUnique(int[] nums) {        //结果集合        List<List<Integer>> ans = new ArrayList<List<Integer>>();        //输入结合        List<Integer> perm = new ArrayList<Integer>();        vis = new boolean[nums.length];        Arrays.sort(nums);        backtrack(nums, ans, 0, perm);        return ans;    }    public void backtrack(int[] nums, List<List<Integer>> ans, int idx, List<Integer> perm) {        if (idx == nums.length) {            ans.add(new ArrayList<Integer>(perm));            return;        }        for (int i = 0; i < nums.length; ++i) {            //最后是核心代码            //个人理解为 :            //判断前一个 是否被用过  用过标记为true  最后回溯标记为false 取反              if (vis[i] || (i > 0 && nums[i] == nums[i - 1] && !vis[i - 1]))            //等价替换为                //if(prem == nums[i] || visited[i]) //如果当前下标已经加入了路径 或 本次选择的值和前一次相同，那么就再选择一个值                continue;            {                continue;            }            perm.add(nums[i]);            vis[i] = true;            backtrack(nums, ans, idx + 1, perm);            vis[i] = false;            perm.remove(idx);        }    }}
```

## [39. 组合总和](https://leetcode-cn.com/problems/combination-sum/)

难度中等1546收藏分享切换为英文接收动态反馈

给定一个**无重复元素**的正整数数组 `candidates` 和一个正整数 `target` ，找出 `candidates` 中所有可以使数字和为目标数 `target` 的唯一组合。

`candidates` 中的数字可以无限制重复被选取。如果至少一个所选数字数量不同，则两种组合是唯一的。 

对于给定的输入，保证和为 `target` 的唯一组合数少于 `150` 个。

 

**示例 1：**

```
输入: candidates = [2,3,6,7], target = 7输出: [[7],[2,2,3]]
```

**示例 2：**

```
输入: candidates = [2,3,5], target = 8输出: [[2,2,2,2],[2,3,3],[3,5]]
```

**示例 3：**

```
输入: candidates = [2], target = 1输出: []
```

````java
class Solution {    public List<List<Integer>> combinationSum(int[] candidates, int target) {        //1        List<List<Integer>> ans = new ArrayList<List<Integer>>();        //2        List<Integer> combine = new ArrayList<Integer>();        //3        dfs(candidates, target, ans, combine, 0);        //4        return ans;    }    //dfs    public void dfs(int[] candidates, int target, List<List<Integer>> ans, List<Integer> combine, int idx) {        //终止        if (idx == candidates.length) {            return;        }        if (target == 0) {            ans.add(new ArrayList<Integer>(combine));            return;        }        // 直接跳过        dfs(candidates, target, ans, combine, idx + 1);        // 选择当前数        if (target - candidates[idx] >= 0) {            //加进来            combine.add(candidates[idx]);            //递归            dfs(candidates, target - candidates[idx], ans, combine, idx);            //禽畜            combine.remove(combine.size() - 1);        }    }}
````

### (**重复的**)****

## [40. 组合总和 II](https://leetcode-cn.com/problems/combination-sum-ii/)

难度中等689收藏分享切换为英文接收动态反馈

给定一个数组 `candidates` 和一个目标数 `target` ，找出 `candidates` 中所有可以使数字和为 `target` 的组合。

`candidates` 中的每个数字在每个组合中只能使用一次。

**注意：**解集不能包含重复的组合。 

 

**示例 1:**

```
输入: candidates = [10,1,2,7,6,1,5], target = 8,输出:[[1,1,6],[1,2,5],[1,7],[2,6]]
```

**示例 2:**

```
输入: candidates = [2,5,2,1,2], target = 5,输出:[[1,2,2],[5]]
```

````java
class Solution {//    List<List<Integer>> ans = new List<List<Integer>>();       List<List<Integer>> ans = new ArrayList<List<Integer>>();//    List<int[]> freq = new List<int[]>();       List<int[]> freq = new ArrayList<int[]>();           List<Integer> seq = new ArrayList<Integer>();//    List<Integer> seq = new List<Integer>();    public List<List<Integer>> combinationSum2(int[] candidates, int target) {        //乱序必须先排序        Arrays.sort(candidates);        for(int i : candidates){            int size = freq.size();            if(freq.isEmpty() || i != freq.get(size-1)[0]){                freq.add(new int[] {i,1});            }            else{                ++freq.get(size-1)[1];            }        }        dfs(0,target);        return ans;    }    public void dfs(int pos,int rest){        //递归条件        if(rest == 0){          ans.add(new ArrayList<Integer>(seq));            return;        }        if(pos == freq.size() ||rest < freq.get(pos)[0]){            return;        }        dfs(pos+1,rest);        int most = Math.min(rest/freq.get(pos)[0],freq.get(pos)[1]);                for(int i = 1;i < most; i++){            seq.add(freq.get(pos)[0]);            dfs(pos + 1, rest - 1 *freq.get(pos)[0]);                 }            for (int i = 1; i < most; i++) {            seq.remove(seq.size() - 1);        }    }      }
````

[77. 组合](https://leetcode-cn.com/problems/combinations/)

难度中等713收藏分享切换为英文接收动态反馈

给定两个整数 `n` 和 `k`，返回范围 `[1, n]` 中所有可能的 `k` 个数的组合。

你可以按 **任何顺序** 返回答案。

 

**示例 1：**

```
输入：n = 4, k = 2输出：[  [2,4],  [3,4],  [2,3],  [1,2],  [1,3],  [1,4],]
```

**示例 2：**

```
输入：n = 1, k = 1输出：[[1]]
```

 ````java

 ````



多种方法任您

最简单的:

1.画图法:

![image-20210920144654374](C:\Users\HaRiJi\AppData\Roaming\Typora\typora-user-images\image-20210920144654374.png)

奇淫技巧:(三个的所以深度为3)

````java
class Solution {    private List<List<Integer>> ans = new ArrayList<>();    public List<List<Integer>> combine(int n, int k) {        getCombine(n, k, 1, new ArrayList<>());        return ans;    }        public void getCombine(int n, int k, int start, List<Integer> list) {        if(k == 0) {            ans.add(new ArrayList<>(list));            return;        }        for(int i = start;i <= n - k + 1;i++) {            list.add(i);            getCombine(n, k - 1, i+1, list);            list.remove(list.size() - 1);        }    }}
````

正常解法:(太熟了都要背下来了)

````java
import java.util.ArrayDeque;import java.util.ArrayList;import java.util.Deque;import java.util.List;public class Solution {    public List<List<Integer>> combine(int n, int k) {        //1.结果集        List<List<Integer>> res = new ArrayList<>();        //2.传入的放进来(路径集合)        Deque<Integer> path = new ArrayDeque<>();        //3.边界情况        if (k <= 0 || n < k) {            return res;        }        // 从 1 开始是题目的设定        //调用dfs        dfs(n, k, 1, path, res);        //返回结果集合        return res;    }    private void dfs(int n, int k, int begin, Deque<Integer> path, List<List<Integer>> res) {        // 递归终止条件是：path 的长度等于 k        if (path.size() == k) {            res.add(new ArrayList<>(path));            return;        }//三部曲有什么好说的????        // 遍历可能的搜索起点        for (int i = begin; i <= n; i++) {            // 向路径变量里添加一个数            path.addLast(i);            // 下一轮搜索，设置的搜索起点要加 1，因为组合数理不允许出现重复的元素            dfs(n, k, i + 1, path, res);            // 重点理解这里：深度优先遍历有回头的过程，因此递归之前做了什么，递归之后需要做相同操作的逆向操作            path.removeLast();        }    }}
````

#### 要考虑的优化情况:

>优化：分析搜索起点的上界进行剪枝
>我们上面的代码，搜索起点遍历到 n，即：递归函数中有下面的代码片段：

````java
// 从当前搜索起点 begin 遍历到 nfor (int i = begin; i <= n; i++) {    path.addLast(i);    dfs(n, k, i + 1, path, res);    path.removeLast();}
````





> 事实上，如果 n = 7, k = 4，从 55 开始搜索就已经没有意义了，这是因为：即使把 55 选上，后面的数只有 66 和 77，一共就 33 个候选数，凑不出 44 个数的组合。因此，搜索起点有上界，这个上界是多少，可以举几个例子分析。

> 分析搜索起点的上界，其实是在深度优先遍历的过程中剪枝，剪枝可以避免不必要的遍历，剪枝剪得好，可以大幅度节约算法的执行时间。

> 下面的图片绿色部分是剪掉的枝叶，当 n 很大的时候，能少遍历很多结点，节约了时间。

<img src="C:\Users\HaRiJi\AppData\Roaming\Typora\typora-user-images\image-20210920145542443.png" alt="image-20210920145542443" style="zoom:200%;" />



> 容易知道：搜索起点和当前还需要选几个数有关，而当前还需要选几个数与已经选了几个数有关，即与 path 的长度相关。我们举几个例子分析：

> 例如：n = 6 ，k = 4。

> **path.size() == 1** 的时候，接下来要选择 33 个数，搜索起点最大是 44，最后一个被选的组合是 [4, 5, 6]；
> **path.size() == 2** 的时候，接下来要选择 22 个数，搜索起点最大是 55，最后一个被选的组合是 [5, 6]；
> **path.size() == 3** 的时候，接下来要选择 11 个数，搜索起点最大是 66，最后一个被选的组合是 [6]；

> 再如：n = 15 ，k = 4。
> **path.size() == 1** 的时候，接下来要选择 33 个数，搜索起点最大是 1313，最后一个被选的是 [13, 14, 15]；
> **path.size() == 2** 的时候，接下来要选择 22 个数，搜索起点最大是 1414，最后一个被选的是 [14, 15]；
> **path.size() == 3** 的时候，接下来要选择 11 个数，搜索起点最大是 1515，最后一个被选的是 [15]；

> 可以归纳出：

> 搜索起点的上界 + 接下来要选择的元素个数 - 1 = n
> 其中，接下来要选择的元素个数 = k - path.size()，整理得到：

> 搜索起点的上界 = n - (k - path.size()) + 1
> 所以，我们的剪枝过程就是：把 i <= n 改成 i <= n - (k - path.size()) + 1 ：

## [78. 子集](https://leetcode-cn.com/problems/subsets/)

难度中等1326收藏分享切换为英文接收动态反馈

给你一个整数数组 `nums` ，数组中的元素 **互不相同** 。返回该数组所有可能的子集（幂集）。

解集 **不能** 包含重复的子集。你可以按 **任意顺序** 返回解集。

 

**示例 1：**

```
输入：nums = [1,2,3]输出：[[],[1],[2],[1,2],[3],[1,3],[2,3],[1,2,3]]
```

**示例 2：**

```
输入：nums = [0]输出：[[],[0]]
```





````java
//太熟了class Solution {       public List<List<Integer>> subsets(int[] nums) {         List<Integer> t = new ArrayList<Integer>();    List<List<Integer>> ans = new ArrayList<List<Integer>>();        dfs(0, nums,t,ans);        return ans;    }    public void dfs(int cur, int[] nums, List<Integer> t,List<List<Integer>> ans) {        if (cur == nums.length) {            ans.add(new ArrayList<Integer>(t));            return;        }        t.add(nums[cur]);        dfs(cur + 1, nums,t,ans);        t.remove(t.size() - 1);        dfs(cur + 1, nums,t,ans);    }}
````

![image-20210920151146498](C:\Users\HaRiJi\AppData\Roaming\Typora\typora-user-images\image-20210920151146498.png)

### **(重复)**

### [90. 子集 II](https://leetcode-cn.com/problems/subsets-ii/)

难度中等652收藏分享切换为英文接收动态反馈

给你一个整数数组 `nums` ，其中可能包含重复元素，请你返回该数组所有可能的子集（幂集）。

解集 **不能** 包含重复的子集。返回的解集中，子集可以按 **任意顺序** 排列。

 

**示例 1：**

```
输入：nums = [1,2,2]输出：[[],[1],[1,2],[1,2,2],[2],[2,2]]
```

**示例 2：**

```
输入：nums = [0]输出：[[],[0]]
```



````java
class Solution {    List<Integer> t = new ArrayList<Integer>();    List<List<Integer>> ans = new ArrayList<List<Integer>>();    public List<List<Integer>> subsetsWithDup(int[] nums) {        Arrays.sort(nums);        dfs(false, 0, nums);        return ans;    }    public void dfs(boolean choosePre, int cur, int[] nums) {        if (cur == nums.length) {            ans.add(new ArrayList<Integer>(t));            return;        }        dfs(false, cur + 1, nums);        if (!choosePre && cur > 0 && nums[cur - 1] == nums[cur]) {            return;        }        t.add(nums[cur]);        dfs(true, cur + 1, nums);        t.remove(t.size() - 1);    }}作者：LeetCode-Solution链接：https://leetcode-cn.com/problems/subsets-ii/solution/zi-ji-ii-by-leetcode-solution-7inq/来源：力扣（LeetCode）著作权归作者所有。商业转载请联系作者获得授权，非商业转载请注明出处。
````

## ****[60. **排列序列**](https://leetcode-cn.com/problems/permutation-sequence/)

难度困难

给出集合 `[1,2,3,...,n]`，其所有元素共有 `n!` 种排列。

按大小顺序列出所有排列情况，并一一标记，当 `n = 3` 时, 所有排列如下：

1. `"123"`
2. `"132"`
3. `"213"`
4. `"231"`
5. `"312"`
6. `"321"`

给定 `n` 和 `k`，返回第 `k` 个排列。

 

**示例 1：**

```
输入：n = 3, k = 3输出："213"
```

**示例 2：**

```
输入：n = 4, k = 9输出："2314"
```

**示例 3：**

```
输入：n = 3, k = 1输出："123"
```

````java
你知道为什么这个是困难吗    ???    我也不知道    就是有个字典顺序有点烦吧    思路:		1.二进制        2.正儿八经的子集树(剪枝)走下去不可以回头,和之前的不一样.这是输出一个,需要走到底.回溯会错!!!        3.2太复杂了(官方的数论  谁想得到啊喂! )        4.超时太怕了    题解:		1.用字符串            2.瞎写就可以了(这就不是回溯的题)            3.重点看这里吧[康托展开与逆展开](https://blog.csdn.net/qq_45458915/article/details/102561188/)
````

````tex
原来困难时针对我来说的  **小丑就是我自己
````

````java

````



## [93. 复原 IP 地址](https://leetcode-cn.com/problems/restore-ip-addresses/)

难度中等682收藏分享切换为英文接收动态反馈

给定一个只包含数字的字符串，用以表示一个 IP 地址，返回所有可能从 `s` 获得的 **有效 IP 地址** 。你可以按任何顺序返回答案。

**有效 IP 地址** 正好由四个整数（每个整数位于 0 到 255 之间组成，且不能含有前导 `0`），整数之间用 `'.'` 分隔。

例如："0.1.2.201" 和 "192.168.1.1" 是 **有效** IP 地址，但是 "0.011.255.245"、"192.168.1.312" 和 "192.168@1.1" 是 **无效** IP 地址。

 

**示例 1：**

```
输入：s = "25525511135"输出：["255.255.11.135","255.255.111.35"]
```

**示例 2：**

```
输入：s = "0000"输出：["0.0.0.0"]
```

**示例 3：**

```
输入：s = "1111"输出：["1.1.1.1"]
```

**示例 4：**

```
输入：s = "010010"输出：["0.10.0.10","0.100.1.0"]
```

**示例 5：**

```
输入：s = "101023"输出：["1.0.10.23","1.0.102.3","10.1.0.23","10.10.2.3","101.0.2.3"]
```

 





```java
class Solution {    List<String> res = new ArrayList<>();    List<String> path = new ArrayList<>();    public List<String> restoreIpAddresses(String s) {        //这里就是对字符串的预处理，但是对于测试用例来说我觉得用处不大，毕竟不会蠢到用13位数字让你分割        if(s.length()<4 || s.length()>12){            return res;        }        //这里就是套用最经典的回溯模板了，相比于分割字符串只加入分割线一个参数以外，这里还需要添加额外的层数参数level        //因为合法的IP地址只有四段，我们不能无限对其进行分割        backtracking(s,0,0);        return res;    }    // 判断分割出来的每一段字符串是否是合法的IP地址    boolean isValidIp(String s){        //判断其是否含有前导0(dai yiji kaku)        if(s.charAt(0)=='0' && s.length()>1){            return false;        }        //长度为4就直接舍弃，加上这一步是为了后面parseInt做准备,防止超过了Integer可以表示的整数范围        if(s.length()>3){            return false;        }        //将字符转为int判断是否大于255，因为题目明确说了只由数字组成，所以这里没有对非数字的字符进行判断        if(Integer.parseInt(s)>255){            return false;        }        return true;    }    void backtracking(String s,int splitIndex,int level){        //递归终止条件，分割的四个字符串都是合法的IP地址        if(level==4){            //在代码的最后再利用join函数加上“.”,构造IP地址的表示形式            res.add(String.join(".",path));            return;        }        for(int i=splitIndex;i<s.length();i++){            //每一次分割之后，对剩余字符长度是否合理进行判断，剪枝操作，优化运行速度            if((s.length()-i-1) > 3*(3-level)){                continue;            }            //如果分割的字符串不是合理的IP地址，跳过            if(! isValidIp(s.substring(splitIndex,i+1))){                continue;            }            //把合法的IP地址段加入path存储            path.add(s.substring(splitIndex,i+1));            //每次把分割线往后移一位，且段数level+1            backtracking(s,i+1,level+1);            //进行回溯操作            path.remove(path.size()-1);        }    }}
```

## [127. 单词接龙](https://leetcode-cn.com/problems/word-ladder/)

难度困难845收藏分享切换为英文接收动态反馈

字典 `wordList` 中从单词 `beginWord` 和 `endWord` 的 **转换序列** 是一个按下述规格形成的序列：

- 序列中第一个单词是 `beginWord` 。
- 序列中最后一个单词是 `endWord` 。
- 每次转换只能改变一个字母。
- 转换过程中的中间单词必须是字典 `wordList` 中的单词。

给你两个单词 `beginWord` 和 `endWord` 和一个字典 `wordList` ，找到从 `beginWord` 到 `endWord` 的 **最短转换序列** 中的 **单词数目** 。如果不存在这样的转换序列，返回 0。

**示例 1：**

```
输入：beginWord = "hit", endWord = "cog", wordList = ["hot","dot","dog","lot","log","cog"]输出：5解释：一个最短转换序列是 "hit" -> "hot" -> "dot" -> "dog" -> "cog", 返回它的长度 5。
```

**示例 2：**

```
输入：beginWord = "hit", endWord = "cog", wordList = ["hot","dot","dog","lot","log"]输出：0解释：endWord "cog" 不在字典中，所以无法进行转换。
```

````java
package DFSandBFS;import java.util.*;/** * Created with IntelliJ IDEA. * * @Author: 张驰 * @Date: 2021/09/21/16:50 * @Description: 三尺秋水尘不染 *//*示例 1：        输入：beginWord = "hit", endWord = "cog", wordList = ["hot","dot","dog","lot","log","cog"]        输出：5        解释：一个最短转换序列是 "hit" -> "hot" -> "dot" -> "dog" -> "cog", 返回它的长度 5。        示例 2：        输入：beginWord = "hit", endWord = "cog", wordList = ["hot","dot","dog","lot","log"]        输出：0        解释：endWord "cog" 不在字典中，所以无法进行转换。                 来源：力扣（LeetCode）        链接：https://leetcode-cn.com/problems/word-ladder        著作权归领扣网络所有。商业转载请联系官方授权，非商业转载请注明出处。 */public class ladderLength {    /*         * @Method: ladderLength         * @Description: 三尺秋水尘不染         *  * @param beginWord         * @param endWord         * @param wordList         * @paramType:         [java.lang.String, java.lang.String, java.util.List<java.lang.String>]         * @return：int         * @Author: HaRiJi         * @Date: 2021/9/21         */    public int ladderLength(String beginWord, String endWord, List<String> wordList) {        // 第 1 步：先将 wordList 放到哈希表里，便于判断某个单词是否在 wordList 里        HashSet<String> wordSet = new HashSet<>(wordList);        //终止条件更具提议        if (wordSet.size() == 0 || !wordSet.contains(endWord)) {            return 0;        }        //.结果集合中没有 开始的凡此        wordSet.remove(beginWord);        // 第 2 步：图的广度优先遍历，必须使用队列和表示是否访问过的 visited 哈希表        Deque<String> queue = new ArrayDeque<>();        queue.offer(beginWord);        Set<String> visited = new HashSet<>();        visited.add(beginWord);        // 第 3 步：开始广度优先遍历，包含起点，因此初始化的时候步数为 1        int step = 1;        //queue是动态的需要动态判断        while (!queue.isEmpty()) {            int currentSize = queue.size();            for (int i = 0; i < currentSize; i++) {                // 依次遍历当前队列中的单词                String currentWord = queue.poll();                // 如果 currentWord 能够修改 1 个字符与 endWord 相同，则返回 step + 1                if (changeWordEveryOneLetter(currentWord, endWord, queue, visited, wordSet)) {                    return step + 1;                }            }            step++;        }        return 0;    }    /*     * @Method: changeWordEveryOneLetter     * @Description: 三尺秋水尘不染     *  * @param currentWord     * @param endWord     * @param queue     * @param visited     * @param wordSet     * @paramType:     [java.lang.String, java.lang.String, java.util.Queue<java.lang.String>, java.util.Set<java.lang.String>, java.util.Set<java.lang.String>]     * @return：boolean     * @Author: HaRiJi     * @Date: 2021/9/21     */    private boolean changeWordEveryOneLetter(String currentWord, String endWord,                                             Queue<String> queue, Set<String> visited, Set<String> wordSet) {        char[] charArray = currentWord.toCharArray();        for (int i = 0; i < endWord.length(); i++) {            // 先保存，然后恢复            //就三位012            char originChar = charArray[i];            //匹配            for (char k = 'a'; k <= 'z'; k++) {                if (k == originChar) {                    continue;                }                charArray[i] = k;                //取出转换                String nextWord = String.valueOf(charArray);                if (wordSet.contains(nextWord)) {                    if (nextWord.equals(endWord)) {                        return true;                    }                    if (!visited.contains(nextWord)) {                        queue.add(nextWord);                        // 注意：添加到队列以后，必须马上标记为已经访问                        visited.add(nextWord);                    }                }            }            // 恢复            charArray[i] = originChar;        }        return false;    }}
````

分析题意：

「转换」意即：两个单词对应位置只有一个字符不同，例如 "hit" 与 "hot"，这种转换是可以逆向的，因此，根据题目给出的单词列表，可以构建出一个无向（无权）图；

![image.png](https://pic.leetcode-cn.com/ec8f7e4f40134b932a9ff2e306d885e427bd8ee912801361849d92ddae6226f3-image.png)

如果一开始就构建图，每一个单词都需要和除它以外的另外的单词进行比较，复杂度是 O(N \rm{wordLen})O(NwordLen)，这里 NN 是单词列表的长度；
为此，我们在遍历一开始，把所有的单词列表放进一个哈希表中，然后在遍历的时候构建图，每一次得到在单词列表里可以转换的单词，复杂度是 O(26 \times \rm{wordLen})O(26×wordLen)，借助哈希表，找到邻居与 NN 无关；
使用 BFS 进行遍历，需要的辅助数据结构是：
队列；
visited 集合。说明：可以直接在 wordSet (由 wordList 放进集合中得到)里做删除。但更好的做法是新开一个哈希表，遍历过的字符串放进哈希表里。这种做法具有普遍意义。绝大多数在线测评系统和应用场景都不会在意空间开销。

作者：liweiwei1419
链接：https://leetcode-cn.com/problems/word-ladder/solution/yan-du-you-xian-bian-li-shuang-xiang-yan-du-you-2/
来源：力扣（LeetCode）
著作权归作者所有。商业转载请联系作者获得授权，非商业转载请注明出处。

# **DFS:**

### 模板:(队列queue+相邻节点cur+标记数组visited)

````java
// 计算从起点 start 到终点 target 的最近距离int BFS(Node start, Node target) {    Queue<Node> q; // 核心数据结构    Set<Node> visited; // 避免走回头路        q.offer(start); // 将起点加入队列    visited.add(start);    int step = 0; // 记录扩散的步数    while (q not empty) {        int sz = q.size();        /* 将当前队列中的所有节点向四周扩散 */        for (int i = 0; i < sz; i++) {            Node cur = q.poll();            /* 划重点：这里判断是否到达终点 */            if (cur is target)                return step;            /* 将 cur 的相邻节点加入队列 */            for (Node x : cur.adj())                if (x not in visited) {                    q.offer(x);                    visited.add(x);                }        }        /* 划重点：更新步数在这里         step++;    }}
````

### [752. 打开转盘锁](https://leetcode-cn.com/problems/open-the-lock/)

难度中等394收藏分享切换为英文接收动态反馈

你有一个带有四个圆形拨轮的转盘锁。每个拨轮都有10个数字： `'0', '1', '2', '3', '4', '5', '6', '7', '8', '9'` 。每个拨轮可以自由旋转：例如把 `'9'` 变为 `'0'`，`'0'` 变为 `'9'` 。每次旋转都只能旋转一个拨轮的一位数字。

锁的初始数字为 `'0000'` ，一个代表四个拨轮的数字的字符串。

列表 `deadends` 包含了一组死亡数字，一旦拨轮的数字和列表里的任何一个元素相同，这个锁将会被永久锁定，无法再被旋转。

字符串 `target` 代表可以解锁的数字，你需要给出解锁需要的最小旋转次数，如果无论如何不能解锁，返回 `-1` 。

 

**示例 1:**

```
输入：deadends = ["0201","0101","0102","1212","2002"], target = "0202"输出：6解释：可能的移动序列为 "0000" -> "1000" -> "1100" -> "1200" -> "1201" -> "1202" -> "0202"。注意 "0000" -> "0001" -> "0002" -> "0102" -> "0202" 这样的序列是不能解锁的，因为当拨动到 "0102" 时这个锁就会被锁定。
```

**示例 2:**

```
输入: deadends = ["8888"], target = "0009"输出：1解释：把最后一位反向旋转一次即可 "0000" -> "0009"。
```

**示例 3:**

```
输入: deadends = ["8887","8889","8878","8898","8788","8988","7888","9888"], target = "8888"输出：-1解释：无法旋转到目标数字且不被锁定。
```

**示例 4:**

```
输入: deadends = ["0000"], target = "8888"输出：-1
```



「双向 BFS」的基本实现思路如下：

创建「两个队列」分别用于两个方向的搜索；
创建「两个哈希表」用于「解决相同节点重复搜索」和「记录转换次数」；
为了尽可能让两个搜索方向“平均”，每次从队列中取值进行扩展时，先判断哪个队列容量较少；
如果在搜索过程中「搜索到对方搜索过的节点」，说明找到了最短路径。
「双向 BFS」基本思路对应的伪代码大致如下：

```java
d1、d2 为两个方向的队列m1、m2 为两个方向的哈希表，记录每个节点距离起点的    // 只有两个队列都不空，才有必要继续往下搜索// 如果其中一个队列空了，说明从某个方向搜到底都搜不到该方向的目标节点while(!d1.isEmpty() && !d2.isEmpty()) {    if (d1.size() < d2.size()) {        update(d1, m1, m2);    } else {        update(d2, m2, m1);    }}// update 为从队列 d 中取出一个元素进行「一次完整扩展」的逻辑void update(Deque d, Map cur, Map other) {}
```

作者：AC_OIer
链接：https://leetcode-cn.com/problems/open-the-lock/solution/gong-shui-san-xie-yi-ti-shuang-jie-shuan-wyr9/
来源：力扣（LeetCode）
著作权归作者所有。商业转载请联系作者获得授权，非商业转载请注明出处。

````java

````

### 一个集合的子集：

思路和心得：

（一）二进制枚举




      class Solution {    public List<List<Integer>> subsets(int[] nums)     {        int n = nums.length;        List<List<Integer>> res = new ArrayList<>();        for (int state = 0; state < (1 << n); state ++)    {        List<Integer> cur = new ArrayList<>();        for (int i = 0; i < n; i ++)        {            if (((state >> i) & 1) == 1)            {                cur.add(nums[i]);            }        }        res.add(cur);    }    return res;}

}
（二）dfs



    class Solution {    int [] nums;    int n;    List<List<Integer>> res = new ArrayList<>();public List<List<Integer>> subsets(int[] nums) {    this.nums = nums;    n = nums.length;    List<Integer> tmp = new ArrayList<>();    dfs(0, tmp);    return res;}public void dfs(int idx, List<Integer> path){    if (idx == n)    {        res.add(path);        return ;    }    List<Integer> path1 = new ArrayList<>();     path1.addAll(path);    dfs(idx + 1, path1);    path.add(nums[idx]);    List<Integer> path2 = new ArrayList<>();     path2.addAll(path);    dfs(idx + 1, path2);}

}
（三）回溯



    class Solution {    int [] nums;    int n;    List<Integer> path = new ArrayList<>();    List<List<Integer>> res = new ArrayList<>();    public List<List<Integer>> subsets(int[] nums) {    this.nums = nums;    this.n = nums.length;    backtrace(0);    return res;}public void backtrace(int idx){    if (idx == n)    {        res.add(new ArrayList<>(path));        return ;    }    backtrace(idx + 1);    path.add(nums[idx]);    backtrace(idx + 1);    path.remove(path.size() - 1);}

}
下一篇：递归算法

作者：Hanxin_Hanxin
链接：https://leetcode-cn.com/problems/TVdhkn/solution/cpython3java-1er-jin-zhi-mei-ju-2dfs-3hu-3z85/
来源：力扣（LeetCode）
著作权归作者所有。商业转载请联系作者获得授权，非商业转载请注明出处。

# 动态规划：

## 1.1. 爬楼梯

\70. Climbing Stairs (Easy)

[Leetcode (opens new window)](https://leetcode.com/problems/climbing-stairs/description/)/ [力扣(opens new window)](https://leetcode-cn.com/problems/climbing-stairs/description/)

题目描述：有 N 阶楼梯，每次可以上一阶或者两阶，求有多少种上楼梯的方法。

定义一个数组 dp 存储上楼梯的方法数（为了方便讨论，数组下标从 1 开始），dp[i] 表示走到第 i 个楼梯的方法数目。

第 i 个楼梯可以从第 i-1 和 i-2 个楼梯再走一步到达，走到第 i 个楼梯的方法数为走到第 i-1 和第 i-2 个楼梯的方法数之和。

![img](https://cs-notes-1256109796.cos.ap-guangzhou.myqcloud.com/14fe1e71-8518-458f-a220-116003061a83.png)



考虑到 dp[i] 只与 dp[i - 1] 和 dp[i - 2] 有关，因此可以只用两个变量来存储 dp[i - 1] 和 dp[i - 2]，使得原来的 O(N) 空间复杂度优化为 O(1) 复杂度。

> 方法1:利用状态方程:

````java
class Solution{    public int climbStairs(int n){		int[] dp = new int[n+1];        dp[0] = 1,dp[1] = 1;        for(int i = 0;i<n+1;i++){            dp[i] = dp[i-1] + dp[i-2];        }        return dp[n];    }}
````

> 技巧二:滚动数组(优化dp空间)O(n)~O(1)

````java
class Solution{    public int climbStairs(int n){		int p = 0, q =0 r = 1;        for(int i = 0; i< n+1;i++){			p = q;            q = r;            r = p + q;        }return r;    }}
````

> 补充:
>
> 技巧:矩阵快速幂复杂度n小的时候可以
>
> ​		通项公式

## 2.打家劫舍198(环状的房屋)

你是一个专业的小偷，计划偷窃沿街的房屋，每间房内都藏有一定的现金。这个地方所有的房屋**都 围成一圈** ，这意味着第一个房屋和最后一个房屋是紧挨着的。同时，相邻的房屋装有相互连通的防盗系统，如果两间相邻的房屋在同一晚上被小偷闯入，系统会自动报警 。

给定一个代表每个房屋存放金额的非负整数数组，计算你 在不触动警报装置的情况下 ，今晚能够偷窃到的最高金额。

 

示例 1：

输入：nums = [2,3,2]
输出：3
解释：你不能先偷窃 1 号房屋（金额 = 2），然后偷窃 3 号房屋（金额 = 2）, 因为他们是相邻的。
示例 2：

输入：nums = [1,2,3,1]
输出：4
解释：你可以先偷窃 1 号房屋（金额 = 1），然后偷窃 3 号房屋（金额 = 3）。
     偷窃到的最高金额 = 1 + 3 = 4 。2
示例 3：

输入：nums = [0]
输出：0

由于不能抢劫邻近住户，如果抢劫了第 i -1 个住户，那么就不能再抢劫第 i 个住户，所以

![img](https://cs-notes-1256109796.cos.ap-guangzhou.myqcloud.com/2de794ca-aa7b-48f3-a556-a0e2708cb976.jpg)

````java
public int rob(int[] nums) {        int pre2 = 0, pre1 = 0;        for (int i = 0; i < nums.length; i++) {               int cur = Math.max(pre2 + nums[i], pre1);                pre2 = pre1;                pre1 = cur;            }    return pre1;}
````



## 2.1[213. 打家劫舍 II](https://leetcode-cn.com/problems/house-robber-ii/)

你是一个专业的小偷，计划偷窃沿街的房屋，每间房内都藏有一定的现金。这个地方所有的房屋都 **围成一圈** ，这意味着第一个房屋和最后一个房屋是紧挨着的。同时，相邻的房屋装有相互连通的防盗系统，**如果两间相邻的房屋在同一晚上被小偷闯入，系统会自动报警** 。

给定一个代表每个房屋存放金额的非负整数数组，计算你 **在不触动警报装置的情况下** ，今晚能够偷窃到的最高金额。

 

**示例 1：**

```
输入：nums = [2,3,2]输出：3解释：你不能先偷窃 1 号房屋（金额 = 2），然后偷窃 3 号房屋（金额 = 2）, 因为他们是相邻的。
```

**示例 2：**

```
输入：nums = [1,2,3,1]输出：4解释：你可以先偷窃 1 号房屋（金额 = 1），然后偷窃 3 号房屋（金额 = 3）。     偷窃到的最高金额 = 1 + 3 = 4 。
```

**示例 3：**

```
输入：nums = [0]输出：0
```

````java
//两种思路:1.差分成单个的两种:{   	1、不偷窃最后一间房间，那么问题转化为偷窃0号到i - 1号房间所能获得的最高金额。	2、不偷窃第一间房间，那么问题转化为偷窃1号到i号房间所能获得的最高金额。}class Solution {    public int rob(int[] nums) {        if(nums.length == 0) return 0;        if(nums.length == 1) return nums[0];        return Math.max(myRob(Arrays.copyOfRange(nums, 0, nums.length - 1)),                         myRob(Arrays.copyOfRange(nums, 1, nums.length)));    }    private int myRob(int[] nums) {        int pre = 0, cur = 0, tmp;        for(int num : nums) {            tmp = cur;            cur = Math.max(pre + num, cur);            pre = tmp;        }        return cur;    }}作者：jyd链接：https://leetcode-cn.com/problems/house-robber-ii/solution/213-da-jia-jie-she-iidong-tai-gui-hua-jie-gou-hua-/来源：力扣（LeetCode）著作权归作者所有。商业转载请联系作者获得授权，非商业转载请注明出处。`我的:`   int n = nums.length;       if(n == 1) return nums[0];     //只有一间房间，返回nums[0]       int[] f = new int[n + 1],  g = new int[n + 1];       f[1] = nums[0];    //初始化       g[2] = nums[1];        for(int i = 1; i < n-1; ++i) f[i+1] = Math.max(f[i], f[i - 1] + nums[i]);       for(int i = 2; i < n; ++i)     g[i+1] = Math.max(g[i], g[i - 1] + nums[i]);       return Math.max(f[n - 1], g[n]);    }
````

## 矩阵问题:

### 1. 矩阵的最小路径和

\64. Minimum Path Sum (Medium)

[Leetcode (opens new window)](https://leetcode.com/problems/minimum-path-sum/description/)/ [力扣(opens new window)](https://leetcode-cn.com/problems/minimum-path-sum/description/)

```html
[[1,3,1], [1,5,1], [4,2,1]]Given the above grid map, return 7. Because the path 1→3→1→1→1 minimizes the sum.
```

题目描述：求从矩阵的左上角到右下角的最小路径和，每次只能向右和向下移动。

![image-20210929152747481](C:\Users\HaRiJi\AppData\Roaming\Typora\typora-user-images\image-20210929152747481.png)



```java
//利用DP[][]数组保存我们的路径值:class Solution{   public int minPathSum(int[][] grid) {       if(grid == null || grid.length == 0 || grid[0].length == 0){           return 0;       }              //初始化变量       int row = grid.length; int col = grid[0].length;       int[][] dp = new int[row][col];       dp[0][0] = grid[0][0];       //初始化dp数组外层       for(int i = 1; i < row; i++){           //往右走           //左边加当前的为第一行的dp           dp[i][0] = dp[i - 1][0] +grid[i][0];                  }       for(int j = 1;j < col; j++){           //向下走           //值为上边的加当前的           dp[0][j] = dp[0][j - 1] +grid[0][j];       }       //使用状态转移方程      for(int i = 1; i < row; i++){         for(int j = 1;j < col; j++){      		dp[i][j] = Math.min(dp[i-1][j],dp[i][j-1]) + grid[i][j];                }      }              //返回状态转移方程的结果为二维数组的最后一个       return dp[row-1][col-1];   }}
```

```java
//优化版本如下:(直接修改原来的数组)class Solution {    public int minPathSum(int[][] grid) {        for(int i = 0; i < grid.length; i++) {            for(int j = 0; j < grid[0].length; j++) {                  //初始化dp数组外层                if(i == 0 && j == 0) continue;                else if(i == 0)  grid[i][j] = grid[i][j - 1] + grid[i][j];                else if(j == 0)  grid[i][j] = grid[i - 1][j] + grid[i][j];                 //使用状态转移方程                else grid[i][j] = Math.min(grid[i - 1][j], grid[i][j - 1]) + grid[i][j];            }        }        //返回状态转移方程的结果为二维数组的最后一个        return grid[grid.length - 1][grid[0].length - 1];    }}作者：jyd链接：https://leetcode-cn.com/problems/minimum-path-sum/solution/zui-xiao-lu-jing-he-dong-tai-gui-hua-gui-fan-liu-c/来源：力扣（LeetCode）著作权归作者所有。商业转载请联系作者获得授权，非商业转载请注明出处。
```

### [62. 不同路径](https://leetcode-cn.com/problems/unique-paths/)

难度中等1125

一个机器人位于一个 `m x n` 网格的左上角 （起始点在下图中标记为 “Start” ）。

机器人每次只能向下或者向右移动一步。机器人试图达到网格的右下角（在下图中标记为 “Finish” ）。

问总共有多少条不同的路径？

 

**示例 1：**

![img](https://assets.leetcode.com/uploads/2018/10/22/robot_maze.png)

```
输入：m = 3, n = 7输出：28
```

**示例 2：**

```
输入：m = 3, n = 2输出：3解释：从左上角开始，总共有 3 条路径可以到达右下角。1. 向右 -> 向下 -> 向下2. 向下 -> 向下 -> 向右3. 向下 -> 向右 -> 向下
```

**示例 3：**

```
输入：m = 7, n = 3输出：28
```

**示例 4：**

```
输入：m = 3, n = 3输出：6
```

优化:二维转一维

````java
public int uniquePaths(int m, int n) {    int[] dp = new int[n];    Arrays.fill(dp, 1);    for (int i = 1; i < m; i++) {        for (int j = 1; j < n; j++) {            dp[j] = dp[j] + dp[j - 1];        }    }    return dp[n - 1];}
````

普通:

````java
public int uniquePaths(int m,int n){    int[][] dp = new int[m][n];    for(int i = 0;i < m;i++){        dp[i][0] = 1;    }    for(int j = 0;j < n;j++){        dp[0][j] = 1;    }    for(int i = 0;i < m;i++){     for(int j = 0;j < n;j++){    	dp[i][j] = dp[i-1][j]+dp[i][j-1];          }    }    return dp[m-1][n-1];}
````

## 数组区间

### [#](http://www.cyc2018.xyz/算法/Leetcode 题解/Leetcode 题解 - 动态规划.html#_1-数组区间和)1. 数组区间和

### 1. 数组区间和

\303. Range Sum Query - Immutable (Easy)

[Leetcode (opens new window)](https://leetcode.com/problems/range-sum-query-immutable/description/)/ [力扣(opens new window)](https://leetcode-cn.com/problems/range-sum-query-immutable/description/)

```html
Given nums = [-2, 0, 3, -5, 2, -1]sumRange(0, 2) -> 1sumRange(2, 5) -> -1sumRange(0, 5) -> -3
```

求区间 i ~ j 的和，可以转换为 sum[j + 1] - sum[i]，其中 sum[i] 为 0 ~ i - 1 的和。

````java
class NumArray {public int[] NumArray;    public NumArray(int[] nums) {        int length = nums.length;        NumArray = new int[length+1];        //关键地方        for(int i = 1;i < length+1 ;i++){            NumArray[i] = NumArray[i-1] + nums[i-1];         }     }        public int sumRange(int left, int right) {        return NumArray[right + 1] - NumArray[left];    }}/** * Your NumArray object will be instantiated and called as such: * NumArray obj = new NumArray(nums); * int param_1 = obj.sumRange(left,right); */
````



### 2. 数组中等差递增子区间的个数

\413. Arithmetic Slices (Medium)

[Leetcode (opens new window)](https://leetcode.com/problems/arithmetic-slices/description/)/ [力扣(opens new window)](https://leetcode-cn.com/problems/arithmetic-slices/description/)

```html
A = [0, 1, 2, 3, 4]return: 6, for 3 arithmetic slices in A:[0, 1, 2],[1, 2, 3],[0, 1, 2, 3],[0, 1, 2, 3, 4],[ 1, 2, 3, 4],[2, 3, 4]
```

dp[i] 表示以 A[i] 为结尾的等差递增子区间的个数。

当 A[i] - A[i-1] == A[i-1] - A[i-2]，那么 [A[i-2], A[i-1], A[i]] 构成一个等差递增子区间。而且在以 A[i-1] 为结尾的递增子区间的后面再加上一个 A[i]，一样可以构成新的递增子区间。

```html
dp[2] = 1    [0, 1, 2]dp[3] = dp[2] + 1 = 2    [0, 1, 2, 3], // [0, 1, 2] 之后加一个 3    [1, 2, 3]     // 新的递增子区间dp[4] = dp[3] + 1 = 3    [0, 1, 2, 3, 4], // [0, 1, 2, 3] 之后加一个 4    [1, 2, 3, 4],    // [1, 2, 3] 之后加一个 4    [2, 3, 4]        // 新的递增子区间
```

综上，在 A[i] - A[i-1] == A[i-1] - A[i-2] 时，dp[i] = dp[i-1] + 1。

因为递增子区间不一定以最后一个元素为结尾，可以是任意一个元素结尾，因此需要返回 dp 数组累加的结果。

````java

````



# 二分法

![img](https://labuladong.gitee.io/algo/images/%E4%BA%8C%E5%88%86%E6%9F%A5%E6%89%BE/poem.png)



模板

````java
int left_bound(int[] nums, int target) {    int left = 0, right = nums.length - 1;    // 搜索区间为 [left, right]    while (left <= right) {        int mid = left + (right - left) / 2;        if (nums[mid] < target) {            // 搜索区间变为 [mid+1, right]            left = mid + 1;        } else if (nums[mid] > target) {            // 搜索区间变为 [left, mid-1]            right = mid - 1;        } else if (nums[mid] == target) {            // 收缩右侧边界            right = mid - 1;        }    }    // 检查出界情况    if (left >= nums.length || nums[left] != target)        return -1;    return left;}
````

#### **第一个，最基本的二分查找算法**：

```python
因为我们初始化 right = nums.length - 1所以决定了我们的「搜索区间」是 [left, right]所以决定了 while (left <= right)同时也决定了 left = mid+1 和 right = mid-1因为我们只需找到一个 target 的索引即可所以当 nums[mid] == target 时可以立即返回
```

#### **第二个，寻找左侧边界的二分查找**：

```python
因为我们初始化 right = nums.length所以决定了我们的「搜索区间」是 [left, right)所以决定了 while (left < right)同时也决定了 left = mid + 1 和 right = mid因为我们需找到 target 的最左侧索引所以当 nums[mid] == target 时不要立即返回而要收紧右侧边界以锁定左侧边界
```

#### **第三个，寻找右侧边界的二分查找**：

```python
因为我们初始化 right = nums.length所以决定了我们的「搜索区间」是 [left, right)所以决定了 while (left < right)同时也决定了 left = mid + 1 和 right = mid因为我们需找到 target 的最右侧索引所以当 nums[mid] == target 时不要立即返回而要收紧左侧边界以锁定右侧边界又因为收紧左侧边界时必须 left = mid + 1所以最后无论返回 left 还是 right，必须减一
```

对于寻找左右边界的二分搜索，常见的手法是使用左闭右开的「搜索区间」，**我们还根据逻辑将「搜索区间」全都统一成了两端都闭，便于记忆，只要修改两处即可变化出三种写法**：

```java
int binary_search(int[] nums, int target) {    int left = 0, right = nums.length - 1;     while(left <= right) {        int mid = left + (right - left) / 2;        if (nums[mid] < target) {            left = mid + 1;        } else if (nums[mid] > target) {            right = mid - 1;         } else if(nums[mid] == target) {            // 直接返回            return mid;        }    }    // 直接返回    return -1;}int left_bound(int[] nums, int target) {    int left = 0, right = nums.length - 1;    while (left <= right) {        int mid = left + (right - left) / 2;        if (nums[mid] < target) {            left = mid + 1;        } else if (nums[mid] > target) {            right = mid - 1;        } else if (nums[mid] == target) {            // 别返回，锁定左侧边界            right = mid - 1;        }    }    // 最后要检查 left 越界的情况    if (left >= nums.length || nums[left] != target)        return -1;    return left;}int right_bound(int[] nums, int target) {    int left = 0, right = nums.length - 1;    while (left <= right) {        int mid = left + (right - left) / 2;        if (nums[mid] < target) {            left = mid + 1;        } else if (nums[mid] > target) {            right = mid - 1;        } else if (nums[mid] == target) {            // 别返回，锁定右侧边界            left = mid + 1;        }    }    // 最后要检查 right 越界的情况    if (right < 0 || nums[right] != target)        return -1;    return right;}
```

如果以上内容你都能理解，那么恭喜你，二分查找算法的细节不过如此。













# 滑动窗口:

本质为***暴力递归优化后的双指针的优化版.***

![img](https://labuladong.gitee.io/algo/images/slidingwindow/poem.png)

## [3. 无重复字符的最长子串](https://leetcode-cn.com/problems/longest-substring-without-repeating-characters/)

难度中等6149收藏分享切换为英文接收动态反馈

给定一个字符串 `s` ，请你找出其中不含有重复字符的 **最长子串** 的长度。

 

**示例 1:**

```
输入: s = "abcabcbb"输出: 3 解释: 因为无重复字符的最长子串是 "abc"，所以其长度为 3。
```

**示例 2:**

```
输入: s = "bbbbb"输出: 1解释: 因为无重复字符的最长子串是 "b"，所以其长度为 1。
```

**示例 3:**

```
输入: s = "pwwkew"输出: 3解释: 因为无重复字符的最长子串是 "wke"，所以其长度为 3。     请注意，你的答案必须是 子串 的长度，"pwke" 是一个子序列，不是子串。
```

**示例 4:**

```
输入: s = ""输出: 0
```

````java
class Solution {    public int lengthOfLongestSubstring(String s) {         HashMap<Character,Integer> map = new HashMap<Character,Integer> ();            int length =  s.length();            int ans = 0;            for(int start = 0 ,end = 0;end < length; end++ ){                if(map.containsKey(s.charAt(end))){                    start = Math.max(map.get(s.charAt(end)),start);                }                ans = Math.max(ans,end-start+1);                map.put(s.charAt(end),end+1);            }            return ans;    }}
````

## [76. 最小覆盖子串](https://leetcode-cn.com/problems/minimum-window-substring/)

难度困难1350收藏分享切换为英文接收动态反馈

给你一个字符串 `s` 、一个字符串 `t` 。返回 `s` 中涵盖 `t` 所有字符的最小子串。如果 `s` 中不存在涵盖 `t` 所有字符的子串，则返回空字符串 `""` 。

 

**注意：**

- 对于 `t` 中重复字符，我们寻找的子字符串中该字符数量必须不少于 `t` 中该字符数量。
- 如果 `s` 中存在这样的子串，我们保证它是唯一的答案。

 

**示例 1：**

```
输入：s = "ADOBECODEBANC", t = "ABC"输出："BANC"
```

**示例 2：**

```
输入：s = "a", t = "a"输出："a"
```

**示例 3:**

```
输入: s = "a", t = "aa"输出: ""解释: t 中两个字符 'a' 均应包含在 s 的子串中，因此没有符合条件的子字符串，返回空字符串。
```

````java
class Solution {    public String minWindow(String s, String t) {        if (s == null || s == "" || t == null || t == "" || s.length() < t.length()) {            return "";        }        //维护两个数组，记录已有字符串指定字符的出现次数，和目标字符串指定字符的出现次数        //ASCII表总长128        int[] need = new int[128];        int[] have = new int[128];        //将目标字符串指定字符的出现次数记录        for (int i = 0; i < t.length(); i++) {            need[t.charAt(i)]++;        }        //分别为左指针，右指针，最小长度(初始值为一定不可达到的长度)        //已有字符串中目标字符串指定字符的出现总频次以及最小覆盖子串在原字符串中的起始位置        int left = 0, right = 0, min = s.length() + 1, count = 0, start = 0;        while (right < s.length()) {            char r = s.charAt(right);            //说明该字符不被目标字符串需要，此时有两种情况            // 1.循环刚开始，那么直接移动右指针即可，不需要做多余判断            // 2.循环已经开始一段时间，此处又有两种情况            //  2.1 上一次条件不满足，已有字符串指定字符出现次数不满足目标字符串指定字符出现次数，那么此时            //      如果该字符还不被目标字符串需要，就不需要进行多余判断，右指针移动即可            //  2.2 左指针已经移动完毕，那么此时就相当于循环刚开始，同理直接移动右指针            if (need[r] == 0) {                right++;                continue;            }            //当且仅当已有字符串目标字符出现的次数小于目标字符串字符的出现次数时，count才会+1            //是为了后续能直接判断已有字符串是否已经包含了目标字符串的所有字符，不需要挨个比对字符出现的次数            if (have[r] < need[r]) {                count++;            }            //已有字符串中目标字符出现的次数+1            have[r]++;            //移动右指针            right++;            //当且仅当已有字符串已经包含了所有目标字符串的字符，且出现频次一定大于或等于指定频次            while (count == t.length()) {                //挡窗口的长度比已有的最短值小时，更改最小值，并记录起始位置                if (right - left < min) {                    min = right - left;                    start = left;                }                char l = s.charAt(left);                //如果左边即将要去掉的字符不被目标字符串需要，那么不需要多余判断，直接可以移动左指针                if (need[l] == 0) {                    left++;                    continue;                }                //如果左边即将要去掉的字符被目标字符串需要，且出现的频次正好等于指定频次，那么如果去掉了这个字符，                //就不满足覆盖子串的条件，此时要破坏循环条件跳出循环，即控制目标字符串指定字符的出现总频次(count）-1                if (have[l] == need[l]) {                    count--;                }                //已有字符串中目标字符出现的次数-1                have[l]--;                //移动左指针                left++;            }        }        //如果最小长度还为初始值，说明没有符合条件的子串        if (min == s.length() + 1) {            return "";        }        //返回的为以记录的起始位置为起点，记录的最短长度为距离的指定字符串中截取的子串        return s.substring(start, start + min);    }}
````

你知道滑动窗口是怎么画起来的吗?

![image-20210922195200418](C:\Users\HaRiJi\AppData\Roaming\Typora\typora-user-images\image-20210922195200418.png)

````java
class Solution {    public String minWindow(String s, String t) {        //保存s        HashMap<Character,Integer> hs = new HashMap<Character,Integer>();        //保存t        HashMap<Character,Integer> ht = new HashMap<Character,Integer>();                for(int i = 0;i < t.length();i ++){            ht.put(t.charAt(i),ht.getOrDefault(t.charAt(i), 0) + 1);        }        String ans = "";        //一个得不到的数字罢了,就按照长度加一就好了.        int len = 0x3f3f3f3f, cnt = 0;  //有多少个元素符合                for(int i = 0,j = 0;i < s.length();i ++)                    {            hs.put(s.charAt(i), hs.getOrDefault(s.charAt(i), 0) + 1);                        if(ht.containsKey(s.charAt(i)) && hs.get(s.charAt(i)) <= ht.get(s.charAt(i))) cnt ++;                        while(j < i && (!ht.containsKey(s.charAt(j)) || hs.get(s.charAt(j)) > ht.get(s.charAt(j)))){                int count = hs.get(s.charAt(j)) - 1;                                hs.put(s.charAt(j), count);                                j ++;            }                        if(cnt == t.length() && i - j + 1 < len){                                len = i - j + 1;                                ans = s.substring(j,i + 1);            }        }                return ans;    }}作者：lin-shen-shi-jian-lu-k链接：https://leetcode-cn.com/problems/minimum-window-substring/solution/leetcode-76-zui-xiao-fu-gai-zi-chuan-cja-lmqz/来源：力扣（LeetCode）著作权归作者所有。商业转载请联系作者获得授权，非商业转载请注明出处。
````

 

# **岛屿系列**：

本期例题为 LeetCode「岛屿问题」系列：

- [**LeetCode 463. Island Perimeter** 岛屿的周长（Easy）]()
- [**LeetCode 695. Max Area of Island** 岛屿的最大面积（Medium）]()
- [**LeetCode 827. Making A Large Island** 填海造陆（Hard）]()

我们所熟悉的 DFS（深度优先搜索）问题通常是在树或者图结构上进行的。而我们今天要讨论的 DFS 问题，是在一种「网格」结构中进行的。岛屿问题是这类网格 DFS 问题的典型代表。网格结构遍历起来要比二叉树复杂一些，如果没有掌握一定的方法，DFS 代码容易写得冗长繁杂。

本文将以岛屿问题为例，展示网格类问题 DFS 通用思路，以及如何让代码变得简洁。主要内容包括：

- 网格类问题的基本性质
- 在网格中进行 DFS 遍历的方法与技巧
- 三个岛屿问题的解法
- 相关题目

## 网格类问题的 DFS 遍历方法

### 网格问题的基本概念

我们首先明确一下岛屿问题中的网格结构是如何定义的，以方便我们后面的讨论。

网格问题是由 个小方格组成一个网格，每个小方格与其上下左右四个方格认为是相邻的，要在这样的网格上进行某种搜索。

岛屿问题是一类典型的网格问题。每个格子中的数字可能是 0 或者 1。我们把数字为 0 的格子看成海洋格子，数字为 1 的格子看成陆地格子，这样相邻的陆地格子就连接成一个岛屿。

![图片](https://mmbiz.qpic.cn/mmbiz_jpg/TKAD4axFcib8CSJjOnbGUamCj2B7OiclOvfCa2mN4vYZpiaUicV2YeKibVCXmQW0TTQ8U4EkHCRyibHLogpl5malQLPw/640?wx_fmt=jpeg&tp=webp&wxfrom=5&wx_lazy=1&wx_co=1)岛屿问题示例

在这样一个设定下，就出现了各种岛屿问题的变种，包括岛屿的数量、面积、周长等。不过这些问题，基本都可以用 DFS 遍历来解决。

### DFS 的基本结构

网格结构要比二叉树结构稍微复杂一些，它其实是一种简化版的**图**结构。要写好网格上的 DFS 遍历，我们首先要理解二叉树上的 DFS 遍历方法，再类比写出网格结构上的 DFS 遍历。我们写的二叉树 DFS 遍历一般是这样的：

```
void traverse(TreeNode root) {    // 判断 base case    if (root == null) {        return;    }    // 访问两个相邻结点：左子结点、右子结点    traverse(root.left);    traverse(root.right);}
```

可以看到，二叉树的 DFS 有两个要素：「**访问相邻结点**」和「**判断 base case**」。

第一个要素是**访问相邻结点**。二叉树的相邻结点非常简单，只有左子结点和右子结点两个。二叉树本身就是一个递归定义的结构：一棵二叉树，它的左子树和右子树也是一棵二叉树。那么我们的 DFS 遍历只需要递归调用左子树和右子树即可。

第二个要素是 **判断 base case**。一般来说，二叉树遍历的 base case 是 `root == null`。这样一个条件判断其实有两个含义：一方面，这表示 `root` 指向的子树为空，不需要再往下遍历了。另一方面，在 `root == null` 的时候及时返回，可以让后面的 `root.left` 和 `root.right` 操作不会出现空指针异常。

对于网格上的 DFS，我们完全可以参考二叉树的 DFS，写出网格 DFS 的两个要素：

首先，网格结构中的格子有多少相邻结点？答案是上下左右四个。对于格子 `(r, c)` 来说（r 和 c 分别代表行坐标和列坐标），四个相邻的格子分别是 `(r-1, c)`、`(r+1, c)`、`(r, c-1)`、`(r, c+1)`。换句话说，网格结构是「四叉」的。

![图片](https://mmbiz.qpic.cn/mmbiz_jpg/TKAD4axFcib8CSJjOnbGUamCj2B7OiclOv9IsSuia3DE42FJWfpThMFlfng0OKu0nsPmwDv2J5BHUkSibGy0KbA4Fg/640?wx_fmt=jpeg&tp=webp&wxfrom=5&wx_lazy=1&wx_co=1)网格结构中四个相邻的格子

其次，网格 DFS 中的 base case 是什么？从二叉树的 base case 对应过来，应该是网格中不需要继续遍历、`grid[r][c]` 会出现数组下标越界异常的格子，也就是那些超出网格范围的格子。

![图片](https://mmbiz.qpic.cn/mmbiz_jpg/TKAD4axFcib8CSJjOnbGUamCj2B7OiclOvddOM2NyLmWmXcwicNe3aUI1U6eYFpq3WibINqFgZAkmicpxjbsRP0SrSw/640?wx_fmt=jpeg&tp=webp&wxfrom=5&wx_lazy=1&wx_co=1)网格 DFS 的 base case

这一点稍微有些反直觉，坐标竟然可以临时超出网格的范围？这种方法我称为「先污染后治理」—— 甭管当前是在哪个格子，先往四个方向走一步再说，如果发现走出了网格范围再赶紧返回。这跟二叉树的遍历方法是一样的，先递归调用，发现 `root == null` 再返回。

这样，我们得到了网格 DFS 遍历的框架代码：

```
void dfs(int[][] grid, int r, int c) {    // 判断 base case    // 如果坐标 (r, c) 超出了网格范围，直接返回    if (!inArea(grid, r, c)) {        return;    }    // 访问上、下、左、右四个相邻结点    dfs(grid, r - 1, c);    dfs(grid, r + 1, c);    dfs(grid, r, c - 1);    dfs(grid, r, c + 1);}// 判断坐标 (r, c) 是否在网格中boolean inArea(int[][] grid, int r, int c) {    return 0 <= r && r < grid.length          && 0 <= c && c < grid[0].length;}
```

### 如何避免重复遍历

网格结构的 DFS 与二叉树的 DFS 最大的不同之处在于，遍历中可能遇到遍历过的结点。这是因为，网格结构本质上是一个「图」，我们可以把每个格子看成图中的结点，每个结点有向上下左右的四条边。在图中遍历时，自然可能遇到重复遍历结点。

这时候，DFS 可能会不停地「兜圈子」，永远停不下来，如下图所示：

![图片](https://mmbiz.qpic.cn/mmbiz_gif/TKAD4axFcib8CSJjOnbGUamCj2B7OiclOvhNwXiaoJdXnDNUGpmtqqlHIbPnpejyAVqnQqODmYMIxovmlLcn0xEicA/640?wx_fmt=gif&tp=webp&wxfrom=5&wx_lazy=1)DFS 遍历可能会兜圈子（动图）

如何避免这样的重复遍历呢？答案是标记已经遍历过的格子。以岛屿问题为例，我们需要在所有值为 1 的陆地格子上做 DFS 遍历。每走过一个陆地格子，就把格子的值改为 2，这样当我们遇到 2 的时候，就知道这是遍历过的格子了。也就是说，每个格子可能取三个值：

- 0 —— 海洋格子
- 1 —— 陆地格子（未遍历过）
- 2 —— 陆地格子（已遍历过）

我们在框架代码中加入避免重复遍历的语句：

```
void dfs(int[][] grid, int r, int c) {    // 判断 base case    if (!inArea(grid, r, c)) {        return;    }    // 如果这个格子不是岛屿，直接返回    if (grid[r][c] != 1) {        return;    }    grid[r][c] = 2; // 将格子标记为「已遍历过」        // 访问上、下、左、右四个相邻结点    dfs(grid, r - 1, c);    dfs(grid, r + 1, c);    dfs(grid, r, c - 1);    dfs(grid, r, c + 1);}// 判断坐标 (r, c) 是否在网格中boolean inArea(int[][] grid, int r, int c) {    return 0 <= r && r < grid.length          && 0 <= c && c < grid[0].length;}
```

![图片](data:image/gif;base64,iVBORw0KGgoAAAANSUhEUgAAAAEAAAABCAYAAAAfFcSJAAAADUlEQVQImWNgYGBgAAAABQABh6FO1AAAAABJRU5ErkJggg==)标记已遍历的格子

这样，我们就得到了一个岛屿问题、乃至各种网格问题的通用 DFS 遍历方法。以下所讲的几个例题，其实都只需要在 DFS 遍历框架上稍加修改而已。

> **小贴士：**
>
> 在一些题解中，可能会把「已遍历过的陆地格子」标记为和海洋格子一样的 0，美其名曰「陆地沉没方法」，即遍历完一个陆地格子就让陆地「沉没」为海洋。这种方法看似很巧妙，但实际上有很大隐患，因为这样我们就无法区分「海洋格子」和「已遍历过的陆地格子」了。如果题目更复杂一点，这很容易出 bug。

## 岛屿问题的解法

理解了网格结构的 DFS 遍历方法以后，岛屿问题就不难解决了。下面我们分别看看三个题目该如何用 DFS 遍历来求解。

### 例题 1：岛屿的最大面积

**LeetCode 695. Max Area of Island** （Medium）

> 给定一个包含了一些 0 和 1 的非空二维数组 `grid`，一个岛屿是一组相邻的 1（代表陆地），这里的「相邻」要求两个 1 必须在水平或者竖直方向上相邻。你可以假设 `grid` 的四个边缘都被 0（代表海洋）包围着。
>
> 找到给定的二维数组中最大的岛屿面积。如果没有岛屿，则返回面积为 0 。

这道题目只需要对每个岛屿做 DFS 遍历，求出每个岛屿的面积就可以了。求岛屿面积的方法也很简单，代码如下，每遍历到一个格子，就把面积加一。

```
int area(int[][] grid, int r, int c) {      return 1         + area(grid, r - 1, c)        + area(grid, r + 1, c)        + area(grid, r, c - 1)        + area(grid, r, c + 1);}
```

最终我们得到的完整题解代码如下：

```
public int maxAreaOfIsland(int[][] grid) {    int res = 0;    for (int r = 0; r < grid.length; r++) {        for (int c = 0; c < grid[0].length; c++) {            if (grid[r][c] == 1) {                int a = area(grid, r, c);                res = Math.max(res, a);            }        }    }    return res;}int area(int[][] grid, int r, int c) {    if (!inArea(grid, r, c)) {        return 0;    }    if (grid[r][c] != 1) {        return 0;    }    grid[r][c] = 2;        return 1         + area(grid, r - 1, c)        + area(grid, r + 1, c)        + area(grid, r, c - 1)        + area(grid, r, c + 1);}boolean inArea(int[][] grid, int r, int c) {    return 0 <= r && r < grid.length          && 0 <= c && c < grid[0].length;}
```

### 例题 2：填海造陆问题

**LeetCode 827. Making A Large Island** （Hard）

> 在二维地图上， 0 代表海洋，1代表陆地，我们最多只能将一格 0 （海洋）变成 1 （陆地）。进行填海之后，地图上最大的岛屿面积是多少？

这道题是岛屿最大面积问题的升级版。现在我们有填海造陆的能力，可以把一个海洋格子变成陆地格子，进而让两块岛屿连成一块。那么填海造陆之后，最大可能构造出多大的岛屿呢？

大致的思路我们不难想到，我们先计算出所有岛屿的面积，在所有的格子上标记出岛屿的面积。然后搜索哪个海洋格子相邻的两个岛屿面积最大。例如下图中红色方框内的海洋格子，上边、左边都与岛屿相邻，我们可以计算出它变成陆地之后可以连接成的岛屿面积为 。

![图片](https://mmbiz.qpic.cn/mmbiz_jpg/TKAD4axFcib8CSJjOnbGUamCj2B7OiclOv1hBJr1PNvOaHctNRUJalic7NibSotbQEMJnbibwiaeZ05FiaKrodTqZuZ7Q/640?wx_fmt=jpeg&tp=webp&wxfrom=5&wx_lazy=1&wx_co=1)一个海洋格子连接起两个岛屿

然而，这种做法可能遇到一个问题。如下图中红色方框内的海洋格子，它的上边、左边都与岛屿相邻，这时候连接成的岛屿面积难道是 ？显然不是。这两个 7 来自同一个岛屿，所以填海造陆之后得到的岛屿面积应该只有 。

![图片](data:image/gif;base64,iVBORw0KGgoAAAANSUhEUgAAAAEAAAABCAYAAAAfFcSJAAAADUlEQVQImWNgYGBgAAAABQABh6FO1AAAAABJRU5ErkJggg==)一个海洋格子与同一个岛屿有两个边相邻

可以看到，要让算法正确，我们得能区分一个海洋格子相邻的两个 7 是不是来自同一个岛屿。那么，我们不能在方格中标记岛屿的面积，而应该标记岛屿的索引（下标），另外用一个数组记录每个岛屿的面积，如下图所示。这样我们就可以发现红色方框内的海洋格子，它的「两个」相邻的岛屿实际上是同一个。

![图片](https://mmbiz.qpic.cn/mmbiz_jpg/TKAD4axFcib8CSJjOnbGUamCj2B7OiclOvmhcyNNzBnr99s7fTPmoyHqrc31AGMANhQN1lt0gOXIibHbuc6ViadgeQ/640?wx_fmt=jpeg&tp=webp&wxfrom=5&wx_lazy=1&wx_co=1)标记每个岛屿的索引（下标）

可以看到，这道题实际上是对网格做了两遍 DFS：第一遍 DFS 遍历陆地格子，计算每个岛屿的面积并标记岛屿；第二遍 DFS 遍历海洋格子，观察每个海洋格子相邻的陆地格子。

这道题的基本思路就是这样，具体的代码还有一些需要注意的细节，但和本文的主题已经联系不大。各位可以自己思考一下如何把上述思路转化为代码。

### 例题 3：岛屿的周长

**LeetCode 463. Island Perimeter** （Easy）

> 给定一个包含 0 和 1 的二维网格地图，其中 1 表示陆地，0 表示海洋。网格中的格子水平和垂直方向相连（对角线方向不相连）。整个网格被水完全包围，但其中恰好有一个岛屿（一个或多个表示陆地的格子相连组成岛屿）。
>
> 岛屿中没有“湖”（“湖” 指水域在岛屿内部且不和岛屿周围的水相连）。格子是边长为 1 的正方形。计算这个岛屿的周长。
>
> ![图片](data:image/gif;base64,iVBORw0KGgoAAAANSUhEUgAAAAEAAAABCAYAAAAfFcSJAAAADUlEQVQImWNgYGBgAAAABQABh6FO1AAAAABJRU5ErkJggg==)题目示例

实话说，这道题用 DFS 来解并不是最优的方法。对于岛屿，直接用数学的方法求周长会更容易。不过这道题是一个很好的理解 DFS 遍历过程的例题，不信你跟着我往下看。

我们再回顾一下 网格 DFS 遍历的基本框架：

```
void dfs(int[][] grid, int r, int c) {    // 判断 base case    if (!inArea(grid, r, c)) {        return;    }    // 如果这个格子不是岛屿，直接返回    if (grid[r][c] != 1) {        return;    }    grid[r][c] = 2; // 将格子标记为「已遍历过」        // 访问上、下、左、右四个相邻结点    dfs(grid, r - 1, c);    dfs(grid, r + 1, c);    dfs(grid, r, c - 1);    dfs(grid, r, c + 1);}// 判断坐标 (r, c) 是否在网格中boolean inArea(int[][] grid, int r, int c) {    return 0 <= r && r < grid.length          && 0 <= c && c < grid[0].length;}
```

可以看到，`dfs` 函数直接返回有这几种情况：

- `!inArea(grid, r, c)`，即坐标 `(r, c)` 超出了网格的范围，也就是我所说的「先污染后治理」的情况

- `grid[r][c] != 1`，即当前格子不是岛屿格子，这又分为两种情况：

- - `grid[r][c] == 0`，当前格子是海洋格子
  - `grid[r][c] == 2`，当前格子是已遍历的陆地格子

那么这些和我们岛屿的周长有什么关系呢？实际上，岛屿的周长是计算岛屿全部的「边缘」，而这些边缘就是我们在 DFS 遍历中，`dfs` 函数返回的位置。观察题目示例，我们可以将岛屿的周长中的边分为两类，如下图所示。黄色的边是与网格边界相邻的周长，而蓝色的边是与海洋格子相邻的周长。

![图片](data:image/gif;base64,iVBORw0KGgoAAAANSUhEUgAAAAEAAAABCAYAAAAfFcSJAAAADUlEQVQImWNgYGBgAAAABQABh6FO1AAAAABJRU5ErkJggg==)将岛屿周长中的边分为两类

当我们的 `dfs` 函数因为「坐标 `(r, c)` 超出网格范围」返回的时候，实际上就经过了一条黄色的边；而当函数因为「当前格子是海洋格子」返回的时候，实际上就经过了一条蓝色的边。这样，我们就把岛屿的周长跟 DFS 遍历联系起来了，我们的题解代码也呼之欲出：

```
public int islandPerimeter(int[][] grid) {    for (int r = 0; r < grid.length; r++) {        for (int c = 0; c < grid[0].length; c++) {            if (grid[r][c] == 1) {                // 题目限制只有一个岛屿，计算一个即可                return dfs(grid, r, c);            }        }    }    return 0;}int dfs(int[][] grid, int r, int c) {    // 函数因为「坐标 (r, c) 超出网格范围」返回，对应一条黄色的边    if (!inArea(grid, r, c)) {        return 1;    }    // 函数因为「当前格子是海洋格子」返回，对应一条蓝色的边    if (grid[r][c] == 0) {        return 1;    }    // 函数因为「当前格子是已遍历的陆地格子」返回，和周长没关系    if (grid[r][c] != 1) {        return 0;    }    grid[r][c] = 2;    return dfs(grid, r - 1, c)        + dfs(grid, r + 1, c)        + dfs(grid, r, c - 1)        + dfs(grid, r, c + 1);}// 判断坐标 (r, c) 是否在网格中boolean inArea(int[][] grid, int r, int c) {    return 0 <= r && r < grid.length          && 0 <= c && c < grid[0].length;}
```

## **总结**
