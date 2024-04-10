# Previous PSITS


### check prime number
```c
#include stdio, stdbool, math


bool is_prime(int num) {
    if (num <= 1) {
        return false;
    }
    int limit = sqrt(num);
    for (int i = 2; i <= limit; i++) {
        if (num % i == 0) {
            return false;
        }
    }
    return true;
}

 int num = 11;
    if (is_prime(num)) {
        printf("%d is a prime number\n", num);
    } else {
        printf("%d is not a prime number\n", num);
    }


```


### Largest number

```c

int max(int arr[], int size) {
    int max_value = arr[0]; // set the first val pina ka largest
    for (int i = 1; i < size; i++) {
        if (arr[i] > max_value) {
            max_value = arr[i]; // update if naay makita na largest
        }
    }
    return max_value;
}

int numbers[] = {5, 4, 2, 5, 10};
int size = sizeof(numbers) / sizeof(numbers[0]);
printf("%d\n", max(numbers, size)); 

```

### Swiper Swapper

```c

void rotateLeft(int arr[], int size) {
    int popNumber = arr[0];
    for (int i = 0; i < size - 1; i++) {
        arr[i] = arr[i + 1];
    }
    arr[size - 1] = popNumber;
}

int numbers[] = {8321, 9321, 7, 5};
int size = sizeof(numbers) / sizeof(numbers[0]);

rotateLeft(numbers, size);

for (int i = 0; i < size; i++) {
    printf("%d ", numbers[i]);
}

printf("\n"); // Output: 9 7 5 8


```

### Reverse Number

```c

int numbers[] = {8, 9, 7, 5};
int size = sizeof(numbers) / sizeof(numbers[0]);

for (int i = size - 1; i >= 0; i--) {
    printf("%d ", numbers[i]);
}
printf("\n"); // Output: 5 7 9 8
    
```

### Find Unique

```c

int numbers[] = {9, 9, 9, 5};
    int size = sizeof(numbers) / sizeof(numbers[0]);
    int unique = -1; // Initialize unique to -1

    // Count occurrences of each element
    for (int i = 0; i < size; i++) {
        int count = 0;
        for (int j = 0; j < size; j++) {
            if (numbers[i] == numbers[j]) {
                count++;
            }
        }
        // If count is 1, it means the element is unique
        if (count == 1) {
            unique = numbers[i];
            break;
        }
    }

    // Print the unique element
    if (unique != -1) {
        printf("%d\n", unique); // Output: 5
    }

```

# Binary to Decimal to Binary

```c

B to D
    char binary[] = "101011";
    int len = strlen(binary);
    int result = 0;

    for (int i = len - 1, count = 0; i >= 0; i--, count++) {
        result += (binary[i] - '0') * (1 << count);
    }

    printf("%d\n", result); // 43

D to B

    int decimal = 43;
    int binary[32]; // Array to store binary digits
    int index = 0;

    // Convert decimal to binary
    while (decimal > 0) {
        binary[index++] = decimal % 2;
        decimal /= 2;
    }

    // Print binary representation in reverse order
    printf("Converted: ");
    for (int i = index - 1; i >= 0; i--) {
        printf("%d", binary[i]); // 101011
    }

    printf("\n");

```
### Sum of Squares

```c
    int num = 9;
    int result = 0;

    // Compute the sum of squares
    for (int i = 0; i <= num; i++) {
        result += i * i;
    }

    printf("%d\n", result); // 285
```

### 3rd Largest number

```c

#include <stdlib.h>
 
//  for decending 
int compare(const void *a, const void *b) {
    return (*(int *)b - *(int *)a);
}

int numbers[] = {4, 3, 2, 1, 5};
int size = sizeof(numbers) / sizeof(numbers[0]);

// Sort the array in descending order
qsort(numbers, size, sizeof(int), compare);

// Print the element at index 2 (0-based indexing)
printf("%d\n", numbers[2]); // Output: 3


```
    