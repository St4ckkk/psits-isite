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

# STAR PATTERNS


### SQUARE STAR PATTERN

```c
    *****
   *****
  *****
 *****
*****

#include <stdio.h>


int main() {
    int i, j, N;

    // Input number of rows
    printf("Enter number of rows: ");
    scanf("%d", &N);

    // Iterate through N rows
    for(i=1; i<=N; i++)
    {
        // Print N-i spaces
        for(j=1; j<=N-i; j++)
        {
            printf(" ");
        }

        // Print i stars
        for(j=1; j<=N; j++)
        {
            printf("*");
        }

        // Move to the next line
        printf("\n");
    }

    return 0;
}

```

### HOLLOW SQUARE STAR PATTERN

```c

*****
*   *
*   *
*   *
*****

#include <stdio.h>

int main() {
    int i, j, N;

    // Input number of rows
    printf("Enter number of rows: ");
    scanf("%d", &N);

    // Iterate through N rows
    for(i=1; i<=N; i++)
    {
        // Print stars for each solid row
        if(i==1 || i==N)
        {
            for(j=1; j<=N; j++)
            {
                printf("*");
            }
        }
        else
        {
            // Print stars for hollow rows
            for(j=1; j<=N; j++)
            {
                if(j==1 || j==N)
                {
                    printf("*");
                }
                else
                {
                    printf(" ");
                }
            }
        }

        // Move to the next line
        printf("\n");
    }

    return 0;
}

```

### INVERTED HALF PYRAMID STAR PATTERN

```c

*****
****
***
**
*

#include <stdio.h>

int main() {
    int i, j, N;

    // Input number of rows
    printf("Enter number of rows: ");
    scanf("%d", &N);

    // Iterate through N rows
    for(i=N; i>=1; i--)
    {
        // Print i stars
        for(j=1; j<=i; j++)
        {
            printf("*");
        }

        // Move to the next line
        printf("\n");
    }

    return 0;
}

```

### Hollow Inverted Right Triangle Star Pattern

```c

*****
*  **
* * *
**  *
*****

#include <stdio.h>

int main() {
    int i, j, N;

    // Input number of rows
    printf("Enter number of rows: ");
    scanf("%d", &N);

    // Iterate through N rows
    for(i=N; i>=1; i--)
    {
        // Print stars for each solid row
        if(i==N || i==1)
        {
            for(j=1; j<=i; j++)
            {
                printf("*");
            }
        }
        else
        {
            // Print star for hollow rows
            for(j=1; j<=i; j++)
            {
                if(j==1 || j==i)
                {
                    printf("*");
                }
                else
                {
                    printf(" ");
                }
            }
        }

        // Move to the next line
        printf("\n");
    }

    return 0;
}

```



### HALF PYRAMID STAR PATTERN

```c

*
**
***
****
*****

#include <stdio.h>

int main() {
    int i, j, N;

    // Input number of rows
    printf("Enter number of rows: ");
    scanf("%d", &N);

    // Iterate through N rows
    for(i=1; i<=N; i++)
    {
        // Print i stars
        for(j=1; j<=i; j++)
        {
            printf("*");
        }

        // Move to the next line
        printf("\n");
    }

    return 0;
}

```

### MIRRORED HALF PYRAMID STAR PATTERN

```c

    *
   **
  ***
 ****
*****

#include <stdio.h>

int main() {
    int i, j, N;

    // Input number of rows
    printf("Enter number of rows: ");
    scanf("%d", &N);

    // Iterate through N rows
    for(i=1; i<=N; i++)
    {
        // Print N-i spaces
        for(j=1; j<=N-i; j++)
        {
            printf(" ");
        }

        // Print i stars
        for(j=1; j<=i; j++)
        {
            printf("*");
        }

        // Move to the next line
        printf("\n");
    }

    return 0;
}

```

### HOLLOW PYRAMID STAR PATTERN

```c

    *
   * *
  *   *
 *     *
*********

#include <stdio.h>

int main() {
    int i, j, N;

    // Input number of rows
    printf("Enter number of rows: ");
    scanf("%d", &N);

    // Iterate through N rows
    for(i=1; i<=N; i++)
    {
        // Print N-i spaces
        for(j=1; j<=N-i; j++)
        {
            printf(" ");
        }

        // Print stars for each solid row
        if(i==N)
        {
            for(j=1; j<=2*i-1; j++)
            {
                printf("*");
            }
        }
        else
        {
            // Print star for hollow rows
            for(j=1; j<=2*i-1; j++)
            {
                if(j==1 || j==2*i-1)
                {
                    printf("*");
                }
                else
                {
                    printf(" ");
                }
            }
        }

        // Move to the next line
        printf("\n");
    }

    return 0;
}

```

