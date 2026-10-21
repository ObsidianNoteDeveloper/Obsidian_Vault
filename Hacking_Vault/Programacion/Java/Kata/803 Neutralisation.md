
Given two strings comprised of `+` and `-`, return a new string which shows how the two strings interact in the following way:

- When positives and positives interact, they _remain positive_.
- When negatives and negatives interact, they _remain negative_.
- But when negatives and positives interact, they _become neutral_, and are shown as the number `0`.

```Java
public class Solution {
  public static String neutralise(String s1, String s2) {
    // Here be dragons!
    return "";
  }
}
```

The two strings will be the same length.

**Solución:**
```Java
public static String neutralise(String s1, String s2) {  
    // Here be dragons!  
    StringBuilder result = new StringBuilder();  
    for (int i = 0; i < s1.length(); i++) {  
        char c1 = s1.charAt(i);  
        char c2 = s2.charAt(i);  
  
        if ((c1 == '+') && (c2 == '+')){  
            char c3 = '+';  
            result.append(c3);  
        } else if ((c1 == '-') && (c2 == '-')) {  
            char c3 = '-';  
            result.append(c3);  
        }else {  
            char c3 = '0';  
            result.append(c3);  
        }  
    }  
    String resultFinal = result.toString();  
    return resultFinal;  
}
```




