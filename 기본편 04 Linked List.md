## 문제 개요

- 주어진 것: 두개의 정렬된 Linked List
- 구하는 것: 두개를 병합한 List



## 문제흐름

- 두 개의 리스트 (헤드: L1, L2) 에서, L1 또는 L2 둘중의 하나가 null 이 아닐때까지 계속한다.
- L1 에서 고르는 경우와 L2 에서 고르는 경우를 나눈다.
- 각 경우에 대해서 적절한 코딩을 한다.



## 문제풀이

### 1. 기본적인 케이스 설정

```javascript
var mergeTwoLists = function(l1, l2) {
    let ret = null;
    let cur = null;
    
    while() {
        // 반복할 조건
    	if () {
            // l1 에서 고를 조건
        	if () {
                // ret 가 null
            }
            else {
                // ret 가 null 이 아님
            }
        }
        else {
            // l2 에서 고를 조건
        }
    }
       
    return ret;
};
```

코딩하려는 분기를 대략적으로 나누고 시작하고 있다.



### 2. L1 을 고를 조건 구현

```javascript
var mergeTwoLists = function(l1, l2) {
    let ret = null;
    let cur = null;
    
    while(l1 !== null || l2 !== null) {
        if (l2 === null || (l1 !== null && l1.val < l2.val)) {
            // l1 에서 고르는 경우
            if (ret === null) {
                // ret 존재 x
                ret = l1;
                cur = l1;
                l1 = l1.next;
            }
            else {
                // ret 존재
                cur.next = l1;
                cur = cur.next;
                l1 = l1.next;
            }
        }
        else {
            // l2 에서 고르는 경우
        }
    }
    
    return ret;
};
```

### 3. L2 를 고를 조건 구현

```javascript
var mergeTwoLists = function(l1, l2) {
    let ret = null;
    let cur = null;
    
    while(l1 !== null || l2 !== null) {
        if (l2 === null || (l1 !== null && l1.val < l2.val)) {
            // l1 에서 고르는 경우
            if (ret === null) {
                // ret 존재 x
                ret = l1;
                cur = l1;
                l1 = l1.next;
            }
            else {
                // ret 존재
                cur.next = l1;
                cur = cur.next;
                l1 = l1.next;
            }
        }
        else {
            // l2 에서 고르는 경우
            if (ret === null) {
                ret = l2;
                cur = l2;
                l2 = l2.next;
            } 
            else {
                cur.next = l2;
                cur = cur.next;
                l2 = l2.next;
            }
        } 
    }
    
    return ret;
};
```

