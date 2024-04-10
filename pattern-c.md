# PATTERN


## Number Pattern

### Arithmetic Sequence

```c
  for (int i = 0; i < 10; i++) {
        printf("%d ", 1 + i * 2); // 1 3 5 7 9
    }
```

### Geometric Sequence

```c
for (int i = 0; i < 5; i++) {
        printf("%d ", 1 * (int)pow(2, i)); // 1 2 4 8 16 
    }
```

### Fibonacci Seq
```c
 int first = 0, second = 1, next;

 for (int i = 0; i < 5; i++) {
        printf("%d ", firstTerm);
        next = first + second;
        first = second;
        second = next;
    }

```


### Square

```c
for(i=1; i<=N; i++)
    {
        for(j=1; j<=N; j++)
        {
            printf("*");
        }
        
        printf("\n");
    }
```

### Pascal Pattern

```c

int pascal(int n, int k) {
    int res = 1;
    if (k > n - k)
        k = n - k;
    for (int i = 0; i < k; ++i) {
        res *= (n - i);
        res /= (i + 1);
    }
    return res;
}

int n = 5; 
    
printf("Pascal's Triangle Pattern:\n");
for (int i = 0; i < n; i++) {
    for (int j = 0; j <= i; j++) {
            printf("%d ", pascal(i, j));
        }
        printf("\n");
    }

```


# STRING COMPETITIVE Q

### ZIGZAG STRING

```c

R . . . . . O . . . 
. E . . . L . C . . 
. . Y . E . . . O . 
. . . D . . . . . N 

#include <stdio.h>
#include <stdlib.h>
#include <string.h>

char** convert(char* s, int numRows, int numCols) {
    if (numRows == 1 || numRows >= strlen(s)) // If only one row or numRows is greater than the length of s
        return NULL;

    int len = strlen(s);
    char** matrix = (char**)malloc(numRows * sizeof(char*));
    for (int i = 0; i < numRows; i++) {
        matrix[i] = (char*)malloc(numCols * sizeof(char));
        memset(matrix[i], '.', numCols * sizeof(char));
    }

    int row = 0, col = 0, step = 1;
    for (int i = 0; i < len; i++) {
        matrix[row][col] = s[i];
        if (row == 0)
            step = 1;
        else if (row == numRows - 1)
            step = -1;
        row += step;
        col++;
    }

    return matrix;
}

int main() {
    char* input = "REYDELOCON";
    int numRows = 4;
    int numCols = 10; // determined based on the pattern you provided
    char** result = convert(input, numRows, numCols);
    
    // Print the matrix
    for (int i = 0; i < numRows; i++) {
        for (int j = 0; j < numCols; j++) {
            printf("%c ", result[i][j]);
        }
        printf("\n");
        free(result[i]);
    }
    free(result);

    return 0;
}


IN STRING WAY

// Zigzag conversion: REOEDLCNYO

#include <stdio.h>
#include <stdlib.h>
#include <string.h>

char* convert(char* s, int numRows) {
    if (numRows == 1 || numRows >= strlen(s)) // If only one row or numRows is greater than the length of s
        return s;

    int len = strlen(s);
    char** rows = (char**)malloc(numRows * sizeof(char*));
    for (int i = 0; i < numRows; i++) {
        rows[i] = (char*)malloc((len + 1) * sizeof(char));
        memset(rows[i], 0, (len + 1) * sizeof(char));
    }

    int row = 0, step = 1;
    for (int i = 0; i < len; i++) {
        rows[row][strlen(rows[row])] = s[i];
        if (row == 0)
            step = 1;
        else if (row == numRows - 1)
            step = -1;
        row += step;
    }

    char* result = (char*)malloc((len + 1) * sizeof(char));
    memset(result, 0, (len + 1) * sizeof(char));
    int index = 0;
    for (int i = 0; i < numRows; i++) {
        int j = 0;
        while (rows[i][j] != '\0') {
            result[index++] = rows[i][j++];
        }
    }

    for (int i = 0; i < numRows; i++) {
        free(rows[i]);
    }
    free(rows);

    return result;
}

int main() {
    char* input = "REYDELOCON";
    int numRows = 3;
    char* result = convert(input, numRows);
    printf("Zigzag conversion: %s\n", result);
    free(result);
    return 0;
}


```

### Tina Loves A

```c

astrangeanalogy
7

#include <stdio.h>
#include <string.h>

int max_length_after_deletion(char *str) {
    int len = strlen(str);
    int count_a = 0;

    // Count the occurrences of 'a' in the string
    for (int i = 0; i < len; i++) {
        if (str[i] == 'a')
            count_a++;
    }

    // If count_a is already more than half, no deletion is required
    if (count_a > len / 2)
        return len;

    // let say 4 - 1 = 3 * 2 = 6 + 1 = 7
    return (2 * (count_a - 1)) + 1;
}

int main() {
    char str[100];

    printf("Enter a string: ");
    scanf("%s", str);


    printf("Maximum length : %d\n", max_length_after_deletion(str)); 

    return 0;
}

```

### Count Decimal
```c

Decimal representation: 0.(6)

#include <stdio.h>
#include <stdlib.h>

void print_decimal_representation(int numerator, int denominator) {
    if (denominator == 0) {
        printf("Error: Division by zero\n");
        return;
    }

    printf("%d.", numerator / denominator);
    numerator %= denominator;

    if (numerator == 0) {
        printf("(0)\n");
        return;
    }

    int seen_remainders[denominator];
    for (int i = 0; i < denominator; i++) seen_remainders[i] = -1;

    numerator *= 10;
    printf("(");
    while (1) {
        printf("%d", numerator / denominator);
        seen_remainders[numerator % denominator] = numerator / denominator;

        numerator = (numerator % denominator) * 10;
        if (seen_remainders[numerator % denominator] != -1) break;
    }
    printf(")\n");
}

int main() {
    int numerator = 2;
    int denominator = 3;

    printf("Decimal: ");
    print_decimal_representation(numerator, denominator);

    return 0;
}

```
