# Recover-Binary-Search-Tree
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
class Solution:
    def recoverTree(self, root: Optional[TreeNode]) -> None:
        """
        Do not return anything, modify root in-place instead.
        """
        if root is None:
            return 
        temp=root
        r=[]
        def add(temp,r):
            if temp is None:
                return
            add(temp.left,r)
            r.append(temp)
            add(temp.right,r)
        add(temp,r)
        n=len(r)
        r1=r2=None
        for i in range(1,n):
            if r[i].val<r[i-1].val:
                r1=r[i-1]
                break
        for i in range(n-1,0,-1):
            if r[i].val<r[i-1].val:
                r2=r[i]
                break
        r1.val,r2.val=r2.val,r1.val

        
        
