## 문제. Hamming Distance

### 문제 출처

 [LeetCode 461. Hamming Distance](https://leetcode.com/problems/hamming-distance/)

### 기본 개념 -  bit 연산

**bitwise** : 두 숫자의 각 자리 bit 를 logical 하게 비교하는 연산

> &: 두 비트가 모두 1 일때 1
>
> |: 두 비트중 적어도 하나가 1 일때 1
>
> ^: 두 비트가 서로 다를때 1

**bitshift** : 비트를 오른쪽이나 왼쪽으로 밀고 나머지를 0 으로 채우는 연산 >>, <<

### 풀이 전략

해밍거리는 두개의 숫자가 bit로 표현이 되었을때, 서로 다른 bit를 비교하여 그 갯수를 세는 것이다. 서로 다른 bit 를 구하는것은 bitwise 연산자 중 exclusive OR 을 사용하고, exclusive OR 의 결과의 각자리 bit 를 모두 더하여 구한다.   

### exclusive OR

```java
class Solution {
    //...
    public static int xOR(int x, int y){
        return x ^ y;
    }
}
```

### 숫자의 각 자리 bit 출력

```java
class Solution {
	public int hammingDistance(int x, int y) {
        int xOR = x ^ y;
        for (int i = 0; i < 32; i++) {
            System.out.print(xOR >> i & 1);
        }
    }
}
```

### Hamming Distance

```java
class Solution {
	public int hammingDistance(int x, int y) {
        int xOR = x ^ y;
        int sum = 0;
        for (int i = 0; i < 32; i++) {
            sum += xOR >> i & 1;
        }
        return sum;
    }
}
```

### Hamming Distance - for 문을 사용하지 않기

```java
class Solution {
    public static int bitSum(int target, int position) {
    	if (posiiton > 31) {
            return 0;
        }
        return ((target >> position) & 1) +  bitSum(target, position + 1);
    }
    
	public int hammingDistance(int x, int y) {
 		int xOR = x ^ y;
        return bitSum(xOR, 0);
    }
}
```

## 풀이 후기

- 재귀문으로 구현할 수 있어서 좋았다. default parameter 와 같은 기능이 있어서 굳이 넣어줄 필요가 없는 인자들은 제거 할 수 없었던 것이 아쉽다.
- bit 연산자에 대해서 처음 배웠다. 쓸만한 용도를 조금 더 찾아봐야 겠다.
- 나노 계획(작은 수준의 계획-> 실행 -> 평가)을 적극적으로 수행했다. 당면한 과제가 무엇인지 정의하고 어떻게 구현할지 생각하다보니 자연스럽게 TDD 와 비슷해져갔다.