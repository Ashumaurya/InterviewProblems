# Problem statement

Given an integer array nums, find the contiguous subarray (containing at least one number) which has the largest sum and return its sum.

A subarray is a contiguous part of an array.

```
Example 1:

Input: nums = [-2,1,-3,4,-1,2,1,-5,4]
Output: 6
Explanation: [4,-1,2,1] has the largest sum = 6.
```

```
Example 2:

Input: nums = [1]
Output: 1
```

```
Example 3:

Input: nums = [5,4,-1,7,8]
Output: 23
```

Constraints:

```
1 <= nums.length <= 3 * 104
-105 <= nums[i] <= 105
```

**Follow up** : If you have figured out the O(n) solution, try coding another solution using the divide and conquer approach, which is more subtle.

## Solutions

**Naive Approach (bruteforce)**

```
int maxSubArray(vector<int>& nums) {
        int result = nums[0];
        int sum = 0 ;

        for(int i = 0 ; i < nums.size() ; i++){
            sum = nums[i];
            if(sum > result){
                result = sum;
            }
            for(int j = i+1 ; j < nums.size() ; j++){
                sum = sum + nums[j];
                if(sum > result){
                    result = sum;
                }
            }
        }


        return result;

    }
```

**Optimized Approach (Dynamic Programming)**

**Kadane's Algorithm**

```
int maxSubArray(vector<int>& nums) {
        int global_maximum = nums[0];
        int local_maximum = 0;

        for(int i = 0 ; i < nums.size() ; i++){
           local_maximum += nums[i];
            if(local_maximum > global_maximum){
                global_maximum = local_maximum;
            }
            if(local_maximum < 0){
                local_maximum = 0 ;
            }
        }


        return global_maximum;

    }
```

Lets edit the code so that we also get the staring and ending index of the array

```
int maxSubArray(vector<int>& nums) {
        int global_maximum = nums[0];
        int local_maximum = 0;
        int starting_index = 0 ;
        int ending_index = 0;

        for(int i = 0 ; i < nums.size() ; i++){
           local_maximum += nums[i];
            if(local_maximum > global_maximum){
                global_maximum = local_maximum;
                end = i;

            }
            if(local_maximum < 0){
                local_maximum = 0 ;
                start = i+1;
            }
        }
         cout <<start << end <<endl;

        return global_maximum;

    }

```

References :
[LeetCode Problem Statement](https://leetcode.com/problems/maximum-subarray/)
[Wikipedia](https://en.wikipedia.org/wiki/Maximum_subarray_problem)
[Medium blog about Kadane's Algorithm](https://medium.com/@rsinghal757/kadanes-algorithm-dynamic-programming-how-and-why-does-it-work-3fd8849ed73d)