### Hollow Inverted Pyramid Star Pattern

```c

*********
 *     *
  *   *
   * *
    *

#include <stdio.h>

int main() {
    int i, j, N;

    // Input number of rows
    printf("Enter number of rows: ");
    scanf("%d", &N);

    // Iterate through N rows
    for(i=N; i>=1; i--)
    {
        // Print N-i spaces
        for(j=1; j<=N-i; j++)
        {
            printf(" ");
        }

        // Print stars for each solid row
        if(i==N)
        {
            for(j=1; j<=2*i-1; j++)
            {
                printf("*");
            }
        }
        else
        {
            // Print star for hollow rows
            for(j=1; j<=2*i-1; j++)
            {
                if(j==1 || j==2*i-1)
                {
                    printf("*");
                }
                else
                {
                    printf(" ");
                }
            }
        }

        // Move to the next line
        printf("\n");
    }

    return 0;
}

```




### PYRAMID STAR PATTERN

```c

    *
   ***
  *****
 *******
*********

#include <stdio.h>

int main() {
    int i, j, N;

    // Input number of rows
    printf("Enter number of rows: ");
    scanf("%d", &N);

    // Iterate through N rows
    for(i=1; i<=N; i++)
    {
        // Print N-i spaces
        for(j=1; j<=N-i; j++)
        {
            printf(" ");
        }

        // Print i stars
        for(j=1; j<=2*i-1; j++)
        {
            printf("*");
        }

        // Move to the next line
        printf("\n");
    }

    return 0;
}

```

### INVERTED PYRAMID STAR PATTERN

```c

*********
 *******
  *****
   ***
    *

#include <stdio.h>

int main() {
    int i, j, N;

    // Input number of rows
    printf("Enter number of rows: ");
    scanf("%d", &N);

    // Iterate through N rows
    for(i=N; i>=1; i--)
    {
        // Print N-i spaces
        for(j=1; j<=N-i; j++)
        {
            printf(" ");
        }

        // Print i stars
        for(j=1; j<=2*i-1; j++)
        {
            printf("*");
        }

        // Move to the next line
        printf("\n");
    }

    return 0;
}

```

### Diamond Star Pattern

```c

    *
   ***
  *****
 *******
*********
 *******
  *****
   ***
    *

#include <stdio.h>

int main() {
    int i, j, N;

    // Input number of rows
    printf("Enter number of rows: ");
    scanf("%d", &N);

    // Iterate through N rows
    for(i=1; i<=N; i++)
    {
        // Print N-i spaces
        for(j=1; j<=N-i; j++)
        {
            printf(" ");
        }

        // Print i stars
        for(j=1; j<=2*i-1; j++)
        {
            printf("*");
        }

        // Move to the next line
        printf("\n");
    }

    for(i=N-1; i>=1; i--)
    {
        for(j=1; j<=N-i; j++)
        {
            printf(" ");
        }
        for(j=1; j<=2*i-1; j++)
        {
            printf("*");
        }
        printf("\n");
    }

    return 0;
}

```


### Hollow Diamond Star Pattern

```c

    *
   * *
  *   *
 *     *
*       *
 *     *
  *   *
   * *
    *

#include <stdio.h>

int main() {
    int i, j, N;
    printf("Enter number of rows: ");
    scanf("%d", &N);

    for(i=1; i<=N; i++)
    {
        for(j=1; j<=N-i; j++)
        {
            printf(" ");
        }
        for(j=1; j<=2*i-1; j++)
        {
            if(j==1 || j==2*i-1)
            {
                printf("*");
            }
            else
            {
                printf(" ");
            }
        }
        printf("\n");
    }
    for(i=N-1; i>=1; i--)
    {
        for(j=1; j<=N-i; j++)
        {
            printf(" ");
        }
        for(j=1; j<=2*i-1; j++)
        {
            if(j==1 || j==2*i-1)
            {
                printf("*");
            }
            else
            {
                printf(" ");
            }
        }
        printf("\n");
    }

    return 0;
}

```

### Right Arrow Star Pattern


