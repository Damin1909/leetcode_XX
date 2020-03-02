> #### [125. 验证回文串](https://leetcode-cn.com/problems/valid-palindrome/)
>
> 难度简单161
>
> 给定一个字符串，验证它是否是回文串，只考虑字母和数字字符，可以忽略字母的大小写。
>
> **说明：**本题中，我们将空字符串定义为有效的回文串。
>
> **示例 1:**
>
> ```
> 输入: "A man, a plan, a canal: Panama"
> 输出: true
> ```
>
> **示例 2:**
>
> ```
> 输入: "race a car"
> 输出: false
> ```

```python
class Solution:
    def isPalindrome(self, s: str) -> bool:
        # 回文串，即正读和反读一样的字符串
        # 去掉字符串中的空格和字符，那么字符串是对称的
        s = "".join(filter(str.isalnum,s)).lower()
        return s == s[::-1]
```

**代码中的知识点：**

```python
filter()		# python语言中的过滤函数
str.isalnum		# 过滤函数满足的条件为，字母和数字
str.lower()		# 将字符串中的字符转为小写
str.upper()		# 将字符串中的字符转换为大写
chr()			# 将数字转为字符，其中大写字母的范围为65——90，小写字母为97——122，数字为48——57
ord()			# 将字符转为数字，与chr()相反
s == s[::-1]	# 将字符串倒转
```



对于上述问题，首先想到的是字符的replace()函数，但是当字符串中的特殊字符太多，如果仅仅使用字符串的replace()函数难以实现。我们想到了 **正则表达式**。

```pyhton
re.compile()	# 构建要匹配的模式，对于要匹配的模式，一种是找出字符串中的字母和数字；另一种是找出特殊字符作为分隔符
re.split()		# 通过特殊字符串对字符串进行分割后合并，实验发现，可能结果太多了
re.findall()	# 寻找字母和数字,匹配字符为"\w"，匹配的是单词字符[A-Za-z0-9_]
```

**生成代码：**

```python
class Solution:
    def isPalindrome(self, s: str) -> bool:
        # 回文串，即正读和反读一样的字符串
        # 去掉字符串中的空格和字符，那么字符串是对称的
        import re
        s = s.lower()
        p = re.compile("\w")
        s = "".join(p.findall(s))
        print(s)
        return s == s[::-1]
```

