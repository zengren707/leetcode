问题：给定一个没有重复数字的数组，返回其所有可能的排列。

解题思路：可以使用回溯法生成所有排列。

function permute(nums) {
const result = [];
const backtrack = (path) => {
if (path.length === nums.length) {
result.push([...path]);
return;
}
for (let i = 0; i < nums.length; i++) {
if (path.includes(nums[i])) continue;
path.push(nums[i]);
backtrack(path);
path.pop();
}
};
backtrack([]);
return result;
}