```c

*****
  ****
    ***
      **
        *
      **
    ***
  ****
*****


#include <stdio.h>


int main()
{
    int i, j, n;

    printf("Enter value of n : ");
    scanf("%d", &n);

    for(i=1; i<n; i++)
    {
        for(j=1; j<=(2*i-2); j++)
        {
            printf(" ");
        }

        for(j=i; j<=n; j++)
        {
            printf("*");
        }

        printf("\n");
    }

    for(i=1; i<=n; i++)
    {
        for(j=1; j<=(2*n - 2*i); j++)
        {
            printf(" ");
        }
        for(j=1; j<=i; j++)
        {
            printf("*");
        }

        printf("\n");
    }

    return 0;
}

```

### Left Arrow Star Pattern
```c

    *****
   ****
  ***
 **
*
 **
  ***
   ****
    *****

#include <stdio.h>

int main()
{
    int i, j, n;

    // Input number of rows from user
    printf("Enter value of n : ");
    scanf("%d", &n);

    // Print upper part of the arrow
    for(i=1; i<n; i++)
    {
        // Print trailing (n-rownumber) spaces
        for(j=1; j<=(n-i); j++)
        {
            printf(" ");
        }

        // Print inverted right triangle
        for(j=i; j<=n; j++)
        {
            printf("*");
        }

        printf("\n");
    }

    // Print bottom part of the arrow
    for(i=1; i<=n; i++)
    {
        // Print trailing (rownumber-1) spaces
        for(j=1; j<i; j++)
        {
            printf(" ");
        }

        // Print the right triangle
        for(j=1; j<=i; j++)
        {
            printf("*");
        }

        printf("\n");
    }

    return 0;
}

```
### X Star Pattern

```c

*       *
 *     *
  *   *
   * *
    *
   * *
  *   *
 *     *

#include <stdio.h>

int main()
{
    int i, j, N;
    int count;

    printf("Enter N: ");
    scanf("%d", &N);

    count = N * 2 - 1;

    for(i=1; i<=count; i++)
    {
        for(j=1; j<=count; j++)
        {
            if(j==i || (j==count - i + 1))
            {
                printf("*");
            }
            else
            {
                printf(" ");
            }
        }

        printf("\n");
    }

    return 0;
}

```

### 8 Star Pattern

```c

 *** 
*   *
*   *
*   *
 *** 
*   *
*   *
*   *
 *** 

#include <stdio.h>

int main()
{
    int i, j, size;

    printf("Enter size: ");
    scanf("%d", &size);

    for(i=1; i<size*2; i++)
    {
        for(j=1; j<=size; j++)
        {
            // Condition for corner and center intersection space
            if((i==1 && (j==1 || j==size)) || 
               (i==size && (j==1 || j==size)) || 
               (i==size*2-1 && (j==1 || j==size)))
            {
                printf(" ");
            }
            else if(i==1 || i==size || i==(size*2)-1 || j==1 || j==size)
            {
                printf("*");
            }
            else
            {
                printf(" ");
            }
        }

        printf("\n");
    }

    return 0;
}


```

### Heart Star Pattern with name

```c
 **   **
**** ****
**REYDEL*
 *******
  *****
   ***
    *

#include <stdio.h>
#include <string.h>
 
int main()
{
    int i, j, n;
    char name[50] = "REYDEL";
    int len;

 
    printf("Enter value of n : ");
    scanf("%d", &n);

    len = strlen(name);

    // Print upper part of the heart shape
    for(i=n/2; i<=n; i+=2)
    {
        for(j=1; j<n-i; j+=2)
        {
            printf(" ");
        }
 
        for(j=1; j<=i; j++)
        {
            printf("*");
        }
 
        for(j=1; j<=n-i; j++)
        {
            printf(" ");
        }
 
        for(j=1; j<=i; j++)
        {
            printf("*");
        }
 
        printf("\n");
    }
 
    // Prints lower triangular part of the pattern
    for(i=n; i>=1; i--)
    {
        for(j=i; j<n; j++)
        {
            printf(" ");
        }
        
        // Print the name
        if(i == n) 
        {
            for(j=1; j<=(n * 2-len)/2; j++)
            {
                printf("*");
            }   

            printf("%s", name);

            for(j=1; j<(n*2-len)/2; j++)
            {
                printf("*");
            }
        }
        else 
        {
            for(j=1; j<=(i*2)-1; j++)
            {
                printf("*");
            }
        }
 
        printf("\n");
    }
 
    return 0;
}

```

# NUMBER PATTERNS

### Number Pattern 1

