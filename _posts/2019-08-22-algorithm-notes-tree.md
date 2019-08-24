---
title: Algorithm Notes | Tree and Tree Traversal
layout: post
author: Zee Nguyen
---

![Note taking](/assets/andrew-neel-cckf4TsHAuw-unsplash.jpg)

<br/>

Tree is one of the many important data structures and it has various applications in the real world. If you're familiar with web, HTML Document Object Model, the DOM, uses trees. Network routing, syntax tree in compiler, or finding out next moves in game all uses trees.

Some common uses of tree are: [*](https://en.wikipedia.org/wiki/Tree_%28data_structure%29#Common_uses)
1. Manipulate hierarchical data.
2. Make information easy to search (see tree traversal).
3. Manipulate sorted lists of data.
4. As a workflow for compositing digital images for visual effects.
5. Router algorithms

<br/>

##### What is a tree? What is a forest?

A tree is an undirected, connected and acyclic graph (meaning, there is no cycle). In a tree, a leaf is a node with degree 1 or any node that has no children. A forest contains a bunch of tree (as it is in nature).

Unlike array and linked lists, which are linear data structures, tree is a hierarchical data structure, i.e. non-linear. If we want to store information that has some hierarchy, such as file system, tree is a perfect choice. 

When a tree is organized in some special ways, it can provide moderate access/ search time (quicker than Linked List, slower than Arrays) and also insertion/ deletion time (quicker than Arrays, slower than Linked Lists).[*](https://www.geeksforgeeks.org/applications-of-tree-data-structure/). 

**Height and depth of a tree**

* The height of a tree is the length of the longest path to a leaf.
* The depth of a node is the length of the path to its root.

<br/>

##### Some properties of a tree

* A tree with n vertices has n-1 edges. 
* If one edge is added to a tree, a simple cycle is formed.
* Remove one edge from the tree will disconnect the tree.
* Any two nodes in the tree are connected by exactly one path.

<br/>

##### Binary Tree

![binary tree](https://www.cs.cmu.edu/~adamchik/15-121/lectures/Trees/pix/insertEx.bmp)

Binary tree is a special type of tree in which each node has at most 2 children – left child and right child. Typically, a binary tree can be represented by a single root node with two pointeres to its left child and its right child, which can point to further binary subtrees.

**Properties of a binary tree**

* The maximum number of nodes at level i of a binary tree is 2<sup>i-1</sup>.
* The maximum number of nodes in a binary tree of heigh h is 2<sup>h</sup> - 1.
* In a binary tree with n nodes, the minimum height (also min number of levels) is log<sub>2</sub>(n+1).
* A binary tree with L leaves has height at least log<sub>2</sub>L + 1.
* In a binary tree, the number of leaf nodes is always one more than the number of nodes with 2 children (by Handshaking Lemma).

<br/>
<hr>
<br/>

### Traverse a Binary Tree

There are a few orderings when it comes to traversing a binary tree.
1. In-order: left, root, right
2. Pre-order: root, left, right
3. Post-order: left, right, root

We can traverse a tree both recursively and iteratively.

> **Iterative solutions help us really understand what is going on while recursion is concise and beautiful.** [(csgator)](https://medium.com/leetcode-patterns/leetcode-pattern-0-iterative-traversals-on-trees-d373568eb0ec)

I tend to go for the recursive solution since it's short and elegant, but ever since I saw this quote, I set out to write solution in both ways in order to gain deeper understanding into what's going on. So let's do that with tree traversal to start.

Let's take in-order traversal as an example.

**Recursive Solution**

The recursive solution is pretty straight-forward. For in-order traversal, we go left, then root, then right. So, if the root has left child, traverse the left child. We'll keep recursing down the left child as long as it' still possible, until we're at the leaf node. A leaf node doesn't have a left child, so the code comes to the next line, which will print out this node's data. Since it's a leaf node, it doesn't have a right child neither and the recursive call stops, returning back up the tree. 

```
def in_order_traversal(root):
    if root.left:
        root.left.in_order_traversal()
    print(root.val)
    if root.right:
        root.right.in_order_traversal()
```

