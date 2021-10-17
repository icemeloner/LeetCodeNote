## 94. 二叉树的中序遍历  
给定一个二叉树的根节点 root ，返回它的中序遍历。  
### 1.递归实现  
```java
/**
 * Definition for a binary tree node.
 * public class TreeNode {
 *     int val;
 *     TreeNode left;
 *     TreeNode right;
 *     TreeNode() {}
 *     TreeNode(int val) { this.val = val; }
 *     TreeNode(int val, TreeNode left, TreeNode right) {
 *         this.val = val;
 *         this.left = left;
 *         this.right = right;
 *     }
 * }
 */
class Solution {
    public static List<Integer> inorderTraversal(TreeNode root) {
        List<Integer> res = new ArrayList<>();
        dfs(res,root);
        return res;
    }
    public static void dfs(List<Integer> res, TreeNode node){
        if(node==null) return;
        dfs(res,node.left);
        res.add(node.val);
        dfs(res,node.right);
    }
}
```
### 2.通过栈实现
```java
/**
 * Definition for a binary tree node.
 * public class TreeNode {
 *     int val;
 *     TreeNode left;
 *     TreeNode right;
 *     TreeNode() {}
 *     TreeNode(int val) { this.val = val; }
 *     TreeNode(int val, TreeNode left, TreeNode right) {
 *         this.val = val;
 *         this.left = left;
 *         this.right = right;
 *     }
 * }
 */
class Solution {
    public List<Integer> inorderTraversal(TreeNode root) {
        List<Integer> res = new ArrayList<>();
        Stack<TreeNode> stack = new Stack<>();
        while (root!=null||!stack.empty()){
            if (root!=null){
                stack.push(root);
                root = root.left;
            }else {
                TreeNode tem = stack.pop();
                res.add(tem.val);
                root = tem.right;
            }
        }
        return res;
    }
}
```
