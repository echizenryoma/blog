# LeetCode

## 1. 基础

### 1.1 回溯

#### 1.1.1 全排列

全排列问题是回溯算法的一个典型应用。它的定义是在给定一个集合（如一个数组或字符串）的情况下，找出其中元素的所有可能的排列。


![排列树](https://www.hello-algo.com/chapter_backtracking/permutations_problem.assets/permutations_i.png)


```cpp
void dfs(vector<int>& nums, int i) {
    if (i >= nums.size()) {
        do_permutation(nums);
        return;
    }

    for (int j = i; j < nums.size(); j++) {
        swap(nums[i], nums[j]);
        dfs(nums, i + 1);
        swap(nums[j], nums[i]);
    }
}
```

LeetCode: [46. 全排列](https://leetcode.cn/problems/permutations/)

## 参考

1. [全排列问题](https://www.hello-algo.com/chapter_backtracking/permutations_problem/)
