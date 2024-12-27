
# Example
Example 1:

Input: s = "the sky is blue"
Output: "blue is sky the"
Example 2:
------------------------------------------------
Input: s = "  hello world  "
Output: "world hello"
Explanation: Your reversed string should not contain leading or trailing spaces.
------------------------------------------------
# Example 3:

Input: s = "a good   example"
Output: "example good a"
Explanation: You need to reduce multiple spaces between two words to a single space in the reversed string.
```
class Solution {
    public String reverseWords(String s) {

        //int n=s.length();
        String trimmedString = s.trim();
        
        // Split the trimmed string into words based on one or more spaces
        String[] words = trimmedString.split("\\s+");
        
        // Reverse the order of words
        StringBuilder reversedString = new StringBuilder();
        for (int i = words.length - 1; i >= 0; i--) {
            if (i < words.length - 1) {
                reversedString.append(" ");
            }
            reversedString.append(words[i]);
        }
        
        return reversedString.toString();
        
       // return new String(sb.reverse());
        
    }
}
```