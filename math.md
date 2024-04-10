# MATH

### FACTORIAL TRAILING ZERO

```c
int trailingZeroes(int n){
    int five = 0;
    for(int i = 5; i <=n; i+=5){
        int val = i;
        while(val){
            if(val %5 == 0){
                five++;
                val /= 5;
            }
            else
                break;
        }
    }
    return five;
}
```

### PRIME NUMBER

```c
bool isPrime(int n) {
    if (n <= 1)
        return false;
    for (int i = 2; i * i <= n; i++) {
        if (n % i == 0)
            return false;
    }
    return true;
}
```

### GCD - GREATEST COMMON DIVISOR


```c
int gcd(int a, int b) {
    if (b == 0)
        return a;
    return gcd(b, a % b);
}
```

### LCM - LEAST COMMON MULTIPLE

```c
int lcm(int a, int b) {
    return a * b / gcd(a, b);
}
```

### POWER OF NUMBER

```c
int power(int a, int b) {
    int res = 1;
    for (int i = 0; i < b; i++)
        res *= a;
    return res;
}
```

### POWER OF NUMBER - RECURSIVE

```c

int power_recursive(int a, int b) {
    if (b == 0)
        return 1;
    return a * power_recursive(a, b - 1);
}
```

### POWER OF NUMBER - FAST POWER

```c
int power_fast(int a, int b) {
    int res = 1;
    while (b) {
        if (b % 2 == 1)
            res *= a;
        a *= a;
        b /= 2;
    }
    return res;
}
```

### FIBONACCI

```c
int fib(int n) {
    if (n == 0)
        return 0;
    if (n == 1)
        return 1;
    return fib(n - 1) + fib(n - 2);
}
```

### FIBONACCI - ITERATIVE

```c
int fib_iterative(int n) {
    if (n == 0)
        return 0;
    if (n == 1)
        return 1;
    int a = 0, b = 1;
    for (int i = 2; i <= n; i++) {
        int c = a + b;
        a = b;
        b = c;
    }
    return b;
}
```

### REVERSE INTEGER

```c
int reverse(int x) {
    long long res = 0; 
    while (x != 0) {
        res = res * 10 + x % 10; 
        x /= 10;
    }

    return (int)res; 
}
```

### PALINDROME NUMBER

```c
#include <stdio.h>

int isPalindrome(int x) {
    if (x < 0)
        return 0;
    long long res = 0;
    int val = x;
    while (x) {
        res = res * 10 + x % 10;
        x /= 10;
    }
    return res == val;
}

int main() {
    int number;
    printf("Enter an integer: ");
    scanf("%d", &number);
    
    if (isPalindrome(number)) {
        printf("%d is a palindrome.\n", number);
    } else {
        printf("%d is not a palindrome.\n", number);
    }

    return 0;
}
```

### Find Triangular Sum of an Array

```c
int findTriangularSum(int arr[], int n){
    int sum = 0;
    for(int i = 0; i < n; i++){
        sum += arr[i]*(arr[i]+1)*(arr[i]+2)/6;
    }
    return sum;
}

int arr[] = {1, 2, 3, 4, 5};
printf("Output: %d\n", findTriangularSum(arr, 5)); 

```

### Find Triangular Number

```c
int isTriangular(int n){
    int sum = 0;
    for(int i = 1; sum < n; i++){
        sum += i;
        if(sum == n)
            return 1;
    }
    return 0;
}

int main(){
    int n;
    printf("Enter a number: ");
    scanf("%d", &n);
    if(isTriangular(n))
        printf("%d is a triangular number.\n", n);
    else
        printf("%d is not a triangular number.\n", n);
    return 0;
}
```

### COUNT SORTED VOWELS STRING

```c

int count(int n, int c)
{
	if(n == 1)
		return 5 - c + 1;

	int ret = 0;
	for(int i=c; i<=5; i++)
		ret += count(n-1, i);
		
	return ret;
}

int countVowelStrings(int n)
{
	return count(n, 1);
}

int main()
{
    int n;
    printf("Enter a number: ");
    scanf("%d", &n);
    printf("Output: %d\n", countVowelStrings(n));
    return 0;
}
```

### Convert the Temperature

