# Maximum-Product-of-Splitted-Binary-Tree

Given the root of a binary tree, split the binary tree into two subtrees by removing one edge such that the product of the sums of the subtrees is maximized.
Return the maximum product of the sums of the two subtrees. Since the answer may be too large, return it modulo 109 + 7.
Note that you need to maximize the answer before taking the mod and not after taking it.

# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
class Solution:

    def maxProduct(self, root: Optional[TreeNode]) -> int:
        ans, total=-inf, 0
        def dfs(root):
            nonlocal ans, total
            if not root: return 0
            Sum=root.val+dfs(root.left)+dfs(root.right)
            ans=max(ans, (total-Sum)*Sum)
            return Sum
        total=dfs(root)
        dfs(root)
        return ans%(10**9+7)
               

 
