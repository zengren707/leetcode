题目描述
给定两个非负整数 num1 和 num2，以字符串形式表示，返回它们的乘积，结果也以字符串形式表示。
function multiply(num1, num2) {
const m = num1.length, n = num2.length;
const result = new Array(m + n).fill(0);

for (let i = m - 1; i >= 0; i--) {
for (let j = n - 1; j >= 0; j--) {
const product = (num1[i] - '0') \* (num2[j] - '0');
const sum = product + result[i + j + 1];
result[i + j + 1] = sum % 10;
result[i + j] += Math.floor(sum / 10);
}
}

let resultStr = result.join('');
return resultStr[0] === '0' ? resultStr.slice(1) : resultStr;
}
