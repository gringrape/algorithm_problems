## 문제 분석

### 구하는 것

bottom-up 방향으로 level 별 노드 값을 담은 배열.

ex) [[1, 3], [9, 20], [3]]

### 주어진 것

binary tree

### 조건

같은 레벨일때에는 왼쪽부터 오른쪽 순으로 표시한다.

## 배경지식

### BFS

- https://www.notion.so/Breadth-First-Search-97e12bf233e646508b57da6f2e68240e

## 문제풀이

### 1. 반환값 설정

```java
class Solution {
    public List<List<Integer>> levelOrderBottom(TreeNode root) {
        List<List<Integer>> ret = new ArrayList<>();
    }
}
```



### 2. 그래프를 순회하기 위한 Queue 를 생성

Queue 를 구현하고 있는 자바 클래스

https://docs.oracle.com/javase/tutorial/collections/implementations/queue.html

```java
class Solution {
    public List<List<Integer>> levelOrderBottom(TreeNode root) {
        List<List<Integer>> ret = new ArrayList<>();
        
        Queue<TreeNode> q = new LinkedList<>();
        q.offer(root);
    }
}
```



### 3. Queue 에 들어있는 요소에 대한 작업 

```java
class Solution {
    public List<List<Integer>> levelOrderBottom(TreeNode root) {
        List<List<Integer>> ret = new ArrayList<>();
        
        Queue<TreeNode> q = new LinkedList<>();
        q.offer(root);
        
        int size = q.size();
        List<Integer> level = new ArrayList<>();
        for (int i = 0; i < size; i++) {
            TreeNode node = q.poll();
            // 현재 레벨의 값에 넣기
            level.add(node.val);
            // Queue 에 다음 노드 추가하기
            if (node.left != null) {
                q.offer(node.left);
            }
            if (node.right != null) {
                q.offer(node.right);
            }
        }
    }
}
```



### 4. 모든 레벨에 대하여 반복적으로 수행하기

```java
class Solution {
    public List<List<Integer>> levelOrderBottom(TreeNode root) {
        List<List<Integer>> ret = new ArrayList<>();
        
        Queue<TreeNode> q = new LinkedList<>();
        q.offer(root);
        
        while(!q.isEmpty()) {
        	int size = q.size();
            List<Integer> level = new ArrayList<>();
            for (int i = 0; i < size; i++) {
                TreeNode node = q.poll();
                // 현재 레벨의 값에 넣기
                level.add(node.val);
                // Queue 에 다음 노드 추가하기
                if (node.left != null) {
                    q.offer(node.left);
                }
                if (node.right != null) {
                    q.offer(node.right);
                }
            }
            
            ret.add(level);
        }
        
        return ret;
    }
}
```



### 5. 역순으로 넣어주기

```java
class Solution {
    public List<List<Integer>> levelOrderBottom(TreeNode root) {
        List<List<Integer>> ret = new ArrayList<>();
        
        Queue<TreeNode> q = new LinkedList<>();
        q.offer(root);
        
        while(!q.isEmpty()) {
        	int size = q.size();
            List<Integer> level = new ArrayList<>();
            for (int i = 0; i < size; i++) {
                TreeNode node = q.poll();
                // 현재 레벨의 값에 넣기
                level.add(node.val);
                // Queue 에 다음 노드 추가하기
                if (node.left != null) {
                    q.offer(node.left);
                }
                if (node.right != null) {
                    q.offer(node.right);
                }
            }
            
            ret.add(0, level); // 새로운 레벨을 처음에 넣으므로 마지막레벨이 가장 앞에 오게된다. 
        }
        
        return ret;
    }
}
```



### 5. Edge Case 추가하기

```java
class Solution {
    public List<List<Integer>> levelOrderBottom(TreeNode root) {
        List<List<Integer>> ret = new ArrayList<>();
        
        if (root == null) {
        	return ret;    
        }
        
        Queue<TreeNode> q = new LinkedList<>();
        q.offer(root);
        
        while(!q.isEmpty()) {
        	int size = q.size();
            List<Integer> level = new ArrayList<>();
            for (int i = 0; i < size; i++) {
                TreeNode node = q.poll();
                // 현재 레벨의 값에 넣기
                level.add(node.val);
                // Queue 에 다음 노드 추가하기
                if (node.left != null) {
                    q.offer(node.left);
                }
                if (node.right != null) {
                    q.offer(node.right);
                }
            }
            
            ret.add(0, level); // 새로운 레벨을 처음에 넣으므로 마지막레벨이 가장 앞에 오게된다. 
        }
        
        return ret;
    }
}
```

## 회고

- 단순한 것부터 멘탈모델을 잡아나간다는 생각으로 진행하였다 
  - 매우 효율적이었다.
- 코드를 똑같이 따라하는 건 별로 의미있는 일은 아닌것 같다.
  - 사고 과정을 주의 깊게 관찰하자.
- 역순으로 표시하는 아이디어가 좋았다.
  - 넣어줄때 앞에다 넣어주면 가장 오래된 것이 가장 나중에 오므로 자연스럽게 역순이 구성된다. collection 에서 앞에서 넣어주는지 뒤에서 넣어주는지도 잘 생각해보아야 할 것 같다.



## 다음에 할 일

for 문을 사용하지 않고 재귀적으로 접근해서 풀어보자. 