```c

1
22
333
4444
55555

#include <stdio.h>

int main()
{
    int i, j, rows;

    printf("Enter number of rows: ");
    scanf("%d", &rows);

    for(i=1; i<=rows; i++)
    {
        for(j=1; j<=i; j++)
        {
            // printf("%d", i); if increment set j
        }

        printf("\n");
    }

    return 0;
}

```


### BOX NUMBER PATTERN

```c

11111
11111
11111
11111
11111

#include <stdio.h>

int main()
{
    int rows, cols, i, j;

    /* Input rows and columns from user */
    printf("Enter number of rows: ");
    scanf("%d", &rows);
    printf("Enter number of columns: ");
    scanf("%d", &cols);

    /* Iterate through rows */
    for(i=1; i<=rows; i++)
    {
        /* Iterate through columns */
        for(j=1; j<=cols; j++)
        {
            printf("1");
        }

        printf("\n");
    }

    return 0;
}

```

### NUMBER PATTERN ALTERNATE ROWS 1,0

```c
11111
00000
11111
00000
11111

#include <stdio.h>

int main()
{
    int rows, cols, i, j;

    /* Input rows and columns from user */
    printf("Enter number of rows: ");
    scanf("%d", &rows);
    printf("Enter number of columns: ");
    scanf("%d", &cols);

    for(i=1; i<=rows; i++)
    {
        for(j=1; j<=cols; j++)
        {
            // Print 1 if current row is odd
            if(i%2 == 1)
            {
                printf("1");
            }
            else
            {
                printf("0");
            }
        }

        printf("\n");
    }

    return 0;
}

```

### WRAP NUMBER PATTERN

```c
11111
10001
10001
10001
11111


#include <stdio.h>

int main()
{
    int rows, cols, i, j;

    /* Input rows and columns from user */
    printf("Enter number of rows: ");
    scanf("%d", &rows);
    printf("Enter number of columns: ");
    scanf("%d", &cols);

    for(i=1; i<=rows; i++)
    {
        for(j=1; j<=cols; j++)
        {
            /* 
             * Print 1 if its first or last row
             * Print 1 if its first or last column
             */
            if(i==1 || i==rows || j==1 || j==cols)
            {
                printf("1");
            }
            else
            {
                printf("0");
            }
        }

        printf("\n");
    }

    return 0;
}

```

### CHESS BOARD NUMBER PATTERN

```c

10101
01010
10101
01010
10101


#include <stdio.h>

int main()
{
    int rows, cols, i, j, k;

    /* Input rows and columns from user */
    printf("Enter number of rows: ");
    scanf("%d", &rows);
    printf("Enter number of columns: ");
    scanf("%d", &cols);

    k = 1;

    for(i=1; i<=rows; i++)
    {
        for(j=1; j<=cols; j++)
        {
            if(k == 1)
            {
                printf("1");
            }
            else
            {
                printf("0");
            }

            // If k = 1  then k *= -1 => -1
            // If k = -1 then k *= -1 =>  1
            k *= -1;
        }

        if(cols % 2 == 0)
        {
            k *= -1;
        }

        printf("\n");
    }

    return 0;
}

```

### CENTER 0 NUMBER PATTERN


```c

11111
11111
11011
11111
11111

#include <stdio.h>

int main()
{
    int rows, cols, i, j;
    int centerRow, centerCol;

    /* Input rows and columns from user */
    printf("Enter number of rows: ");
    scanf("%d", &rows);
    printf("Enter number of columns: ");
    scanf("%d", &cols);

    /* Find center row and column */
    centerRow = (rows + 1) / 2;
    centerCol = (cols + 1) / 2;

    for(i=1; i<=rows; i++)
    {
        for(j=1; j<=cols; j++)
        {
            if(centerCol == j && centerRow == i)
            {
                printf("0");
            }
            else if(cols%2 == 0 && centerCol+1 == j)
            {
                if(centerRow == i || (rows%2 == 0 && centerRow+1 == i))
                    printf("0");
                else
                    printf("1");
            }
            else if(rows%2 == 0 && centerRow+1 == i)
            {
                if(centerCol == j || (cols%2 == 0 && centerCol+1 == j))
                    printf("0");
                else
                    printf("1");
            }
            else
            {
                printf("1");
            }
        }

        printf("\n");
    }

    return 0;
}

```


### NUMBER PATTERN BOX TYPE 


