##Longest Substring with At Most K Distinct Characters

	Given a string s, find the length of the longest substring T that contains at most k distinct characters.

	Have you met this question in a real interview? Yes
	Example
	For example, Given s = "eceba", k = 3,

	T is "eceb" which its length is 4.

####Challenge
O(n), n is the size of the string s.

####Tags Expand
String Two Pointers LintCode Copyright Hash Table


####思路
- 窗口型指针
- 注意以下,不是必须k distinct而是k个以下就可以,所以有了以下代码

```java
            if (map.size() == k + 1) {
                max = Math.max(max, length - 1);
            } else {
                max = Math.max(max, length);
            }
```
- 因为如果达到了k,那么就要减掉多余的一个,但是如果是因为j达到上限,说明还只是k个以下,就不用减

```java
public class Solution {
    /**
     * @param s : A string
     * @return : The length of the longest substring
     *           that contains at most k distinct characters.
     */
    public int lengthOfLongestSubstringKDistinct(String s, int k) {
        // write your code here
        if (s == null || s.length() == 0 || k <= 0) {
            return 0;
        }

        if (s.length() <= k) {
            return s.length();
        }

        HashMap<Character, Integer> map = new HashMap<Character, Integer>();
        int i = 0;
        int j = 0;
        int length = 0;
        int max = 0;

        for (i = 0; i < s.length(); i++) {
            while (map.size() <= k && j < s.length()) {
                char cur = s.charAt(j++);
                if (map.containsKey(cur)) {
                    map.put(cur, map.get(cur) + 1);
                } else {
                    map.put(cur, 1);
                }
                length++;
            }

            if (map.size() == k + 1) {
                max = Math.max(max, length - 1);
            } else {
                max = Math.max(max, length);
            }

            char deletechar = s.charAt(i);
            int times = map.get(deletechar);
            if (times == 1) {
                map.remove(deletechar);
            } else {
                map.put(deletechar, map.get(deletechar) - 1);
            }
            length--;

        }

        return max;
    }
}
```
