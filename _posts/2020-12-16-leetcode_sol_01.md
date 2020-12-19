---
layout: post
title:  "[Java/LeetCode]1.Two Sum"
author: "Misun"
categories: [ Coding_test ]
comments: true
---

### - 문제설명
Given an array of integers nums and an integer target, return indices of the two numbers such that they add up to target.<br />

You may assume that each input would have exactly one solution, and you may not use the same element twice.<br />

You can return the answer in any order.<br />

### [제한사항]
```
2 <= nums.length <= 103
-10^9 <= nums[i] <= 10^9
-10^9 <= target <= 10^9
Only one valid answer exists.
```

### 입출력 예
#### Example 1:
```
Input: nums = [2,7,11,15], target = 9
Output: [0,1]
Output: Because nums[0] + nums[1] == 9, we return [0, 1].
```

#### Example 2:
```
Input: nums = [3,2,4], target = 6
Output: [1,2]
```

#### Example 3:
```
Input: nums = [3,3], target = 6
Output: [0,1]
```
<br />
---
영어로 된 코딩문제는 처음풀어보는거라 쉬운문제를 선택했다.<br />
무식하게 for문으로 찾아보는 방법으로 풀었는데 생각보다 느리진 않았다.<br />
<br />
Runtime: 10 ms, faster than 38.11% of Java online submissions for Two Sum.<br />
Memory Usage: 39.5 MB, less than 28.18% of Java online submissions for Two Sum.<br />

<br />

```java
class Solution {
    public int[] twoSum(int[] nums, int target) {
        
        int[] answer = new int[2];
        
        for(int i=0; i<nums.length-1; i++){
            for(int j=i+1; j<nums.length; j++){
                if(nums[i]+nums[j]==target){
                    answer[0] = i;
                    answer[1] = j;
                }
            }
        }
        
        return answer;
    }
}
```
<br />
---
<b>다른사람 풀이 참고</b>
<https://limdongjin.github.io/problemsolving/twosum.html#list%EC%9D%98-lastindexof-%EB%A9%94%EC%86%8C%EB%93%9C%EB%A1%9C-%ED%92%80%EC%96%B4%EB%B3%B4%EA%B8%B0-125ms>
<br />