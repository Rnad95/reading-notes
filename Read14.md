# Read 14 - Tree

## Introduction

---

Tree is a data structure represents nodes which connect with edges.

- There are many types of tree data structure such as Binary Trees, Binary Search Trees, and K-ary Trees.  

- Tree solved the problem of search, access, and remove to reach `logn` Complexity.

- Common Terminology

1. Node: which is represented the value and the reference to another node.

2. Root: the beginning of the tree.

3. K: the maximum is allowed of children number of tree.

4. Left, right: point to the reference of children in binary tree.

5. Edge: the line(link) between the parent node and the child.

6. Leaf: the node which has **no** children

7. Height: ehich is the level of the Tree

![tree](https://static.javatpoint.com/ds/images/tree2.png)

## Traversals

---

- This is Term to access all Elements in the data structure only once.

There are two categories of traversals in tree:

1. Depth First
2. Breadth First

### Depth First

- Prioritize going through the depth (height) of the tree first.

- There are three methods for depth first traversal:

1. Pre-order: root => left => right
2. In-order: left => root => right
3. Post-order: left => right => root

### Breadth First (Level Order)

- Breadth first traversal iterates through the tree by going through each level of the tree node-by-node

**The difference between Breath and depth**

![Vs](https://rhettinger.github.io/_images/depth_first_breadth_first.gif)

breadth first traversal pseudo:

![breadth](https://i.ibb.co/R2hvKkj/Screenshot-from-2022-03-24-03-41-02.png)

## Binary Tree Vs K-ary Trees

---

- Binary Search (BST), nodes are organized in a manner where all values that are smaller than the root are placed to the left, and all values that are larger than the root are placed to the right.

- K-ary Trees

In this type of tree we use K to refer to the maximum number of children that each Node is able to have.

- K-ary Trees pseudo:

![](https://i.ibb.co/rwg06gS/Screenshot-from-2022-03-24-03-43-50.png)
