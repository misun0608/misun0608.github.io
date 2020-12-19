---
layout: post
title:  "[Java/Codility]BinaryGap"
author: "Misun"
categories: [ Coding_test ]
comments: true
---

### - Task description
A binary gap within a positive integer N is any maximal sequence of consecutive zeros that is surrounded by ones at both ends in the binary representation of N.<br />

For example, number 9 has binary representation 1001 and contains a binary gap of length 2. The number 529 has binary representation 1000010001 and contains two binary gaps: one of length 4 and one of length 3. The number 20 has binary representation 10100 and contains one binary gap of length 1. The number 15 has binary representation 1111 and has no binary gaps. The number 32 has binary representation 100000 and has no binary gaps.<br />

Write a function:<br />

class Solution { public int solution(int N); }<br />

that, given a positive integer N, returns the length of its longest binary gap. The function should return 0 if N doesn't contain a binary gap.<br />

For example, given N = 1041 the function should return 5, because N has binary representation 10000010001 and so its longest binary gap is of length 5. Given N = 32 the function should return 0, because N has binary representation '100000' and thus no binary gaps.<br />

Write an efficient algorithm for the following assumptions:<br />

N is an integer within the range [1..2,147,483,647].<br /><br />
Copyright 2009–2020 by Codility Limited. All Rights Reserved. Unauthorized copying, publication or disclosure prohibited.<br />

<br />
---
10진수를 2진수를 변환하여서 1~1사이에서 가장 높은 0의 개수의 수를 구하면 되는 문제이다.
<br />

<br />


<br />

```java
import java.util.ArrayList;

class Solution {
    public int solution(int N) {
        // 2진법으로 변환하고 
        // 1과 1 사이의 0의 갯수가 binary gap

        ArrayList<Integer> list = new ArrayList<>();

        int i=0;

        // 2진법으로 변환
        while(N>0){
            list.add(N%2);
            N /= 2;
            i++;
        }

        i--;

        int cnt=0;
        int max=0;

        for(int j=i; j>=0; j--){
            if(list.get(j)==1){
                max = maxGap(cnt,max);
                cnt = 0;
            }else{
                cnt++;
            }
        }
        return max;
    }

    private static int maxGap(int cnt,int max){
        if(max<cnt){
            return cnt;
        }
        return max;
    }
}
```
<br />
---
<b>다른사람 풀이 참고</b>
<https://github.com/DavidHerBet/java-codility/blob/master/src/main/java/com/dherbet/codility/lesson1/BinaryGap.java>
<br />