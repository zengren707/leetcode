题目：给定一个整数数组，找到两个不重叠的子数组，使得它们的和最大。
思路：前缀和+预处理
function maxTowSubArrays(nums) {
if (nums.length < 2) {
return 0;
}
let len = nums.length;
let leftMax = [nums[0]],
rightMax = [],
maxSum = 0;

for (let i = 1, currSum = nums[0]; i < len; i++) {
currSum = Math.max(nums[i], currSum + nums[i]);
leftMax[i] = currSum;
}
for (let j = len - 1, currSum = 0; j >= 0; j--) {
currSum = Math.max(nums[j], currSum + nums[j]);
rightMax[j] = currSum;
}
for (let i = 0; i < len - 2; i++) {
let sum = leftMax[i] + Math.max.apply(null, rightMax.slice(i + 1));
maxSum = Math.max(maxSum, sum);
}
return maxSum;
}
