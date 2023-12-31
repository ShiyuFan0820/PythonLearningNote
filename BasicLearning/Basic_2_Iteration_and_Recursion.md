# What Are Iteration And Recursion

## Iteration

If there are elements in a given range, the programme will loop throught the elements one by one automatically and will stop looping until reaches the last one. This process is called iteration.

## Recursion

Recuesion is a function that calls itself from within.

# Fibonacci Sequence In Iteration And Recursion

## Fibonacci Sequence

Fibonacci sequence is a kind of number sequence where the next value always equals the sum of it's two previous values. For example:
|No.1|No.2|No.3   |No.4 |No.5  |No.6  |No.7  |No.8  |No.9|
|:----:|:----:|:----:|:----:|:----:|:----:|:----:|:----:|:----:|
|0    |1  |1(0+1)|2(1+1)|3(1+2)|5(2+3)|8(3+5)|13(5+8)|21(8+13)|

## Fibonacci In Iteration

```py
def fibonacci(index):
    num1 = 0
    num2 = 1  #Because the next value is equal to the sum of the two previous values, so we define two viariables to store the two values.
    if index == 1:
        return 0
    elif index == 2:
        return 1
    else:
        for i in range(index-2): #Loop evaluation loops once from the third number, loops twice from the fourth number.
            result = num1 + num2
            num1 = num2
            num2 = result
        return result

#Test a few indices:
print(fibonacci(1))
print(fibonacci(2))
print(fibonacci(3))
print(fibonacci(4))
print(fibonacci(5))
```

The output is:
```py
0
1
1
2
3
```

## Fibonacci In Recursion

```py
def fibonacci(index):
    if index == 1:
        return 0
    elif index == 2:
        return 1
    else:
        result = fibonacci(index - 1) + fibonacci(index - 2) #Function calls itself in within.
        return result

#Test a few indices
print(fibonacci(1))
print(fibonacci(2))
print(fibonacci(3))
print(fibonacci(4))
print(fibonacci(5))
```

The output is:
```py
0
1
1
2
3
```

_**Issues: When I first wrote the code I made a mistake, it was when the `index` is equal to `1` or `2`, the values are assigned to the `result`, but they are not returned, when the code reaches the `else` block and makes the recursion, the base cases return `None`, and `None` to `None` can not be added, so the `TypeError` occurs.**_

_**This is the wrong code:**_

```py
def fibonacci(index):
    if index == 1:
        result = 0 #The result is not returned
    elif index == 2:
        result = 1
    else:
        result = fibonacci(index - 1) + fibonacci(index - 2)
    print(result)

print(fibonacci(1))
print(fibonacci(2))
print(fibonacci(3))
```

_**The output is:**_
```py
TypeError: unsupported operand type(s) for +: 'NoneType' and 'NoneType'
0
None
1
None
1
0
```

# Iteration vs Recursion

To test which one is more efficient, we can use the `time` module to record the time it takes for both functions:

**The speed of iteration:**

```py
import time
def fibonacci(index):
    num1 = 0
    num2 = 1  
    if index == 1:
        return 0
    elif index == 2:
        return 1
    else:
        for i in range(index-2):
            result = num1 + num2
            num1 = num2
            num2 = result
        return result

record = time.time()
print(fibonacci(40))
print("The speed of iteration is: " + str(time.time() - record) )
```
**The output is:**
```py
63245986
The speed of iteration is: 1.2159347534179688e-05
```

**The speed of recursion:**

```py
import time
def fibonacci(index):
    if index == 1:
        return 0
    elif index == 2:
        return 1
    else:
        result = fibonacci(index - 1) + fibonacci(index - 2) 
        return result

record = time.time()
print(fibonacci(40))
print("The speed of recursion is: " + str(time.time() - record) )
```
**The output is:**
```py
63245986
The speed of recursion is: 6.610930919647217
```

Apparently, $1.2159347534179688e-05 < 6.610930919647217$, the speed of iteation is quicker than recursion. 

**In conclusion, comparing to recursion, iteration is faster, and although the recursion code can be easy to understand, it will cause stack overflow in some situations.**






