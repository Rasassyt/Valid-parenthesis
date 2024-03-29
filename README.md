<h1> Valid-parenthesis</h1>
Leetcode problem / 20 / easy

Given a string s containing just the characters '(', ')', '{', '}', '[' and ']', determine if the input string is valid.

An input string is valid if:

    Open brackets must be closed by the same type of brackets.
    Open brackets must be closed in the correct order.
    Every close bracket has a corresponding open bracket of the same type.

 

Example 1:

Input: s = "()"
Output: true

Example 2:

Input: s = "()[]{}"
Output: true

Example 3:

Input: s = "(]"
Output: false

 

Constraints:

    1 <= s.length <= 104
    s consists of parentheses only '()[]{}'.

<h2>Code</h2>

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
        if(ss.size()==0) return true;
        return false;
    }
    
};
