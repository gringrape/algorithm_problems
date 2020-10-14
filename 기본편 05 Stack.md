## 문제 개요

- 주어진 것: 괄호쌍 문자열
- 구하는 것: 주어진 문자열이 유효한 괄호쌍인지 여부

## 접근 전략

- 스택을 사용한다. 
- 괄호쌍에 있는 각각의 캐릭터에 대해서 반복을 진행한다.
- 열린괄호의 경우 스택에 넣는다.
- 닫힌괄호의 경우 스택에서 꺼낸다.
- 중간중간에 유효성 검사를 한다.

## 구현
### 1. 괄호가 열린경우
스택에 집어넣는다.

```java
public boolean isValid(String s) {
	char[] arr = s.toCharArray();
    Stack<Character> stack = new Stack<>();
    
    for (char c : arr) {
        if (c == '(' || c == '[' || c == '{') {
            stack.push();
        }
    }
}
```

### 2. 괄호가 닫힌 경우

유효성 검사를 진행한다. 거짓일 조건은 다음과 같다.

- 스택이 비어있다.
- 스택에서 꺼낸 괄호와 현재 괄호의 쌍이맞지 않는다. 

```java
public boolean isValid(String s) {
	char[] arr = s.toCharArray();
    Stack<Character> stack = new Stack<>();
    
    for (char c : arr) {
        if (c == '(' || c == '[' || c == '{') {
            stack.push();
        }
        else {
            if (c == ')' && (stack.empty() && stack.pop() != '(')) {
                return false;
            }
            if (c == '}' && (stack.empty() && stack.pop() != '{')) {
                return false;
            }
            if (c == ']' && (stack.empty() && stack.pop() != '[')) {
                return false;
            }
        }
    }
    
    return stack.empty(); // 마지막에 스택이 비었는지를 확인하여, 마지막이 열린괄호일 경우를 대비한다. 
}
```

