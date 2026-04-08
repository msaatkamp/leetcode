## Path sum - DFS algorithm

##### [Leet code path sum algorithm link](https://leetcode.com/problems/path-sum)

This challenge is based on a node tree structure, that may be resolved by using a recursive function in order to evaluate each value in memory. 

The custom structure is provided by the written problem, and the resolution may be solved by writing a new function to handle it, or by changing the method parameters, in order to enable the function to carry tens unity values forward 

<img width="707" height="715" alt="image" src="https://github.com/user-attachments/assets/500d411a-f74e-42ff-8187-1e719ab90423" />


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
 * @return {boolean}
 */

 // O objetivo do algoritimo é avaliar se é possível encontrar uma soma total igual ao segundo parametro, percorrendo um caminho da raiz até o node "folha"
var hasPathSum = function(root, targetSum) {
    const evaluatePath = (root, acc = 0) => {
        acc = root?.val + acc
        if(!root?.left && !root?.right) { 
            // If there is no negative values in the graph we could write an early return like acc > targetSum 
            if(acc == targetSum) {
                return true
            }
            return false
        }

        let esquerda = root?.left ? evaluatePath(root.left, acc) : false
        let direita = root?.right ? evaluatePath(root.right, acc) : false
            
        return esquerda || direita
    }
    return evaluatePath(root)
};
