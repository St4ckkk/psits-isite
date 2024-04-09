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