```c
#include <stdio.h>
#include <stdlib.h>

double* convertTemperature(double celsius, int* returnSize){
    double* ans = malloc(2 * sizeof(double));
    ans[0] = celsius + 273.15;
    ans[1] = celsius*1.8 + 32;
    *returnSize = 2;
    return ans;
}

int main(){
    double celsius;
    printf("Enter the temperature in celsius: ");
    scanf("%lf", &celsius);
    int returnSize;
    double* ans = convertTemperature(celsius, &returnSize);
    printf("Output: [%.5lf, %.5lf]\n", ans[0], ans[1]);
    return 0;
}
```

### IDENTICAL PAIRS

```c

int numIdenticalPairs(int* nums, int numsSize){
    int s = 0, a[101] = { 0 };
    for (int i = 0; i < numsSize; i++) s += a[nums[i]]++;
    return s;
}

int main(){
    int n;
    printf("Enter the size of the array: ");
    scanf("%d", &n);
    int arr[n];
    printf("Enter the elements of the array: ");
    for(int i = 0; i < n; i++)
        scanf("%d", &arr[i]);
    printf("Output: %d\n", numIdenticalPairs(arr, n));
    return 0;
}
```

### SUM OF ALL ODD LENGTH SUBARRAYS

```c

int sumOddLengthSubarrays(int* arr, int arrSize){
    int sum = 0;
    for(int i = 0; i < arrSize; i++){
        int sum1 = 0;
        for(int j = i; j < arrSize; j++){
            sum1 += arr[j];
            if((j-i+1)%2 == 1)
                sum += sum1;
        }
    }
    return sum;
}

int main(){
    int n;
    printf("Enter the size of the array: ");
    scanf("%d", &n);
    int arr[n];
    printf("Enter the elements of the array: ");
    for(int i = 0; i < n; i++)
        scanf("%d", &arr[i]);
    printf("Output: %d\n", sumOddLengthSubarrays(arr, n));
    return 0;
}
```

### SUM OF ALL SUBARRAYS

```c

int sumSubarray(int* arr, int arrSize){
    int sum = 0;
    for(int i = 0; i < arrSize; i++){
        int sum1 = 0;
        for(int j = i; j < arrSize; j++){
            sum1 += arr[j];
            sum += sum1;
        }
    }
    return sum;
}

int main(){
    int n;
    printf("Enter the size of the array: ");
    scanf("%d", &n);
    int arr[n];
    printf("Enter the elements of the array: ");
    for(int i = 0; i < n; i++)
        scanf("%d", &arr[i]);
    printf("Output: %d\n", sumSubarray(arr, n));
    return 0;
}
```

### Divisible and Non-divisible Sums Difference

```c

int differenceOfSums(int n, int m) {
    int num1 = 0, num2 = 0;
    for (int i = 1; i <= n; i++) {
        if (i % m == 0) num2 += i;
        else num1 += i;
    }
    return num1 - num2;
}

int main() {
    int n, m;
    printf("Enter two numbers: ");
    scanf("%d %d", &n, &m);
    printf("Output: %d\n", differenceOfSums(n, m));
    return 0;
}
```

### Find the Sum of the Series

```c

int sumOfSeries(int n) {
    int sum = 0;
    for (int i = 1; i <= n; i++) {
        sum += i * i;
    }
    return sum;
}

int main() {
    int n;
    printf("Enter a number: ");
    scanf("%d", &n);
    printf("Output: %d\n", sumOfSeries(n));
    return 0;
}
```

### SELF CROSSING
```c
bool isSelfCrossing(int* x, int xSize){
    for(int i = 3; i < xSize; i++){
        if(x[i] >= x[i-2] && x[i-1] <= x[i-3])
            return true;
        if(i >= 4 && x[i-1] == x[i-3] && x[i] + x[i-4] >= x[i-2])
            return true;
        if(i >= 5 && x[i-2] >= x[i-4] && x[i] + x[i-4] >= x[i-2] && x[i-1] <= x[i-3] && x[i-1] + x[i-5] >= x[i-3])
            return true;
    }
    return false;
}

int main(){
    int n;
    printf("Enter the size of the array: ");
    scanf("%d", &n);
    int arr[n];
    printf("Enter the elements of the array: ");
    for(int i = 0; i < n; i++)
        scanf("%d", &arr[i]);
    if(isSelfCrossing(arr, n))
        printf("Output: true\n");
    else
        printf("Output: false\n");
    return 0;
}
```

### Water and Jug Problem

