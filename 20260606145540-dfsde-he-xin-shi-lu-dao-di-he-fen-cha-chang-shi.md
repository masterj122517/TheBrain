# DFS的核心是一路到底和分叉尝试

Tags: #algorithm 

---

DFS的原理实际上很简单，选择一个路径，一直往下执行，碰到边界条件调用上层，进入别的条件

所以我们就能得到以下code

```c

void dfs_combination(int* candidates, int candidates_size, int target, int start_index, int* path, int path_len)
{

  if (target == 0) {
    printf("there is %d combination\n", path_len);
    printf("They are: \n");
    for (int i = 0; i < path_len; i++) {
      printf("%d\n", path[i]);
    }
    return;
  }

  if (target < 0) {
    // means sum is bigger than target
    return;
  }

  for (int i = start_index; i < candidates_size; i++) {

    path[path_len] = candidates[i];
    dfs_combination(candidates, candidates_size, target - candidates[i], i, path, path_len + 1);
  }
}

/**
 * 问题 2：岛屿数量（二维网格）
 * @param grid : 二维网格指针（假设固定最大维度，或在 main 里定义）
 * @param r : 当前行坐标
 * @param c : 当前列坐标
 * @param max_r : 总行数
 * @param max_c : 总列数
 */
void dfs_island(char** grid, int r, int c, int max_r, int max_c)
{
  if (r < 0 || r >= max_r || c < 0 || c >= max_c || grid[r][c] == '0') {
    return;
  }

  if (grid[r][c] == 0)
    return;

  grid[r][c] = '0';
  dfs_island(grid, r + 1, c, max_r, max_c);
  dfs_island(grid, r - 1, c, max_r, max_c);
  dfs_island(grid, r, c + 1, max_r, max_c);
  dfs_island(grid, r, c - 1, max_r, max_c);
}

/**
 * 问题 3：二叉树最大深度（树形态）
 * @param root : 当前树的节点指针
 * @return : 返回当前节点向下的最大深度
 */
// it's like a stack , 先进后出
int dfs_tree_depth(TreeNode* root)
{
  if (root == NULL)
    return 0;

  int left_depth = dfs_tree_depth(root->left);
  int right_depth = dfs_tree_depth(root->right);

  return (left_depth > right_depth ? left_depth : right_depth) + 1;
}
```







## References
-
