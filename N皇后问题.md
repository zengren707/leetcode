function solveNQueens(n) {
const res = [];
const cols = new Set(), diag1 = new Set(), diag2 = new Set();
const board = Array(n).fill().map(() => Array(n).fill('.'));
function dfs(row) {
if (row === n) {
res.push(board.map(r => r.join('')));
return;
}
for (let c = 0; c < n; c++) {
if (cols.has(c) || diag1.has(row + c) || diag2.has(row - c)) continue;
cols.add(c); diag1.add(row + c); diag2.add(row - c);
board[row][c] = 'Q';
dfs(row + 1);
board[row][c] = '.';
cols.delete(c); diag1.delete(row + c); diag2.delete(row - c);
}
}
dfs(0);
return res;
}
// Test
console.log(solveNQueens(4));
// 输出 [[".Q..","...Q","Q...","..Q."],["..Q.","Q...","...Q",".Q.."]]
