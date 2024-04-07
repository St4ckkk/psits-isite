
### Common Pattern
```py
rows = 5
    # Top half
    for i in range(rows):
        # increment 1 to 5, (upper left)                    * 5 4 3 2 1 * * * * * 1 
        for j in range(i + 1):                              * * 5 4 3 2 * * * * 1 2 
            print("*", end=" ")                             * * * 5 4 3 * * * 1 2 3 
                                                            * * * * 5 4 * * 1 2 3 4 
        #decrement 5 to 1, starts at (upper right)          * * * * * 5 * 1 2 3 4 5 
        for k in range(5, i, -1):                           1 2 3 4 5 * 5 * * * * * 
            print(k, end=" ")                               1 2 3 4 * * 5 4 * * * * 
                                                            1 2 3 * * * 5 4 3 * * * 
        #decrement 5* to 1, starts at (upper left)          1 2 * * * * 5 4 3 2 * * 
        for k in range(5, i, -1):                           1 * * * * * 5 4 3 2 1 * 
            print("*", end=" ")
         
        # increment 1 to 5 starts at (upper right)
        for k in range(i + 1):
            print(k + 1, end=" ")
        print()


    # Bottom half
    for i in range(rows, 0, -1):
        #decrement, starts at (upper left)
        for j in range(i):
            print(j + 1, end=" ")
            
        # increment 1 to 5, starts at (upper right)
        for j in range(5 + 1, i, -1):
            print("*", end=" ")
            
        #decrement 5 to 1, starts at at (upper right)      
        for j in range(6, i, -1):
            print(j - 1, end=" ")
            
        #decrement 5 to 1, starts at at (upper right)      
        for k in range(i):
            print("*", end=" ")
        print()        

```

### String Pattern

Increment text from R to Reydel
If decrement, use the len as start and step is -1 / range(len(text), 0, -1):

```py
    text = "Reydel"
    for i in range(1, len(text) + 1):
        print(text[:i])
```


### Hallow Rectangle
```py
rows = 5
cols = 8
                                                                              * * * * * * * * 
    for i in range(rows):                                                     *             * 
        for j in range(cols):                                                 *             * 
            if i == 0 or i == rows - 1 or j == 0 or j == cols - 1:            *             * 
                print("*", end=" ")                                           * * * * * * * * 
            else:
                print(" ", end=" ")
        print()
```

### Zigzag Pattern
```py
    def zigzag_pattern(rows, cols):                                             * * * * * 
        for i in range(rows):                                                           *
            for j in range(cols):                                               * * * * * 
                if i % 2 == 0:                                                          *
                    print("*", end=" ")                                         * * * * *
                else:
                    if j == cols - 1 and i % 2 != 0:
                        print("*", end="")
                    else:
                        print(" ", end=" ")
            print()

    zigzag_pattern(5, 5)

```


### Cross Pattern (x)
If printing symbol, change the print to *, etc
```py                                                              
    n = 10                                                                  0   0
    for rows in range(n):                                                    1 1 
    for cols in range(n):                                                     2  
        if((rows == cols) or (rows+cols)==n-1 ):                             1 1 
        print(min(rows, n - rows - 1),end="")                               0   0
        else:
        print(" ",end="")
    print()

```


### Pascal Triangle

if dont want a pyramid, remove the first inner loop

```py

n = 5
    for i in range(1, n+1):
        for j in range(0, n-i+1):
            print(' ', end='')
                                                                          1
        # first element is always 1                                      1 1
        basis = 1                                                       1 2 1
        for j in range(1, i+1):                                        1 3 3 1
                                                                      1 4 6 4 1
            # first value in a line is always 1
            print(' ', basis, sep='', end='')

            # using Binomial Coefficient
            # basis = basis multiply (i - j) then divide 
            basis = basis * (i - j) // j
        print()

```


### Diamond

although the other example is at the top, 
this one specifically for diamond

```py
    n = 5                                                             
    for i in range(n):
        print(" " * (n - i - 1) + "*" * (2 * i + 1))                    basta pina diamond
    for i in range(n - 2, -1, -1):
        print(" " * (n - i - 1) + "*" * (2 * i + 1))
        
```

# Previous Psits

### Check Prime no.
```py
    num = 1
    if num > 1:
        for i in range(2, (num//2)+1):
            if (num % i) == 0:
                print(num, "is not a prime number")
                break
        else:
            print(num, "is a prime number")
    else:
        print(num, "is not a prime number")

```

### Largest no. in array

```py
    numbers = [5,4,2,5,10]

    print(max(numbers)) // 10
```

### Swiper Swapper

```py

    numbers = [8,9,7,5]

    popNumber = numbers.pop(0)

    numbers.append(popNumber)

    print(*numbers) // 9 7 5 8

```

### Reverse Number

``` py
    numbers = [8,9,7,5]

    print(*reversed(numbers)) // 5, 7, 9, 8
```


### Find Unique


```py
    numbers = [9,9,9,5]

    # if only appears once
    unique = list(filter(lambda x: numbers.count(x) == 1, numbers))

    if len(unique) > 0:
    print(unique[0]) // 5

```

### Binary to Decimal

```py

    binary =  str(101011)
    list_binary = [char for char in binary]
    count = 0
    result = 0
    for i in reversed(list_binary):
        result += int(i) * 2 ** count
        count += 1
    print(result) // 43

```

### Sum of Squares

```py

    num = 9
    result = 0
    for i in range(num + 1):
        result = result + ((i) * i)

    print(result) // 285

```


