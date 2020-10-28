## 문제링크

https://leetcode.com/problems/two-sum/submissions/



## 문제분석

### 구하는 것

- 인덱스 쌍
- 숫자 배열에서 두개의 인덱스에 해당하는 숫자를 합하면 타겟 숫자가 나온다.

### 주어진 것

- 숫자 배열
- 타겟

### 조건

- 하나의 해가 반드시 존재

## 문제접근

문제에서는 매우 큰 숫자 배열이 제시된다. 따라서 불변성을 이용한 재귀의 경우 힙 메모리 오류가 나게 된다. 그리고 시간복잡도가 n 보다 커지는 경우 문제가 발생하는 것 같다.

해쉬맵을 사용하면 문제가 생각보다 쉽게 클리어 가능하다. target- 현재값을 키로 넣어주고, 새로 들어오는 값과 비교해주면 끝이난다.

## 풀이

```javascript
var twoSum = function(nums, target) {
    let map = {};
    let indicies;
    
    for (let i = 0; i < nums.length; i++) {
        const number = nums[i];
        if (map[number] || map[number] === 0) {
            indicies = [map[number]], i];
            break;
        }
        map[target - number] = i; 
    }

    return indicies;
};
```

