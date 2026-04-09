[Binary tree inorder traversal](https://leetcode.com/problems/binary-tree-inorder-traversal/description/)


<img width="755" height="482" alt="image" src="https://github.com/user-attachments/assets/ad03fd4d-89ee-4643-b5a8-a5e5a311d5fd" />

Given the root of a binary tree, return the inorder traversal of its nodes' values.

Example 1:

Input: root = [1,null,2,3]

Output: [1,3,2]

Explanation:



Example 2:

Input: root = [1,2,3,4,5,null,8,null,null,6,7,9]

Output: [4,2,6,5,7,1,3,9,8]

Explanation:



Example 3:

Input: root = []

Output: []

Example 4:

Input: root = [1]

Output: [1]

 

Constraints:

The number of nodes in the tree is in the range [0, 100].
-100 <= Node.val <= 100
 

var inorderTraversal = function(root) {    
    const evaluatePaths = (node, visited = []) => {
        if(!node) {
            return []
        }

        // Se for folha, inclui o valor do nó
        if(!node.left && !node.right) {
            return [...visited, node?.val ]
        }

        /*
        * 1 - Preciso percorrer toda a árvore
        * 2 - Qual direção vem primeiro? (x) Esquerda ( ) direita
        * 3 - Em qual momento incremento a lista de nós visitados? ( ) antes de stackar ( ) antes de avaliar os nós a esquerda 
        (x) após avaliar os nós esquerda ( ) após avaliar os nós a direita
        */
        //---------NEM RODA SE FOR FOLHA-------------------//
        const toTheLeft = node?.left ? evaluatePaths(node.left, visited) : visited

        // Finalizada a leitura da pilha criada pela chamada de funções que avaliam nós a esquerda, adicionamos o nó atual (da esquerda pra direita)
        visited = [...toTheLeft, node?.val]

        // Avalia possíveis caminhos a esquerda, dos nós a direita
        const toTheRight = node?.right ? evaluatePaths(node.right, visited) : visited
        
        return toTheRight
    }


    return evaluatePaths(root) 
};
