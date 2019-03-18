## 总结

> 使用到了中序遍历，需要把计数器和返回值弄到方法外面。

## 代码

```java
    private int count=0;
    private TreeNode node;
    TreeNode KthNode(TreeNode pRoot, int k)
    {
        inOrder(pRoot,k);
        return node;
    }

    private void inOrder(TreeNode root, int k) {
        if (root == null) {
            return;
        }
        inOrder(root.left,k);
        count++;
        if (count == k) {
            node=root;
        }
        inOrder(root.right,k);
    }