```c

555555555
544444445
543333345
543222345
543212345
543222345
543333345
544444445
555555555


#include <stdio.h>

int main()
{
    int N, i, j;

    printf("Enter N: ");
    scanf("%d", &N);

    // First upper half of the pattern
    for(i=N; i>=1; i--)
    {
        // First inner part of upper half
        for(j=N; j>i; j--)
        {
            printf("%d", j);
        }

        // Second inner part of upper half
        for(j=1; j<=(i*2-1); j++)
        {
            printf("%d", i);
        }

        // Third inner part of upper half
        for(j=i+1; j<=N; j++)
        {
            printf("%d", j);
        }

        printf("\n");
    }

    // Second lower half of the pattern
    for(i=1; i<N; i++)
    {
        // First inner part of lower half
        for(j=N; j>i; j--)
        {
            printf("%d", j);
        }

        // Second inner part of lower half
        for(j=1; j<=(i*2-1); j++)
        {
            printf("%d", i+1);
        }

        // Third inner part of lower half
        for(j=i+1; j<=N; j++)
        {
            printf("%d", j);
        }

        printf("\n");
    }

    return 0;
}

```

### HALF DIAMOND

```c

1
121
12321
1234321
123454321
1234321
12321
121
1

#include <stdio.h>

int main()
{
    int i, j, N;

    printf("Enter rows: ");
    scanf("%d", &N);

    // Print the first upper half
    for(i=1; i<=N; i++)
    {
        for(j=1; j<=i; j++)
        {
            printf("%d", j);
        }
        for(j=i-1; j>=1; j--)
        {
            printf("%d", j);
        }

        printf("\n");
    }

    // Print the lower half of the pattern
    for(i=N-1; i>=1; i--)
    {
        for(j=1; j<=i; j++)
        {
            printf("%d", j);
        }
        for(j=i-1; j>=1; j--)
        {
            printf("%d", j);
        }

        printf("\n");
    }

    return 0;
}

```

### HALF DIAMOND WITH STAR END

```c
*
*1*
*121*
*12321*
*1234321*
*123454321*
*1234321*
*12321*
*121*
*1*
*


#include <stdio.h>

int main()
{
    int i, j, N;

    printf("Enter rows: ");
    scanf("%d", &N);

    printf("*\n");
    // Print the first upper half
    for(i=1; i<=N; i++)
    {
        printf("*");
        for(j=1; j<=i; j++)
        {
            printf("%d", j);
        }

        for(j=i-1; j>=1; j--)
        {
            printf("%d", j);
        }
        printf("*");

        printf("\n");
    }

    // Print the lower half of the pattern
    for(i=N-1; i>=1; i--)
    {
        printf("*");
        for(j=1; j<=i; j++)
        {
            printf("%d", j);
        }

        for(j=i-1; j>=1; j--)
        {
            printf("%d", j);
        }
        printf("*");

        printf("\n");
    }
    printf("*");

    return 0;
}

```

### X NUMBER PATTERN

```c

1       1
 2     2
  3   3
   4 4
    5
   4 4
  3   3
 2     2
1       1

#include <stdio.h>

int main()
{
    int i, j, N;

    printf("Enter N: ");
    scanf("%d", &N);

    // First part of the pattern
    for(i=1; i<=N; i++)
    {
        // Print trailing spaces
        for(j=1; j<i; j++)
        {
            printf(" ");
        }

        printf("%d", i);

        // Print central spacces
        for(j=1; j<=((N - i) * 2 - 1); j++)
        {
            printf(" ");
        }
        // Don't print for last row
        if(i != N)
            printf("%d", i);
        // Moves on to the next row
        printf("\n");
    }

    // Second part of the pattern
    for(i=N-1; i>=1; i--)
    {
        // Print trailing spaces
        for(j=1; j<i; j++)
        {
            printf(" ");
        }

        printf("%d", i);

        // Print central spaces
        for(j=1; j<=((N - i ) * 2 - 1); j++)
        {
            printf(" ");
        }

        printf("%d", i);

        // Move on to the next line
        printf("\n");
    }

    return 0;
}

```

### DIAMOND NUMBER PATTERN

```c

    1
   212
  32123
 4321234
543212345
 4321234
  32123
   212
    1

#include <stdio.h>

int main()
{
    int i, j, N;

    printf("Enter N: ");
    scanf("%d", &N);

    // First upper half of the pattern
    for(i=1; i<=N; i++)
    {
        // Print trailing spaces
        for(j=1; j<=N-i; j++)
        {
            printf(" ");
        }

        // Print leading numbers
        for(j=i; j>=1; j--)
        {
            printf("%d", j);
        }

        // Print trailing numbers
        for(j=2; j<=i; j++)
        {
            printf("%d", j);
        }

        // Move to the next line
        printf("\n");
    }

    // Second lower half of the pattern
    for(i=N-1; i>=1; i--)
    {
        // Print trailing spaces
        for(j=1; j<=N-i; j++)
        {
            printf(" ");
        }

        // Print leading numbers
        for(j=i; j>=1; j--)
        {
            printf("%d", j);
        }

        // Print trailing numbers
        for(j=2; j<=i; j++)
        {
            printf("%d", j);
        }

        // Move to the next line
        printf("\n");
    }

    return 0;
}

```

