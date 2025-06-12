给定一个整数数组，找到其中的最长重复子数组。
function findLength(A, B) {
let left = 0, right = Math.min(A.length, B.length);
let result = 0;

    // 二分查找子数组的最大长度
    while (left <= right) {
        let mid = Math.floor((left + right) / 2);

        // 检查是否存在长度为 mid 的重复子数组
        if (hasCommonSubarray(A, B, mid)) {
            result = mid; // 记录当前最长的重复子数组
            left = mid + 1; // 尝试更大的长度
        } else {
            right = mid - 1; // 尝试更小的长度
        }
    }

    return result;

}

// 辅助函数：检查长度为 mid 的重复子数组是否存在
function hasCommonSubarray(A, B, length) {
let seen = new Set();

    // 使用滚动哈希（滚动窗口）存储每个长度为 length 的子数组的哈希值
    let hash = 0, base = 101, mod = 1e9 + 7;

    // 初始化 hash 值
    for (let i = 0; i < length; i++) {
        hash = (hash * base + A[i]) % mod;
    }
    seen.add(hash);

    // 滑动窗口：检查 A 数组的所有子数组
    for (let i = 1; i <= A.length - length; i++) {
        hash = (hash * base - A[i - 1] * Math.pow(base, length) + A[i + length - 1]) % mod;
        seen.add(hash);
    }

    // 对 B 数组进行相同的处理，检查是否有重复的子数组
    hash = 0;
    for (let i = 0; i < length; i++) {
        hash = (hash * base + B[i]) % mod;
    }

    // 如果 B 数组的当前子数组的哈希值在 A 数组的子数组中出现过，说明找到了重复子数组
    if (seen.has(hash)) {
        return true;
    }

    for (let i = 1; i <= B.length - length; i++) {
        hash = (hash * base - B[i - 1] * Math.pow(base, length) + B[i + length - 1]) % mod;
        if (seen.has(hash)) {
            return true;
        }
    }

    return false;

}

// 示例使用
const A = [1, 2, 3, 2, 1];
const B = [3, 2, 1, 4, 7];
console.log(findLength(A, B)); // 输出：3