```c

int gcd(int a, int b) {
    if (b == 0)
        return a;
    return gcd(b, a % b);
}

bool canMeasureWater(int x, int y, int z) {
    if (x + y < z) return false;
    if (x == z || y == z || x + y == z) return true;
    return z % gcd(x, y) == 0;
}


int main() {
    int x, y, z;
    printf("Enter three numbers: ");
    scanf("%d %d %d", &x, &y, &z);
    if (canMeasureWater(x, y, z)) {
        printf("Output: true\n");
    } else {
        printf("Output: false\n");
    }
    return 0;
}
```

### Find the Number of Digits in an Integer

```c

int findDigits(int n) {
    int count = 0;
    while (n != 0) {
        n /= 10;
        count++;
    }
    return count;
}

int main() {
    int n;
    printf("Enter an integer: ");
    scanf("%d", &n);
    printf("Output: %d\n", findDigits(n));
    return 0;
}
```

### Sum of Number and Its Reverse

```c

int rev(int x){
	int ans=0;
	while(x!=0){
		ans=ans*10+x%10;
		x/=10;
	}
	return ans;
}

bool sumOfNumberAndReverse(int num){
	if(num==0) return true;
	for(int i=num/2;i<num;i++){
		if(i+rev(i)==num){
			return true;
		}
	}
	return false;
}

int main(){
    int n;
    printf("Enter an integer: ");
    scanf("%d", &n);
    if(sumOfNumberAndReverse(n))
        printf("Output: true\n");
    else
        printf("Output: false\n");
    return 0;
}

```

### MAXIMUM SWAP

```c
int maximumSwap(int num){
    char s[12];
    sprintf(s, "%d", num);
    int n = strlen(s);
    int max = -1, maxIndex = -1, leftIndex = -1, rightIndex = -1;
    for(int i = n-1; i >= 0; i--){
        if(s[i] > max){
            max = s[i];
            maxIndex = i;
        }
        else if(s[i] < max){
            leftIndex = i;
            rightIndex = maxIndex;
        }
    }
    if(leftIndex == -1)
        return num;
    char temp = s[leftIndex];
    s[leftIndex] = s[rightIndex];
    s[rightIndex] = temp;
    return atoi(s);
}

int main(){
    int n;
    printf("Enter an integer: ");
    scanf("%d", &n);
    printf("Output: %d\n", maximumSwap(n));
    return 0;
}
```

### WATER BOTTLES

```c

int numWaterBottles(int numBottles, int numExchange){
    int res = numBottles;
    while(numBottles >= numExchange) {
        res += numBottles / numExchange;
        numBottles = numBottles / numExchange + numBottles % numExchange;
    }
    
    return res;
}

int main(){
    int n, m;
    printf("Enter two numbers: ");
    scanf("%d %d", &n, &m);
    printf("Output: %d\n", numWaterBottles(n, m));
    return 0;
}
```

### Rotated Digits
    
```c

int rotatedDigits(int n){
    int count = 0;
    for(int i = 1; i <= n; i++){
        int num = i;
        bool valid = false;
        while(num){
            int digit = num % 10;
            if(digit == 3 || digit == 4 || digit == 7){
                valid = false;
                break;
            }
            if(digit == 2 || digit == 5 || digit == 6 || digit == 9)
                valid = true;
            num /= 10;
        }
        if(valid)
            count++;
    }
    return count;
}

int main(){
    int n;
    printf("Enter a number: ");
    scanf("%d", &n);
    printf("Output: %d\n", rotatedDigits(n));
    return 0;
}
```

### Concatenation of Consecutive Binary Numbers

```c

int concatenatedBinary(int n){
    long long ans = 0;
    for(int i = 1; i <= n; i++){
        int len = log2(i) + 1;
        ans = ((ans << len) + i) % 1000000007;
    }
    return ans;
}

int main(){
    int n;
    printf("Enter a number: ");
    scanf("%d", &n);
    printf("Output: %d\n", concatenatedBinary(n));
    return 0;
}

```

### Find Greatest Common Divisor of Array

```c

int findGCD(int* nums, int numsSize){
    int min = INT_MAX, max = INT_MIN;
    for(int i = 0; i < numsSize; i++){
        if(nums[i] < min)
            min = nums[i];
        if(nums[i] > max)
            max = nums[i];
    }
    return gcd(min, max);
}

int main(){
    int n;
    printf("Enter the size of the array: ");
    scanf("%d", &n);
    int arr[n];
    printf("Enter the elements of the array: ");
    for(int i = 0; i < n; i++)
        scanf("%d", &arr[i]);
    printf("Output: %d\n", findGCD(arr, n));
    return 0;
}
```
### BINARY NUMBER WITH ALTERNATING BITS

