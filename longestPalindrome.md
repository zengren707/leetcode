最长回文子串（Longest Palindromic Substring）
问题：给定一个字符串，找出其中最长的回文子串。
function longestPalindrome(s) {
let longest = 0,
index = 0;
for (let i = 0; i < s.length; i++) {
let len = isPalindrome(i, s);
if (len > longest) {
longest = len;
index = i;
}
}
for (let start = index - 1, end = index + 1; ; start--, end++) {
if (s[start] == s[end] && start >= 0 && end < s.length) {
} else {
return s.substring(start + 1, end);
}
}

function isPalindrome(i, s) {
let left = i - 1,
right = i + 1;
while (left >= 0 && right < s.length && s[left] == s[right]) {
left--;
right++;
}
return right - left;
}
}
