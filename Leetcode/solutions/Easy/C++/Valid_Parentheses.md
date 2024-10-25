# Valid Parentheses

**Platform:** LeetCode

**Problem Link:** https://leetcode.com/problems/valid-parentheses/description/

### Problem Statement:
Given a string s containing just the characters '(', ')', '{', '}', '[' and ']', determine if the input string is valid.

An input string is valid if:
1. Open brackets must be closed by the same type of brackets.
2. Open brackets must be closed in the correct order.
3. Every close bracket has a corresponding open bracket of the same type.

### Constraints:
* 1 <= s.length <= 10^4
* s consists of parentheses only '()[]{}'.

### Sample Input and Output:

**Example 1:**

Input: s = `"()"`

Output: `true`

**Example 2:**

Input: s = `"()[]{}"`

Output: `true`

**Example 3:**

Input: s = `"(]"`

Output: `false`

**Example 4:**

Input: s = `"([])"`

Output: `true`

## Solution

### Approach

1. Push each opening bracket ((, {, [) onto the stack.
2. Match Closing Brackets for each opening bracket (')', '}', ']'):
3. Check if it matches the top of the stack. If it does, pop the top.
4. If it doesn’t match or the stack is empty, return false.
5. Check: After processing all characters, return true if the stack is empty (all brackets matched), otherwise false.

### Code
```c++

class Solution {
public:
    bool isValid(string s) {
        int n=s.length();
        stack<char> ss;
        for(int i=0;i<n;i++) {
            if(ss.empty()) {
                if(s[i]=='(' || s[i]=='{' || s[i]=='[') ss.push(s[i]);
                else return false;
            }
            else if(s[i]=='(' || s[i]=='{' || s[i]=='[') ss.push(s[i]);
            else {
                if(ss.top()=='(' && s[i]==')') ss.pop();
                else if(ss.top()=='[' && s[i]==']') ss.pop();
                else if(ss.top()=='{' && s[i]=='}') ss.pop();
                else return false;
            }
        }
    }
};
```