# STRING PATTERNS

### STRING PATTERN 1

```c

A
AB
ABC
ABCD
ABCDE

#include <stdio.h>

int main()
{
    int i, j, N;
    char str[] = "REYDEL"; // Replace with provided string
    int rows = 5; // Provided number of rows

    N = rows; 

    for(i=1; i<=N; i++)
    {
        for(j=1; j<=i; j++)
        {
            printf("%c", str[j-1]);
        }

        printf("\n");
    }

    return 0;
}

```


### STRING PATTERN 2

```c

A
BB
CCC
DDDD
EEEEE

#include <stdio.h>

int main()
{
    int i, j, N;
    char str[] = "REYDEL"; 
    int rows = 5; 

    N = rows; 

    for(i=1; i<=N; i++)
    {
        for(j=1; j<=i; j++)
        {
            printf("%c", str[i-1]); 
        }

        printf("\n");
    }

    return 0;
}

```

### STRING PATTERN 3

```c

A
BA
CBA
DCBA
EDCBA


#include <stdio.h>

int main()
{
    int i, j, N;
    char str[] = "REYDEL"; // Replace with provided string
    int rows = 5; // Provided number of rows

    N = rows; 
    for(i=1; i<=N; i++)
    {
        for(j=i; j>=1; j--)
        {
            printf("%c", str[j-1]); 
        }

        printf("\n");
    }

    return 0;
}

```

### STRING PATTERN 4

```c

A
AB
ABC
ABCD
ABCDE
ABCD
ABC
AB
A

#include <stdio.h>

int main()
{
    int i, j, N;
    char str[] = "REYDEL"; 
    int rows = 5;

    N = rows; 

    for(i=1; i<=N; i++)
    {
        for(j=1; j<=i; j++)
        {
            printf("%c", str[j-1]); 
        }

        printf("\n");
    }

    for(i=N-1; i>=1; i--)
    {
        for(j=1; j<=i; j++)
        {
            printf("%c", str[j-1]); 
        }

        printf("\n");
    }

    return 0;
}

```

### STRING PATTERN 5

```c

A
BB
CCC
DDDD
EEEEE
DDDD
CCC
BB
A

#include <stdio.h>

int main()
{
    int i, j, N;
    char str[] = "REYDEL";
    int rows = 5; 

    N = rows; 
    for(i=1; i<=N; i++)
    {
        for(j=1; j<=i; j++)
        {
            printf("%c", str[i-1]); 
        }

        printf("\n");
    }

    for(i=N-1; i>=1; i--)
    {
        for(j=1; j<=i; j++)
        {
            printf("%c", str[i-1]); 
        }

        printf("\n");
    }

    return 0;
}

```


### STRING PATTERN 6

```c

A
BA
CBA
DCBA
EDCBA
DCBA
CBA
BA
A

#include <stdio.h>

int main()
{
    int i, j, N;
    char str[] = "REYDEL"; 
    int rows = 5; 

    N = rows; 

    for(i=1; i<=N; i++)
    {
        for(j=i; j>=1; j--)
        {
            printf("%c", str[j-1]);
        }

        printf("\n");
    }

    for(i=N-1; i>=1; i--)
    {
        for(j=i; j>=1; j--)
        {
            printf("%c", str[j-1]); 
        }

        printf("\n");
    }

    return 0;
}

```

### STRING PATTERN 7

```c

A
BB
CCC
DDDD
EEEEE
DDDD
CCC
BB
A


#include <stdio.h>

int main()
{
    int i, j, N;
    char str[] = "REYDEL"; 
    int rows = 5; 

    N = rows; 

    for(i=1; i<=N; i++)
    {
        for(j=1; j<=i; j++)
        {
            printf("%c", str[i-1]); 
        }

        printf("\n");
    }

    for(i=N-1; i>=1; i--)
    {
        for(j=1; j<=i; j++)
        {
            printf("%c", str[i-1]); 
        }

        printf("\n");
    }

    return 0;
}

```

