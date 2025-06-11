题目：给定一个包含非负整数的 m x n 网格，起始点在左上角，终点在右下角，求从起点到终点的最小路径和。只能向下或向右移动
function minPathSum(grid) {
let m = grid.length, n = grid[0].length;
for (let i = 1; i < m; i++) {
grid[i][0] += grid[i - 1][0];
}
for (let j = 1; j < n; j++) {
grid[0][j] += grid[0][j - 1];
}
for (let i = 1; i < m; i++) {
for (let j = 1; j < n; j++) {
grid[i][j] += Math.min(grid[i - 1][j], grid[i][j - 1]);
}
}
return grid[m - 1][n - 1];
}

// 示例
console.log(minPathSum([[1,3,1],[1,5,1],[4,2,1]])); // 输出 7
