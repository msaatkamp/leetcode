## Path sum II - DFS algorithm

##### [Leet code path sum II algorithm link](https://leetcode.com/problems/path-sum-ii)

This challenge is based on a node tree structure, that may be resolved by using a recursive function in order to evaluate each value in memory. 

The custom structure is provided by the written problem, and the resolution may be solved by writing a new function to handle it, or by changing the method parameters, in order to enable the function to carry tens unity values forward 

<img width="719" height="429" alt="image" src="https://github.com/user-attachments/assets/0ef3e8ea-3743-432f-8b5d-734b87a5bc1d" />

### submitted
/**
 * Definition for a binary tree node.
 * function TreeNode(val, left, right) {
 *     this.val = (val===undefined ? 0 : val)
 *     this.left = (left===undefined ? null : left)
 *     this.right = (right===undefined ? null : right)
 * }
 */
/**
 * @param {TreeNode} root
 * @param {number} targetSum
 * @return {number[][]}
 */
var pathSum = function(root, targetSum) {
    const paths = []
    const evaluatePaths = (root, visited = []) => {
        if(!root) {
            return false
        }
        const totalSum = visited.reduce((acc, cur) => acc + cur, root?.val )
        const actualPath = [ ...visited, root.val]
        if(!root.left && !root.right) {
            if(targetSum === totalSum) {
                paths.push(actualPath)
                return true
            }
            return false
        }
        const toTheLeft = root?.left && evaluatePaths(root.left, actualPath)
        const toTheRight = root?.right && evaluatePaths(root.right, actualPath)
        return toTheLeft || toTheRight
    }
    evaluatePaths(root)
    return paths
};
