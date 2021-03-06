

From [Leetcode](https://leetcode.com/problems/same-tree/)

#### 100 - Same Tree

Given two binary trees, write a function to check if they are the same or not.

Two binary trees are considered the same if they are structurally identical and the nodes have the same value.

**Example 1:**

```
Input:     1         1
          / \       / \
         2   3     2   3

        [1,2,3],   [1,2,3]

Output: true
```

**Example 2:**

```
Input:     1         1
          /           \
         2             2

        [1,2],     [1,null,2]

Output: false
```

**Example 3:**

```
Input:     1         1
          / \       / \
         2   1     1   2

        [1,2,1],   [1,1,2]

Output: false
```



#### Resolution:

Applying preorder - depth first - traversal algorithm

```swift
/**
 * Definition for a binary tree node.
 * public class TreeNode {
 *     public var val: Int
 *     public var left: TreeNode?
 *     public var right: TreeNode?
 *     public init(_ val: Int) {
 *         self.val = val
 *         self.left = nil
 *         self.right = nil
 *     }
 * }
 */
class Solution {
    
    func compare(_ p: TreeNode?, _ q: TreeNode?) -> Bool {
        
        if (p != nil || q != nil) && (p?.val != q?.val) {
            return false
        } 
        if (p == nil && q == nil) {
            return true   
        }
        return compare(p?.left, q?.left) && compare(p?.right, q?.right)
    }
    
    func isSameTree(_ p: TreeNode?, _ q: TreeNode?) -> Bool {
        return compare(p, q)        
    }
    
}
```

