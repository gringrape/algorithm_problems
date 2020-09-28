## 문제 1. Generate Parenthesis



### 문제 출처

[Generate Parenthesis]: https://leetcode.com/problems/generate-parentheses/

### 기본적인 해결 전략

backtracking 은 재귀와 유사하다. 재귀 + 완료조건 체크를 backtracking 문제라고 볼 수 있다. 빈 문자열에 괄호를 하나씩 넣어가는 과정을 코드로 서술한다.  현재 시점에서 다음 시점(괄호를 하나 더 넣기)으로 넘어갈때, 유효성 검사를 해서 불필요한 연산을 줄인다.

### 초기 상태

재귀를 사용해서 해결한다. 최종함수는 가능한 문자열을 모두 갖고 있는 배열이다.

```java
class Solution {
    public List<String> generateParenthesis(int n) {
        List<String> ret = new ArrayList<>();
        process(ret); // 재귀함수를 통해서 ret 을 변화시킨다.
        return ret;
    }
}
```

### 재귀 함수의 인자 결정

문제에서 주어지는 괄호 짝의 갯수 n,

최종 결과값 ret,

현재 시점의 문자열 str,

현재 시점의 열린괄호 갯수 numOpen,

현재 시점의 닫힌괄호 갯수 numClosed,

```java
class Solution {
    public List<String> generateParenthesis(int n) {
        List<String> ret = new ArrayList<>();
        process(ret); // 재귀함수를 통해서 ret 을 변화시킨다.
        return ret;
    }
    public void process(
        int n, 
        String str, 
        int numOpen,
        int numClosed,
        List<String> ret
    ) {
        
    }
}
```
### 현재 시점에서 다음 시점으로의 상태변화

현재 시점에서 다음 시점으로 변화할때, 두가지 동작만이 가능하다. (recurse)

1. 열려있는 괄호를 넣는다.
2. 닫혀있는 괄호를 넣는다.

괄호가 가득찼을때, 바람직한 결과값에 도달했다면 함수를 종료한다. (termination check)

```java
class Solution {
    public List<String> generateParenthesis(int n) {
        List<String> ret = new ArrayList<>();
        process(ret); // 재귀함수를 통해서 ret 을 변화시킨다.
        return ret;
    }
    public void process(
        int n, 
        String str, 
        int numOpen,
        int numClosed,
        List<String> ret
    ) {
        // terminate
        
        // recurse
        process(); // add open bracket
        process(); // add closed bracket
    }
}
```

### 상태변화 시의 유효성 체크

괄호를 넣어줄때, 넣고나서도 유효한 상태가 되기 위해서는 조건이 필요하다.

1. 열린괄호를 넣고도 유효하려면, 넣기전에 열린괄호 갯수가 n 보다 작아야 한다.
2. 닫힌괄호를 넣고도 유효하려면, 넣기전에 닫힌괄호 갯수가 열린괄호갯수보다 작아야 한다.

```java
class Solution {
    public List<String> generateParenthesis(int n) {
        List<String> ret = new ArrayList<>();
        process(ret); // 재귀함수를 통해서 ret 을 변화시킨다.
        return ret;
    }
    public void process(
        int n, 
        String str, 
        int numOpen,
        int numClosed,
        List<String> ret
    ) {
        // terminate
        
        // recurse
        if (numOpen < n) {
        	process(); // add open bracket            
        }
        if (numOpen > numClosed) {
        	process(); // add closed bracket            
        }
    }
}
```

### 종료 조건 & 적절한 인자 넣기

종료시에는 열린괄호 갯수와 닫힌 괄호 갯수가 각각 괄호쌍 갯수와 같아야 한다.

```java
class Solution {
    public List<String> generateParenthesis(int n) {
        List<String> ret = new ArrayList<>();
        process(n, "", 0, 0, ret); // 재귀함수를 통해서 ret 을 변화시킨다.
        return ret;
    }
    public void process(
        int n, 
        String str, 
        int numOpen,
        int numClosed,
        List<String> ret
    ) {
        // terminate
        if (numOpen == n && numClosed == n) {
            ret.add(str);
            return;
        }
        
        // recurse
        if (numOpen < n) {
        	process(n, str + "(", numOpen + 1, numClosed, ret); // add open bracket            
        }
        if (numOpen > numClosed) {
        	process(n, str + ")", numOpen, numClosed + 1, ret); // add closed bracket            
        }
    }
}
```

## 느낀점 & 향후 과제

재귀는 기본적으로 하나의 시점에서부터 다음시점으로의 이동이라는 것을 알았다. 특정 시점의 상태는 인자를 통해 관리된다. 

재귀에 대해 생각할때 시점 이라든지, 상태라든지 하는 나만의 정제되지 않은 정의를 가지고 있다. 다음단계는 수업을 찾아보며 재귀적풀이를 체계적으로 이해하고, 용어와 모델이 머릿속에 확립될 필요가 있다. 

