# STRINGS

### REPLACE CHARACTER


```c

i: Reydel
o: R*yd*l

#include <stdio.h>
#include <string.h>

void replaceAll(char *str, char oldChar, char newChar);

int main() {
    char str[100] = "Reydel";
    char oldChar = 'e', newChar = '*';

    printf("String before replacing: %s\n", str);
    replaceAll(str, oldChar, newChar);
    printf("String after replacing '%c' with '%c': %s\n", oldChar, newChar, str);

    return 0;
}

void replaceAll(char *str, char oldChar, char newChar) {
    while (*str != '\0') {
        if (*str == oldChar) {
            *str = newChar;
        }
        str++;
    }
}


```

### REPLACE FIRST / LAST CHARACTER

```C

FIRST

I: REYDEL
O: 4EYDEL

#include <stdio.h>
#include <string.h>

void replaceFirst(char *str, char newChar);

int main() {
    char str[100] = "REYDEL";
    char newChar = '4'; 

    printf("String before replacing: %s\n", str);

    replaceFirst(str, newChar);

    printf("String after replacing first character with '%c': %s\n", newChar, str);

    return 0;
}

void replaceFirst(char *str, char newChar) {
    if (str[0] != '\0') {
        str[0] = newChar;
    }
}

LAST

I: REYDEL
O: REYDE4

void replaceLast(char *str, char newChar) {
    size_t length = strlen(str);
    if (length > 0) {
        str[length - 1] = newChar;
    }
}

```


### REVERSE STRING

```C

#include <stdio.h>
#include <string.h>

int main() {
    char str[101];
    scanf("%s", str);
    int len = strlen(str);
    
    // Reverse the string
    for (int i = len - 1; i >= 0; i--) {
        printf("%c", str[i]);
    }
    
    return 0;
}

```

### CHECK OF BOTH STRINGS ARE ANAGRAM

```C

#include <stdio.h>
#include <string.h>

int main() {
    char str1[100001] = "DSDA"; 
    char str2[100001] = "DSAD";
    
    int len1 = strlen(str1);
    int len2 = strlen(str2);

    if (len1 != len2) {
        printf("NO\n");
        return 0;
    }
    
    // Sort both strings
    for (int i = 0; i < len1; i++) {
        for (int j = i + 1; j < len1; j++) {
            if (str1[i] > str1[j]) {
                char temp = str1[i];
                str1[i] = str1[j];
                str1[j] = temp;
            }
            if (str2[i] > str2[j]) {
                char temp = str2[i];
                str2[i] = str2[j];
                str2[j] = temp;
            }
        }
    }
    
    // Check if sorted strings are equal
    for (int i = 0; i < len1; i++) {
        if (str1[i] != str2[i]) {
            printf("NO\n");
            return 0;
        }
    }
    
    printf("YES\n");
    return 0;
}

```

### LONGEST SUBSTRING W/O REPEATING CHARACTERS

```C

Example abcabcbb 1: 3
Example bbbbb 2: 1
Example pwwkew 3: 3


#include <stdio.h>
#include <string.h>

int lengthOfLongestSubstring(char *s) {
    int n = strlen(s);
    int longest = 0;
    int start = 0;
    int charIndex[256]; // Assuming ASCII characters

    memset(charIndex, -1, sizeof(charIndex));

    for (int end = 0; end < n; end++) {
        if (charIndex[s[end]] != -1) {
            // If the character is found in the substring, update the start index
            start = (start > charIndex[s[end]] + 1) ? start : charIndex[s[end]] + 1;
        }
        // Update the character's index
        charIndex[s[end]] = end;
        // Update the length of the longest substring
        longest = (longest > end - start + 1) ? longest : end - start + 1;
    }

    return longest;
}

int main() {
    char s1[] = "abcabcbb";
    char s2[] = "bbbbb";
    char s3[] = "pwwkew";

    printf("Example 1: %d\n", lengthOfLongestSubstring(s1)); // Output: 3
    printf("Example 2: %d\n", lengthOfLongestSubstring(s2)); // Output: 1
    printf("Example 3: %d\n", lengthOfLongestSubstring(s3)); // Output: 3

    return 0;
}
```


### LONGEST PALINDROMIC SUBSTRING

