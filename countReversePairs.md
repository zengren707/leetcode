给定一个整数数组，找到其中的所有逆序对
function countReversePairs(nums) {
// 辅助函数：用于合并两个已排序的子数组
function mergeAndCount(arr, tempArr, left, right) {
if (left === right) {
return 0;
}

    let mid = Math.floor((left + right) / 2);
    let count = 0;

    // 递归计算左半部分和右半部分的逆序对数
    count += mergeAndCount(arr, tempArr, left, mid);
    count += mergeAndCount(arr, tempArr, mid + 1, right);

    // 合并两个有序数组并计算逆序对数
    count += merge(arr, tempArr, left, mid, right);

    return count;

}

// 合并两个有序的子数组，并计算逆序对数
function merge(arr, tempArr, left, mid, right) {
let i = left;
let j = mid + 1;
let k = left;
let count = 0;

    // 合并过程
    while (i <= mid && j <= right) {
      if (arr[i] <= arr[j]) {
        tempArr[k++] = arr[i++];
      } else {
        tempArr[k++] = arr[j++];
        // 右边的元素比左边的元素小，说明从 i 到 mid 之间的所有元素都形成逆序对
        count += (mid - i + 1);
      }
    }

    // 复制剩余的元素
    while (i <= mid) {
      tempArr[k++] = arr[i++];
    }

    while (j <= right) {
      tempArr[k++] = arr[j++];
    }

    // 把合并后的临时数组拷贝回原数组
    for (let i = left; i <= right; i++) {
      arr[i] = tempArr[i];
    }

    return count;

}

let tempArr = new Array(nums.length);
return mergeAndCount(nums, tempArr, 0, nums.length - 1);
}

// 示例使用
const arr = [7, 5, 6, 4];
console.log(countReversePairs(arr)); // 输出：5
