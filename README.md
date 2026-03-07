# 1D Array Operations
arr = [10, 20, 30, 40, 50]

print("Array elements:")
for i in range(len(arr)):
     print(arr[i])

pos = 2
value = 25
arr.insert(pos, value)
print("After insertion:", arr)

pos = 3
arr.pop(pos)
print("After deletion:", arr)
# 2D Array Operations
matrix = [
    [1, 2, 3],
    [4, 5, 6]
]

rows = 2
cols = 3

print("Matrix elements:")
for i in range(rows):
    for j in range(cols):
        print(matrix[i][j], end=" ")
    print()

print("Row-wise sum:")
for i in range(rows):
    row_sum = 0
    for j in range(cols):
        row_sum += matrix[i][j]
    print("Sum of row", i, "=", row_sum)

print("Column-wise sum:")
for j in range(cols):
    col_sum = 0
    for i in range(rows):
        col_sum += matrix[i][j]
    print("Sum of column", j, "=", col_sum)
# Matrix Addition
A = [
    [1, 2],
    [3, 4]
]

B = [
    [5, 6],
    [7, 8]
]

result = [
    [0, 0],
    [0, 0]
]

for i in range(2):
    for j in range(2):
        result[i][j] = A[i][j] + B[i][j]

print("Matrix Addition Result:")
for row in result:
    print(row)
# Matrix Transpose
matrix = [
    [1, 2, 3],
    [4, 5, 6]
]

transpose = [
    [0, 0],
    [0, 0],
    [0, 0]
]

for i in range(2):
    for j in range(3):
        transpose[j][i] = matrix[i][j]

print("Transpose of matrix:")
for row in transpose:
    print(row)
# Stack Operations using List
stack = []
stack.append(10)
stack.append(20)
stack.append(30)
print("Stack after push:", stack)

stack.pop()
print("Stack after pop:", stack)

print("Top element:", stack[-1])

if len(stack) == 0:
    print("Stack is empty")
else:
    print("Stack is not empty")
# Factorial using recursion
def factorial(n):
    if n == 0 or n == 1:  # this is the base case
        return 1
    else:
        return n * factorial(n - 1)  # recursive call

num = 5
print("Factorial of", num, "is:", factorial(num))
# Fibonacci using recursion
def fibonacci(n):
    if n == 0:
        return 0
    elif n == 1:
        return 1
    else:
        return fibonacci(n - 1) + fibonacci(n - 2)

terms = 6
print("Fibonacci series:")
for i in range(terms):
    print(fibonacci(i), end=" ")


# Tower of Hanoi using recursion
def tower_of_hanoi(n, source, auxiliary, destination):
    if n == 1:
        print("Move disk 1 from", source, "to", destination)
        return
    tower_of_hanoi(n - 1, source, destination, auxiliary)
    print("Move disk", n, "from", source, "to", destination)
    tower_of_hanoi(n - 1, auxiliary, source, destination)
disks = 3
tower_of_hanoi(disks, 'A', 'B', 'C')
# linear search
def linear_search(arr, target):
    for i in range(len(arr)):
        if arr[i] == target:
            return i   
    return -1          
arr = [15, 60, 30, 45, 50]
target = int(input("Enter element to search (Linear Search): "))
index = linear_search(arr, target)
if index != -1:
    print("Element found at index:", index)
else:
    print("Element not found")
# binary serach    
def binary_search(arr, target):
    low = 0
    high = len(arr) - 1
    while low <= high:
        mid = (low + high) // 2
        if arr[mid] == target:
            return mid
        elif target < arr[mid]:
            high = mid - 1
        else:
            low = mid + 1
    return -1  # not found
arr = [10, 20, 30, 40, 50]  # sorted list
target = int(input("Enter element to search (Binary Search): "))
index = binary_search(arr, target)
if index != -1:
    print("Element found at index:", index)
else:
    print("Element not found")
    
# bubble sort
def bubble_sort(arr):
    n = len(arr)
    
    for i in range(n):               # number of passes
        for j in range(n - 1):       # compare neighbors
            if arr[j] > arr[j + 1]:  # swap
                arr[j], arr[j + 1] = arr[j + 1], arr[j]

    return arr

arr = [5, 2, 8, 1, 3]
print("Original Array:", arr)
print("Bubble Sort:", bubble_sort(arr))

# selection sort
def selection_sort(arr):
    n = len(arr)

    for i in range(n):
        min_pos = i                      # assume current is smallest
        for j in range(i + 1, n):        # find smaller
            if arr[j] < arr[min_pos]:
                min_pos = j

        arr[i], arr[min_pos] = arr[min_pos], arr[i]  # swap smallest found

    return arr

arr = [5, 2, 8, 1, 3]
print("Selection Sort:", selection_sort(arr))

# insertion sort 
def insertion_sort(arr):
    n = len(arr)

    for i in range(1, n):        # start from 2nd element
        key = arr[i]            # element to insert
        j = i - 1

        while j >= 0 and arr[j] > key:
            arr[j + 1] = arr[j]  # shift right
            j -= 1

        arr[j + 1] = key         # insert key

    return arr

arr = [5, 2, 8, 1, 3]
print("Insertion Sort:", insertion_sort(arr))

# Function to find Nth Maximum and Minimum using built-in sort function
def nth_max_min(arr, n):
    arr.sort()   # Sort the list

    nth_min = arr[n-1]          # Nth smallest
    nth_max = arr[-n]           # Nth largest

    return nth_min, nth_max

arr = [10, 4, 7, 2, 15, 9]
n = 2

minimum, maximum = nth_max_min(arr, n)

print("Nth Minimum:", minimum)
print("Nth Maximum:", maximum)

# using built-in library of heapq
import heapq

def nth_max(arr, n):
    return heapq.nlargest(n, arr)[-1]

def nth_min(arr, n):
    return heapq.nsmallest(n, arr)[-1]


arr = [10, 4, 7, 2, 15, 9]
n = 2

print("Nth Minimum:", nth_min(arr, n))
print("Nth Maximum:", nth_max(arr, n))

# string matching 
def naive_pattern_matching(text, pattern):
    n = len(text)
    m = len(pattern)

    for i in range(n - m + 1):
        if text[i:i+m] == pattern:
            print("Pattern found at index", i)

text = "ABABDABACDABABCABAB"
pattern = "ABABC"

naive_pattern_matching(text, pattern)
