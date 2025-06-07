题目描述
给定一个包含 n 个整数的数组 nums，判断 nums 中是否存在三个元素 a, b, c，使得 a + b + c = 0？请你找出所有满足条件的三元组。
function threeSum(nums) {
nums.sort((a, b) => a - b);
const result = [];

for (let i = 0; i < nums.length - 2; i++) {
if (i > 0 && nums[i] === nums[i - 1]) continue; // 去重
let left = i + 1, right = nums.length - 1;

    while (left < right) {
      const sum = nums[i] + nums[left] + nums[right];
      if (sum === 0) {
        result.push([nums[i], nums[left], nums[right]]);
        while (nums[left] === nums[left + 1]) left++;  // 去重
        while (nums[right] === nums[right - 1]) right--;  // 去重
        left++;
        right--;
      } else if (sum < 0) {
        left++;
      } else {
        right--;
      }
    }

}

return result;
}