```C

#include <stdio.h>
#include <string.h>

char* longestPalindrome(char* s) {
    int n = strlen(s);
    int start = 0, maxLength = 1;
    int dp[n][n]; // Create a 2D array to store the results of subproblems

    // Initialize dp[i][i] as true because single characters are palindromes
    for (int i = 0; i < n; ++i)
        dp[i][i] = 1;

    // Check for palindromes of length 2
    for (int i = 0; i < n - 1; ++i) {
        if (s[i] == s[i + 1]) {
            dp[i][i + 1] = 1;
            start = i;
            maxLength = 2;
        }
    }

    // Check for palindromes of length greater than 2
    for (int len = 3; len <= n; ++len) {
        for (int i = 0; i < n - len + 1; ++i) {
            int j = i + len - 1;
            if (s[i] == s[j] && dp[i + 1][j - 1]) {
                dp[i][j] = 1;
                start = i;
                maxLength = len;
            }
        }
    }

    // Allocate memory for the result substring
    char* result = (char*)malloc((maxLength + 1) * sizeof(char));
    strncpy(result, s + start, maxLength);
    result[maxLength] = '\0'; // Null-terminate the string

    return result;
}

int main() {
    char s1[] = "babad";
    char s2[] = "cbbd";

    printf("Example 1: %s\n", longestPalindrome(s1)); // Output: "bab" or "aba"
    printf("Example 2: %s\n", longestPalindrome(s2)); // Output: "bb"

    return 0;
}

```


### STRING TO INTEGER (ATOI)

```C

#include <stdio.h>
#include <ctype.h> // for isdigit

int myAtoi(char *s) {
    int sign = 1; // 1 for positive, -1 for negative
    int result = 0;
    int i = 0;

    // Skipping leading whitespace
    while (s[i] == ' ')
        i++;

    // Handling optional sign
    if (s[i] == '+' || s[i] == '-') {
        sign = (s[i++] == '-') ? -1 : 1;
    }

    // Processing digits
    while (isdigit(s[i])) {
        // Handling overflow/underflow
        if (result > INT_MAX / 10 || (result == INT_MAX / 10 && s[i] - '0' > INT_MAX % 10)) {
            return (sign == 1) ? INT_MAX : INT_MIN;
        }
        result = result * 10 + (s[i++] - '0');
    }

    return sign * result;
}

int main() {
    char s1[] = "42";
    char s2[] = "   -42";
    char s3[] = "4193 with words";

    printf("Example 1: %d\n", myAtoi(s1)); // Output: 42
    printf("Example 2: %d\n", myAtoi(s2)); // Output: -42
    printf("Example 3: %d\n", myAtoi(s3)); // Output: 4193

    return 0;
}

```


### REGULAR EXPRESSION MATCHING

```C

#include <stdio.h>
#include <stdbool.h>
#include <string.h>

bool isMatch(char *s, char *p) {
    if (*p == '\0') {
        return *s == '\0'; 
    }

    bool firstMatch = (*s != '\0' && (*s == *p || *p == '.'));

    if (*(p + 1) == '*') {
        return (isMatch(s, p + 2) || (firstMatch && isMatch(s + 1, p)));
    } else {
        return firstMatch && isMatch(s + 1, p + 1);
    }
}

int main() {
    char s1[] = "aa";
    char p1[] = "a";

    char s2[] = "aa";
    char p2[] = "a*";

    char s3[] = "ab";
    char p3[] = ".*";

    printf("Example 1: %s\n", isMatch(s1, p1) ? "true" : "false"); // Output: false
    printf("Example 2: %s\n", isMatch(s2, p2) ? "true" : "false"); // Output: true
    printf("Example 3: %s\n", isMatch(s3, p3) ? "true" : "false"); // Output: true

    return 0;
}

```

### INTEGER TO ROMAN TO INTEGER

```C

char* intToRoman(int num) {

    char* symbol[] = {"M", "CM", "D", "CD", "C", "XC", "L", "XL", "X", "IX", "V", "IV", "I"};
    int value[] = {1000, 900, 500, 400, 100, 90, 50, 40, 10, 9, 5, 4, 1};


    char* result = (char*)malloc(20 * sizeof(char));
    result[0] = '\0'; // Initialize the result string


    for (int i = 0; num != 0; ++i) {

        while (num >= value[i]) {
            strcat(result, symbol[i]);
            num -= value[i];
        }
    }

    return result;
}

int romanToInt(char *s) {
    int values[26];
    values['I' - 'A'] = 1;
    values['V' - 'A'] = 5;
    values['X' - 'A'] = 10;
    values['L' - 'A'] = 50;
    values['C' - 'A'] = 100;
    values['D' - 'A'] = 500;
    values['M' - 'A'] = 1000;

    int result = 0;
    int prevValue = 0;


    for (int i = 0; s[i] != '\0'; ++i) {
        int value = values[s[i] - 'A'];
 
        result += (prevValue < value) ? -prevValue : prevValue;
        prevValue = value;
    }


    result += prevValue;

    return result;
}

```


