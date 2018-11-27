## Palindrome Number

#### 描述： 
判断一个数字是否是回文，不可以用额外的空间。

#### 分析： 
题目的初衷是不想答题者转换成字符串再判断是否是回文。可是即使不用字符串，也不可能完全做到不用额外的空间的，还不如直接明说了限制。 
另外，负数，0 结尾的数字，是无论如何也不会成为回文的。

#### 思路： 
可以先把数字逆序，再比较原数字和逆序后的数字是否相同，相同则是回文。 
但是如果完全逆序则有可能导致overflow，所以只能逆序半截数字，前半截与后半截相同，则是回文。

比如： 
1221 逆序半截就成了 1221 -> [12]–[12]。 
12321 逆序半截就成了 12321 ->[12]–[123]。

1221 的具体流程是： 
1，1221 % 10 = 1; 得到末位 1，新数字为 1。 
2，然后把原数字 1221 的末尾去掉，1221 / 10 = 122，原数字为122。 
重复第 1，2 步的流程： 
1，122 % 10 = 2；得到末位 2，新数字为 12。 
2，然后把原数字 122 的末尾去掉，122 / 10 = 12，原数字为12。

12321 的具体流程是： 
1，12321 % 10 = 1; 得到末位 1，新数字为 1。 
2，然后把原数字 1221 的末尾去掉，12321 / 10 = 1232，原数字为1232。 
重复第 1，2 步的流程： 
1，1232 % 10 = 2；得到末位 2，新数字为 12。 
2，然后把原数字 1232 的末尾去掉，1232 / 10 = 123，原数字为123。

什么时候这个循环结束？ 
原数字每次减 1 位，新数字每次加 1 位，所以当新数字大于原数字时，就达到中位了，也就是反转了半截了。

#### 实现：
``` C#
public class Solution
{
    public bool IsPalindrome(int x)
    {
        if (x < 0 || (x % 10 == 0 && x != 0))
        {
            return false;
        }

        int revertedNumber = 0;
        while (x > revertedNumber)
        {
            revertedNumber = revertedNumber * 10 + x % 10;
            x /= 10;
        }

        //偶数位则完全相等，奇数位则去末尾位后相待。
        return x == revertedNumber || x == revertedNumber / 10;
    }
}
```