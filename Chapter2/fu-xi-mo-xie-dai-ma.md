# 需定期默写复习的基础代码

## String

#### Reverse word Order

```java
public String reverseWord(String str) {
    if (str == null || str.length() == 0) return str;

}
```

#### KMP

## Binary Tree

#### PreOrder Traverse \(Iterative\)

#### InOrder Traverse \(Iterative\)

#### PostOrder Traverse \(Iterative\)

#### Delete a Node in BST

```java
public TreeNode deleteNode(TreeNode root, int target) {
    if (root == null) return null;
    // search for target node 
    if (root.val > target) {
        root.left = delete(root.left, target);
        return root;
    } else if (root.val < target) {
        root.right = delete(root.right, target);
        return root;
    }
    // case 1. target node's left and right child node are null, return null
    // case 2. one of target node's child node is null, return the child node which is not null
    // case 3. If both left and right child node are not null, replace root node with smallest node in right subtree or largest node in left subtree, delete the smallest/largest node from right/left subtree 
    if (root.left == null && root.right == null) {
        return null;
    } else if (root.left == null || root.right == null) {
        return root.left != null ? root.left : root.right;
    } else {
        int smallest = findSmallest(root.right);
        root.val = smallest;
        root.right = deleteNode(root.right, smallest);
        return root;
    }
}
private int findSmallest(TreeNode root) {
    while (root.left != null) {
        root = root.left;
    }
    return root;
}
```

## LinkedList

#### Reverse a LinkedList \(Three Methods\)

#### Reverse LinedList in K-Groups

## Graph

#### Topological Sort \(BFS + DFS\)

## Union Find

#### Path Compression & Union by Rank

```java
class UnionFind {
    int[] parent;
    int[] rank;
    public UnionFind() {
        for (int i = 0; i < )
    }
```

## Trie