```c

bool hasAlternatingBits(int n){
    int prev = n % 2;
    n /= 2;
    while(n){
        if(n % 2 == prev)
            return false;
        prev = n % 2;
        n /= 2;
    }
    return true;
}

int main(){
    int n;
    printf("Enter a number: ");
    scanf("%d", &n);
    if(hasAlternatingBits(n))
        printf("Output: true\n");
    else
        printf("Output: false\n");
    return 0;
}
```

### MATRIX ADDITION

```c

int** matrixAddition(int** mat1, int mat1Size, int* mat1ColSize, int** mat2, int mat2Size, int* mat2ColSize, int* returnSize, int** returnColumnSizes){
    int** res = (int**)malloc(mat1Size * sizeof(int*));
    *returnColumnSizes = (int*)malloc(mat1Size * sizeof(int));
    for(int i = 0; i < mat1Size; i++){
        res[i] = (int*)malloc((*mat1ColSize) * sizeof(int));
        (*returnColumnSizes)[i] = *mat1ColSize;
        for(int j = 0; j < *mat1ColSize; j++)
            res[i][j] = mat1[i][j] + mat2[i][j];
    }
    *returnSize = mat1Size;
    return res;
}

int main(){
    int n, m;
    printf("Enter the number of rows and columns: ");
    scanf("%d %d", &n, &m);
    int** mat1 = (int**)malloc(n * sizeof(int*));
    int* mat1ColSize = (int*)malloc(n * sizeof(int));
    printf("Enter the elements of the first matrix: ");
    for(int i = 0; i < n; i++){
        mat1[i] = (int*)malloc(m * sizeof(int));
        mat1ColSize[i] = m;
        for(int j = 0; j < m; j++)
            scanf("%d", &mat1[i][j]);
    }
    int** mat2 = (int**)malloc(n * sizeof(int*));
    int* mat2ColSize = (int*)malloc(n * sizeof(int));
    printf("Enter the elements of the second matrix: ");
    for(int i = 0; i < n; i++){
        mat2[i] = (int*)malloc(m * sizeof(int));
        mat2ColSize[i] = m;
        for(int j = 0; j < m; j++)
            scanf("%d", &mat2[i][j]);
    }
    int returnSize, *returnColumnSizes;
    int** res = matrixAddition(mat1, n, mat1ColSize, mat2, n, mat2ColSize, &returnSize, &returnColumnSizes);
    printf("Output: \n");
    for(int i = 0; i < returnSize; i++){
        for(int j = 0; j < returnColumnSizes[i]; j++)
            printf("%d ", res[i][j]);
        printf("\n");
    }
    return 0;
}
```

### Closest Divisors

```c

int* closestDivisors(int num, int* returnSize){
    int* res = (int*)malloc(2 * sizeof(int));
    int a = sqrt(num + 2), b = sqrt(num + 1);
    while(a > 0){
        if((num + 1) % a == 0){
            res[0] = a;
            res[1] = (num + 1) / a;
            break;
        }
        a--;
    }
    while(b > 0){
        if((num + 2) % b == 0){
            res[0] = b;
            res[1] = (num + 2) / b;
            break;
        }
        b--;
    }
    *returnSize = 2;
    return res;
}

int main(){
    int n;
    printf("Enter a number: ");
    scanf("%d", &n);
    int returnSize;
    int* res = closestDivisors(n, &returnSize);
    printf("Output: [%d, %d]\n", res[0], res[1]);
    return 0;
}
```

### Find the Smallest Divisor Given a Threshold

```c

int smallestDivisor(int* nums, int numsSize, int threshold){
    int left = 1, right = 1000000;
    while(left < right){
        int mid = left + (right - left) / 2;
        int sum = 0;
        for(int i = 0; i < numsSize; i++)
            sum += (nums[i] + mid - 1) / mid;
        if(sum > threshold)
            left = mid + 1;
        else
            right = mid;
    }
    return left;
}

int main(){
    int n, m;
    printf("Enter the size of the array: ");
    scanf("%d", &n);
    int arr[n];
    printf("Enter the elements of the array: ");
    for(int i = 0; i < n; i++)
        scanf("%d", &arr[i]);
    printf("Enter a number: ");
    scanf("%d", &m);
    printf("Output: %d\n", smallestDivisor(arr, n, m));
    return 0;
}
```