### STRING PATTERN 8

```c

A
AB
ABC
ABCD
ABCDE
ABCD
ABC
AB
A

#include <stdio.h>
#include <string.h>

int main()
{
    int i, j, N;
    char str[] = "REYDEL"; 
    int rows = 5;
    N = rows; 

    int len = strlen(str);

    for(i=1; i<=N; i++)
    {
        for(j=1; j<=i; j++)
        {
            printf("%c", str[j % len - 1]); 
        }

        printf("\n");
    }

    for(i=N-1; i>=1; i--)
    {
        for(j=1; j<=i; j++)
        {
            printf("%c", str[j % len - 1]); 
        }

        printf("\n");
    }

    return 0;
}

```

### STRING PATTERN 9

```c

A
BB
CCC
DDDD
EEEEE
DDDD
CCC
BB
A

#include <stdio.h>

int main()
{
    int i, j, N;
    char str[] = "REYDEL"; 
    int rows = 5; 

    N = rows; 

    for(i=1; i<=N; i++)
    {
        for(j=1; j<=i; j++)
        {
            printf("%c", str[i-1]); 
        }

        printf("\n");
    }

    for(i=N-1; i>=1; i--)
    {
        for(j=1; j<=i; j++)
        {
            printf("%c", str[i-1]); 
        }

        printf("\n");
    }

    return 0;
}

```

### STRING PATTERN 10

```c

A
BA
CBA
DCBA
EDCBA
DCBA
CBA
BA
A

#include <stdio.h>

int main()
{
    int i, j, N;
    char str[] = "REYDEL"; 
    int rows = 5; 

    N = rows; 

    for(i=1; i<=N; i++)
    {
        for(j=i; j>=1; j--)
        {
            printf("%c", str[j-1]); 
        }

        printf("\n");
    }

    for(i=N-1; i>=1; i--)
    {
        for(j=i; j>=1; j--)
        {
            printf("%c", str[j-1]); 
        }

        printf("\n");
    }

    return 0;
}

```

### STRING PATTERN 11

```c

A
BB
CCC
DDDD
EEEEE
DDDD
CCC
BB
A

#include <stdio.h>

int main()
{
    int i, j, N;
    char str[] = "REYDEL"; 
    int rows = 5; 

    N = rows; 

    for(i=1; i<=N; i++)
    {
        for(j=1; j<=i; j++)
        {
            printf("%c", str[i-1]); 
        }

        printf("\n");
    }

    for(i=N-1; i>=1; i--)
    {
        for(j=1; j<=i; j++)
        {
            printf("%c", str[i-1]); 
        }

        printf("\n");
    }

    return 0;
}

```

### STRING PATTERN 12

```c

A
AB
ABC
ABCD
ABCDE
ABCD
ABC
AB
A

#include <stdio.h>

int main()
{
    int i, j, N;
    char str[] = "REYDEL"; 
    int rows = 5; 

    N = rows; 

    for(i=1; i<=N; i++)
    {
        for(j=1; j<=i; j++)
        {
            printf("%c", str[j-1]); 
        }

        printf("\n");
    }

    for(i=N-1; i>=1; i--)
    {
        for(j=1; j<=i; j++)
        {
            printf("%c", str[j-1]); 
        }

        printf("\n");
    }

    return 0;
}

```


### STRING PATTERN 13

```c

A
BA
CBA
DCBA
EDCBA
DCBA
CBA
BA
A

#include <stdio.h>

int main()
{
    int i, j, N;
    char str[] = "REYDEL"; 
    int rows = 5; 

    N = rows; 

    for(i=1; i<=N; i++)
    {
        for(j=i; j>=1; j--)
        {
            printf("%c", str[j-1]); 
        }

        printf("\n");
    }

    for(i=N-1; i>=1; i--)
    {
        for(j=i; j>=1; j--)
        {
            printf("%c", str[j-1]); 
        }

        printf("\n");
    }

    return 0;
}

```

### STRING PATTERN 14

```c

A
BB
CCC
DDDD
EEEEE
DDDD
CCC
BB
A

#include <stdio.h>

int main()
{
    int i, j, N;
    char str[] = "REYDEL"; 
    int rows = 5; 

    N = rows; 

    for(i=1; i<=N; i++)
    {
        for(j=1; j<=i; j++)
        {
            printf("%c", str[i-1]); 
        }

        printf("\n");
    }

    for(i=N-1; i>=1; i--)
    {
        for(j=1; j<=i; j++)
        {
            printf("%c", str[i-1]); 
        }

        printf("\n");
    }

    return 0;
}

```

