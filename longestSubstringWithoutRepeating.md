### [Longest substring without repeating characters](https://leetcode.com/problems/longest-substring-without-repeating-characters/)

#### Sliding window solution is suggested

For resolving this problem, you want to aim into "sliding" a range of values from an index that keep track of last repeated value, as the left reference for the window, and another one, to keep track of the current value, as the right side reference.

In order to evaluate the total numbers, you can calculate the difference, from right - left and plus one that represent the "actual" value 

This result could be improved, but I'll keep it like this to make it easier to read and comprehend

<img width="624" height="434" alt="image" src="https://github.com/user-attachments/assets/3188f723-0c1d-478e-aeac-3474d2dcbeb7" />


/**
 * @param {string} s
 * @return {number}
 */
var lengthOfLongestSubstring = function(s) {  
    let longestString = 0  
    let charMap = {}  
    let lastSafe = 0  
  
    for (let i=0; i < s.length; i++) {  
        if(s[i] in charMap) {  
            lastSafe = Math.max(lastSafe, charMap[s[i]]+1)  
        }  
        charMap[s[i]] = i;  
        // window size equal reference - lastSafe position +actual  
        longestString = Math.max(longestString, (i-lastSafe)+1);  
    }  
  
    return longestString;  
};    
