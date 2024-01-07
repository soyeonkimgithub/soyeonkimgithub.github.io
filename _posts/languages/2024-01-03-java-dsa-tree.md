---
layout: post
title: Java DSA
categories: languages
sitemap: false
hide_last_modified: true
published: true

---
## [Java] Tree

### Tree
* full: every node either points to zero nodes or two nodes
* perfect: any level in the tree that has any nodes is completely filled all the way across
* complete: filled the tree from left to right with no gaps

### Binary search trees
* all nodes below it to the right are going to be greater than that node, everything on the left is going to be less than.
* lookup, insert, remove: O(log n)

~~~java
public class BinarySearchTree {
    Node root;

    class Node {
        int value;
        Node left;
        Node right;

        private Node(int value) {
            this.value = value;
        }
    }

    public boolean insert(int value) {
        Node newNode = new Node(value);
        if(root==null) {
            root = newNode;
            return true;
        }
        Node temp = root;

        while(true) {
            if(newNode.value == temp.value) return false;

            if(newNode.value < temp.value) {
                if (temp.left == null) {
                    temp.left = newNode;
                    return true;
                }
                temp = temp.left;
            } else {
                if(temp.right == null) {
                    temp.right = newNode;
                    return true;
                }
                temp = temp.right;
            }
        }
    }

    public boolean contains(int value) {
        Node temp = root;

        while(temp != null) {
            if(value < temp.value) {
                temp = temp.left;
            } else if(value > temp.value) {
                temp = temp.right;
            } else {
                return true;
            }
        }
        return false;
    }
}
~~~

## Binary Tree Paths

Given the root of a binary tree, return all root-to-leaf paths in any order.
A leaf is a node with no children.

~~~java
public class TreeNode{
    int val;
    TreeNode left;
    TreeNode right;
    TreeNode() {}
    TreeNode(int val) {
        this.val = val;
    }
    TreeNode(int val, TreeNode left, TreeNode right) {
        this.val = val
        this.left = left
        this.right = right
    }
} 

public List<String> binaryTreePaths(TreeNode root) {
    List<String> answer = new ArrayList<String>();
    if (root != null) searchBT(root, "", answer);
    return answer;
}
private void searchBT(TreeNode root, String path, List<String> answer) {
    if (root.left == null && root.right == null) answer.add(path + root.val);
    if (root.left != null) searchBT(root.left, path + root.val + "->", answer);
    if (root.right != null) searchBT(root.right, path + root.val + "->", answer);
}
~~~