### STRING PATTERN 15

```c

A
AB
ABC
ABCD
ABCDE
ABCD
ABC
AB
A

#include <stdio.h>

int main()
{
    int i, j, N;
    char str[] = "REYDEL"; 
    int rows = 5; 

    N = rows; 

    for(i=1; i<=N; i++)
    {
        for(j=1; j<=i; j++)
        {
            printf("%c", str[j-1]); 
        }

        printf("\n");
    }

    for(i=N-1; i>=1; i--)
    {
        for(j=1; j<=i; j++)
        {
            printf("%c", str[j-1]); 
        }

        printf("\n");
    }

    return 0;
}

```

### STRING X PATTERN

```c

A       A
 B     B
  C   C
   D D
    E
   D D
  C   C
 B     B

#include <stdio.h>

int main()
{
    int i, j, N;
    char str[] = "REYDEL"; 
    int rows = 5; 

    N = rows; 

    for(i=1; i<=N; i++)
    {
        for(j=1; j<i; j++)
        {
            printf(" ");
        }

        printf("%c", str[i-1]);

        for(j=1; j<=2*(N-i)-1; j++)
        {
            printf(" ");
        }

        if(i != N)
            printf("%c", str[i-1]);

        printf("\n");
    }

    return 0;
}

```

### STRING 8 PATTERN

```c

A       A
AB     BA
ABC   CBA
ABCD DCBA
ABCDEEDCBA
ABCD DCBA
ABC   CBA
AB     BA
A       A

#include <stdio.h>

int main()
{
    int i, j, N;
    char str[] = "REYDEL"; 
    int rows = 5; 

    N = rows; 

    for(i=1; i<=N; i++)
    {
        printf("%c", str[i-1]);

        for(j=1; j<=2*(N-i); j++)
        {
            printf(" ");
        }

        if(i != 1)
            printf("%c", str[i-1]);

        printf("\n");
    }

    for(i=N-1; i>=1; i--)
    {
        printf("%c", str[i-1]);

        for(j=1; j<=2*(N-i); j++)
        {
            printf(" ");
        }

        if(i != 1)
            printf("%c", str[i-1]);

        printf("\n");
    }

    return 0;
}

```

### STRING 8 DIAMOND PATTERN

```c

     R
    RER
   REYER
  REYDYER
 REYDEDYER
REYDELEDYER
 REYDEDYER
  REYDYER
   REYER
    RER
     R


#include <stdio.h>
#include <string.h>

int main() {
    char str[] = "REYDEL"; // Replace with your string
    int len = strlen(str);
    int rows = len * 2 - 1; // Number of rows in the diamond

    for (int i = 0; i < rows; i++) {
        int spaces = i < len ? len - i - 1 : i - len + 1; // Calculate spaces

        // Print leading spaces
        for (int j = 0; j < spaces; j++) {
            printf(" ");
        }

        // Print characters in increasing order
        for (int j = 0; j < len - spaces; j++) {
            printf("%c", str[j]);
        }

        // Print characters in decreasing order
        for (int j = len - spaces - 2; j >= 0; j--) {
            printf("%c", str[j]);
        }

        printf("\n");
    }

    return 0;
}

```


```c

*****
*   *
* * *
*   *
*****

#include <stdio.h>

int main() {
    int n, i, j;
    
    printf("Enter a number: ");
    scanf("%d", &n);
    
    if(n % 2 == 0)
        n++;
        
    for(i = 0; i < n; i++) {
        for(j = 0; j < n; j++) {
            if(i == n/2 && j == n/2)
                printf("*");
            else if(i == 0 || i == n-1 || j == 0 || j == n-1)
                printf("*");
            else
                printf(" ");
        }
        printf("\n");
    }
    
    return 0;
}

```


### PLUS STAR PATTERN

```c
    +
    +
    +
    +
+++++++++
    +
    +
    +
    +

#include <stdio.h>

int main()
{
    int i, j, N;

    printf("Enter N: ");
    scanf("%d", &N);

    // Run an outer loop from 1 to N*2-1
    for(i=1; i<=(N * 2 - 1); i++)
    {
        if(i == N)
        {
            for(j=1; j<=(N * 2 - 1); j++)
            {
                printf("+");
            }
        }
        else
        {
            for(j=1; j<=N-1; j++)
            {
                printf(" ");
            }
            printf("+");
        }

        printf("\n");
    }

    return 0;
}
