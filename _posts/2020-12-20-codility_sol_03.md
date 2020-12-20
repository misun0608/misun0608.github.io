---
layout: post
title:  "[Java/Codility]CyclicRotation"
author: "Misun"
categories: [ Coding_test ]
comments: true
---

### - Task description
An array A consisting of N integers is given. Rotation of the array means that each element is shifted right by one index, and the last element of the array is moved to the first place. For example, the rotation of array A = [3, 8, 9, 7, 6] is [6, 3, 8, 9, 7] (elements are shifted right by one index and 6 is moved to the first place).
<br>
The goal is to rotate array A K times; that is, each element of A will be shifted to the right K times.
<br>
Write a function:
<br>
class Solution { public int[] solution(int[] A, int K); }
<br>
that, given an array A consisting of N integers and an integer K, returns the array A rotated K times.
<br>
For example, given
<br>
    A = [3, 8, 9, 7, 6]<br>
    K = 3<br>
the function should return [9, 7, 6, 3, 8]. Three rotations were made:
<br>
    [3, 8, 9, 7, 6] -> [6, 3, 8, 9, 7]<br>
    [6, 3, 8, 9, 7] -> [7, 6, 3, 8, 9]<br>
    [7, 6, 3, 8, 9] -> [9, 7, 6, 3, 8]<br>
For another example, given
<br>
    A = [0, 0, 0]<br>
    K = 1<br>
the function should return [0, 0, 0]
<br>
Given
<br>
    A = [1, 2, 3, 4]<br>
    K = 4<br>
the function should return [1, 2, 3, 4]
<br>
Assume that:
<br>
N and K are integers within the range [0..100];<br>
each element of array A is an integer within the range [−1,000..1,000].<br>
In your solution, focus on correctness. The performance of your solution will not be the focus of the assessment.<br>
<br>
<br>
Copyright 2009–2020 by Codility Limited. All Rights Reserved. Unauthorized copying, publication or disclosure prohibited.

<br />
---
간단한 문제인데 index를 answer와 A를 바꿔적어서 좀 헤맸다.<br>
그리고 배열이 빈거에 대한 처리도 해줘야했다.
<br />

<br />


<br />

```java
class Solution {
    public int[] solution(int[] A, int K) {
       int len = A.length;
       
        // empty일때 처리
        if(len == 0){
            return A;
        }

       // K가 A의 길이보다 클 경우 무의미한 회전을 반복하는걸 막기 위해
       int RNum = K % len;
       
       int[] answer = new int[len];
       
       if(RNum == 0) {
          return A;
       }
       
       for(int i=0; i<len; i++) {
          answer[(i+RNum)%len] = A[i];
       }
        return answer;
    }
}
```
<br />
---
<b>다른사람 풀이 참고</b>
<https://stroot.tistory.com/86>
<br />