### Find the Smallest Common Number

```c

int findCommon(int* arr1, int n1, int* arr2, int n2, int* arr3, int n3){
    int i = 0, j = 0, k = 0;
    while(i < n1 && j < n2 && k < n3){
        if(arr1[i] == arr2[j] && arr2[j] == arr3[k])
            return arr1[i];
        if(arr1[i] <= arr2[j] && arr1[i] <= arr3[k])
            i++;
        else if(arr2[j] <= arr1[i] && arr2[j] <= arr3[k])
            j++;
        else
            k++;
    }
    return -1;
}

int main(){
    int n1, n2, n3;
    printf("Enter the size of the first array: ");
    scanf("%d", &n1);
    int arr1[n1];
    printf("Enter the elements of the first array: ");
    for(int i = 0; i < n1; i++)
        scanf("%d", &arr1[i]);
    printf("Enter the size of the second array: ");
    scanf("%d", &n2);
    int arr2[n2];
    printf("Enter the elements of the second array: ");
    for(int i = 0; i < n2; i++)
        scanf("%d", &arr2[i]);
    printf("Enter the size of the third array: ");
    scanf("%d", &n3);
    int arr3[n3];
    printf("Enter the elements of the third array: ");
    for(int i = 0; i < n3; i++)
        scanf("%d", &arr3[i]);
    printf("Output: %d\n", findCommon(arr1, n1, arr2, n2, arr3, n3));
    return 0;
}
```


### Most Frequent Prime

```c

int mostFrequentPrime(int* arr, int n){
    int max = 0, res = 0;
    for(int i = 0; i < n; i++){
        int count = 0;
        for(int j = 2; j <= arr[i]; j++){
            if(arr[i] % j == 0){
                int isPrime = 1;
                for(int k = 2; k <= j / 2; k++){
                    if(j % k == 0){
                        isPrime = 0;
                        break;
                    }
                }
                if(isPrime)
                    count++;
            }
        }
        if(count > max){
            max = count;
            res = arr[i];
        }
    }
    return res;
}

int main(){
    int n;
    printf("Enter the size of the array: ");
    scanf("%d", &n);
    int arr[n];
    printf("Enter the elements of the array: ");
    for(int i = 0; i < n; i++)
        scanf("%d", &arr[i]);
    printf("Output: %d\n", mostFrequentPrime(arr, n));
    return 0;
}
```


### Multiply Strings

```c

char* multiply(char* num1, char* num2){
    int n = strlen(num1), m = strlen(num2);
    int* res = (int*)malloc((n + m) * sizeof(int));
    for(int i = 0; i < n + m; i++)
        res[i] = 0;
    for(int i = n - 1; i >= 0; i--){
        for(int j = m - 1; j >= 0; j--){
            int mul = (num1[i] - '0') * (num2[j] - '0');
            int sum = mul + res[i + j + 1];
            res[i + j] += sum / 10;
            res[i + j + 1] = sum % 10;
        }
    }
    char* ans = (char*)malloc((n + m + 1) * sizeof(char));
    int i = 0;
    while(i < n + m && res[i] == 0)
        i++;
    if(i == n + m){
        ans[0] = '0';
        ans[1] = '\0';
        return ans;
    }
    int k = 0;
    while(i < n + m){
        ans[k++] = res[i] + '0';
        i++;
    }
    ans[k] = '\0';
    return ans;
}

int main(){
    char num1[100], num2[100];
    printf("Enter two numbers: ");
    scanf("%s %s", num1, num2);
    char* res = multiply(num1, num2);
    printf("Output: %s\n", res);
    return 0;
}
```


### Closest Prime Numbers in Range

```c

bool isPrime(int n){
    if(n <= 1)
        return false;
    for(int i = 2; i * i <= n; i++){
        if(n % i == 0)
            return false;
    }
    return true;
}

void closestPrimes(int n){
    int left = n - 1, right = n + 1;
    while(1){
        if(isPrime(left)){
            printf("%d ", left);
            break;
        }
        left--;
    }
    while(1){
        if(isPrime(right)){
            printf("%d\n", right);
            break;
        }
        right++;
    }
}

int main(){
    int n;
    printf("Enter a number: ");
    scanf("%d", &n);
    closestPrimes(n);
    return 0;
}
```








