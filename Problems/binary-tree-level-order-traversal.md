

From [Leetcode](https://leetcode.com/problems/binary-tree-level-order-traversal/)

#### 102 Binary Tree Level Order Traversal

Given a binary tree, return the *level order* traversal of its nodes' values. (ie, from left to right, level by level).

For example:
Given binary tree `[3,9,20,null,null,15,7]`,

```
    3
   / \
  9  20
    /  \
   15   7
```

return its level order traversal as:

```
[
  [3],
  [9,20],
  [15,7]
]
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
    func levelOrder(_ root: TreeNode?) -> [[Int]] {
             
        func processTree(_ node: TreeNode?, 
                         _ results: inout [Int : [Int]], _ level: Int) {
            
          	if node == nil {
                return
            }
            
            if results[level] == nil {
                results[level] = []
            }
            if let val = node?.val {
                results[level]?.append(val)    
            }            
            processTree(node?.left, &results, level+1)
            processTree(node?.right, &results, level+1)
        }
        
        var results: [Int : [Int]] = [:]
        processTree(root, &results, 0)
        let resultsB = results.sorted(by:{ $0.0 < $1.0 }).map{ $0.1 }
        return resultsB
    }
}
```

