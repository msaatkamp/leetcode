## Add two numbers algorithm

##### [Leet code add two numbers algorithm link](https://leetcode.com/problems/add-two-numbers/description/)  

This challenge is based on a linked list structure, that may be resolved by using a recursive function in order to evaluate each value in memory. 

The custom structure is provided by the written problem, and the resolution may be solved by writing a new function to handle it, or by changing the method parameters, in order to enable the function to carry tens unity values forward 

### submitted

<img width="680" height="434" alt="image" src="https://github.com/user-attachments/assets/929c8d8c-076c-4523-96d5-418678184e02" />



/**
 * Definition for singly-linked list.
 * function ListNode(val, next) {
 *     this.val = (val===undefined ? 0 : val)
 *     this.next = (next===undefined ? null : next)
 * }
 */
/**
 * @param {ListNode} l1
 * @param {ListNode} l2
 * @return {ListNode}
 */

var addTwoNumbers = function(l1, l2, carry) {
    carry = carry ?? 0 // starts with undefined, fixed to zero

    // L1 & L2 will only be null when the next value is undefined, otherwise there'll be a number
    if(l1 == null && l2 == null && carry < 1 ) {
        return null
    }

    // If the values are not null, then it should be covered with a zero
    const valA = l1?.val ? l1.val : 0
    const valB = l2?.val ? l2.val : 0

    // Total value must carry an upper value as tens, hundreds, etc. from a lower unit, due to recursive growth, as SUM
    let currentVal = valA+valB+carry

    // Evaluate how much upper units should be carried on, usually no more  than 1, as it's max sum is equal to 18
    carry = currentVal >= 10  ? 1 : 0

    // Recursive calling the function, in order to form a chain linking, built by new ListNode(firstValue, Function to evaluate chain linking to next position in the callStack, similiar as bubbling)
    return new ListNode(currentVal % 10, addTwoNumbers(l1?.next, l2?.next, carry))
};
