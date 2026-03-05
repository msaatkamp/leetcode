# Brief explanation

##### The two sum challenge objective is to find a solution avoiding running the given set twice. 

I've created a reference for the numbers that are the answer for past numbers, and kept record for future validation and result presentation, by using a map that holds the index of the number that combined, result in the target. 

@param {number[]} nums  
@param {number} target  
@return {number[]}  

```
 var twoSum = function(nums, target) {  
    let answer = []  
    let answerFound = false  
    let i = 0;  
    const resultsMap = {}  
    const duplicatedNums = [...nums]  
    
    while(i < nums.length && !answerFound) {
        const actual = nums[i]
        const result = target - actual
      
        if(actual in resultsMap) {
            answerFound = true
            answer = [resultsMap[actual], i]
        } else {
            resultsMap[result] = i
        }

        i++;
    }
    return answer
};
```
    

