题目：在一个未排序的整数数组中，找出最长连续序列的长度。
function longestConsecutive(nums) {
if (nums.length === 0) return 0;

const numSet = new Set(nums); // 使用哈希集合存储所有元素
let longestStreak = 0;

for (let num of nums) {
// 如果 num-1 不在集合中，说明 num 是一个连续序列的起点
if (!numSet.has(num - 1)) {
let currentNum = num;
let currentStreak = 1;

      // 继续查找 num+1, num+2, ... 是否在集合中
      while (numSet.has(currentNum + 1)) {
        currentNum++;
        currentStreak++;
      }

      longestStreak = Math.max(longestStreak, currentStreak);  // 更新最长连续序列
    }

}

return longestStreak;
}
