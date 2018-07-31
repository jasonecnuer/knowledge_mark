# 97. 交错字符串

给定三个字符串 s1, s2, s3, 验证 s3 是否是由 s1 和 s2 交错组成的。

示例 1:
```java
输入: s1 = "aabcc", s2 = "dbbca", s3 = "aadbbcbcac"
输出: true
```

示例 2:
```java
输入: s1 = "aabcc", s2 = "dbbca", s3 = "aadbbbaccc"
输出: false
```

2. 测试类
```java
public boolean isInterleave(String s1, String s2, String s3) {
    if (s1.length() + s2.length() != s3.length()) {
        return false;
    }
    boolean[][] interleaved = new boolean[s1.length() + 1][s2.length() + 1];

    //先确定取字符串的前0个字符的情况
    interleaved[0][0] = true;

    //s2取前0个字符的情况
    for (int i = 1; i <= s1.length(); i++) {
        if (s1.charAt(i - 1) == s3.charAt(i - 1) && interleaved[i - 1][0]) {
            interleaved[i][0] = true;
        }
    }

    //s1取前0个字符的情况
    for (int j = 1; j <= s2.length(); j++) {
        if (s2.charAt(j - 1) == s3.charAt(j - 1) && interleaved[0][j - 1]) {
            interleaved[0][j] = true;
        }
    }

    //剩下的情况
    for (int i = 1; i <= s1.length(); i++) {
        for (int j = 1; j <= s2.length(); j++) {
            //情况一：当前s3的字符与当前s1的字符相匹配，则必须要满足s1当前字符（不包括当前字符）之前的字符串已匹配上
            if ((s3.charAt(i + j - 1) == s1.charAt(i - 1) && interleaved[i - 1][j]) ||
            //情况二：当前s3的字符与当前s2的字符相匹配，则必须要满足s2当前字符（不包括当前字符）之前的字符串已匹配上
                (s3.charAt(i + j - 1) == s2.charAt(j - 1) && interleaved[i][j - 1])) {
                interleaved[i][j] = true;
            }
        }
    }

    return interleaved[s1.length()][s2.length()];
}
```
