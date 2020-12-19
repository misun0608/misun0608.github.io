---
layout: post
title:  "[Java/Codility]OddOccurrencesInArray"
author: "Misun"
categories: [ Coding_test ]
comments: true
---

### - Task description
A non-empty array A consisting of N integers is given. The array contains an odd number of elements, and each element of the array can be paired with another element that has the same value, except for one element that is left unpaired.<br>
<br>
For example, in array A such that:<br>
<br>
  A[0] = 9  A[1] = 3  A[2] = 9<br>
  A[3] = 3  A[4] = 9  A[5] = 7<br>
  A[6] = 9<br>
the elements at indexes 0 and 2 have value 9,<br>
the elements at indexes 1 and 3 have value 3,<br>
the elements at indexes 4 and 6 have value 9,<br>
the element at index 5 has value 7 and is unpaired.<br>
Write a function:<br>

class Solution { public int solution(int[] A); }<br>

that, given an array A consisting of N integers fulfilling the above conditions, returns the value of the unpaired element.<br>
<br>
For example, given array A such that:<br>

  A[0] = 9  A[1] = 3  A[2] = 9<br>
  A[3] = 3  A[4] = 9  A[5] = 7<br>
  A[6] = 9<br>
the function should return 7, as explained in the example above.<br>

Write an efficient algorithm for the following assumptions:<br>

N is an odd integer within the range [1..1,000,000];<br>
each element of array A is an integer within the range [1..1,000,000,000];<br>
all but one of the values in A occur an even number of times.<br>
<br>
Copyright 2009–2020 by Codility Limited. All Rights Reserved. Unauthorized copying, publication or disclosure prohibited.<br>

<br />
---
Arrays.sort로 오름차순으로 정렬해서 짝수 index중에 index+1가 다른 값을 리턴하려고 했다. 그런데 런타임오류가 나서 실패^^<br>
그래서 다른 사람 풀이를 찾아보았다. XOR이나 HashSet을 이용할 수 있었다.<br>
<br />

### [XOR 풀이] 

```
- ^연산(XOR연산)
 -> 양쪽 비트가 서로 다른 비트면 1, 아니면 0의 결과를 낸다. (10진수로 반환한다)
 ex) 9(1001) ^ 15(1111) = 6(0110)
```
0으로 처음에 초기화해서 0000으로 시작해서 XOR 연산을 계속 진행하면<br>
결국 겹치지않는 수 결과만 남게 된다.

```java
class Solution {
    public int solution(int[] A) {
        int answer = 0;
        
        for(int num : A) {
            answer ^= num; // answer = answer ^ num;  a = a + 1 == a += 1;
        }
        return answer;
    }
}
```


<br />

---

### [HashSet 풀이] 

Set은 순서의 의미가 없지만 Data를 중복해서 포함할 수 없다.<br>
이 특성을 이용해서 문제를 풀 수도 있다. <br>

```java
class Solution {
    public int solution(int[] A){
        Set<Integer> set = new HashSet<>();

        for(int i : A){
            if(set.contains(i)){
                set.remove(i);
            }else{
                set.add(i);
            }
        }
        return set.iterator().next();
    }
}

```

<b>출처</b>
<https://hojak99.tistory.com/314>
<br />