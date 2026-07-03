# 🚀 DSA Quick Reference

> **Revision Tip:** Press **Ctrl+F** and search the problem name.

---

# <span style="color:#2563EB">📘 Arrays</span>

- Largest Element
- Second Largest
- Move Zeroes
- Remove Duplicates
- Merge Sorted Arrays

# <span style="color:#7C3AED">🟣 Bit Manipulation</span>

- Single Number I
- Single Number II
- Subsets (Bitmask)
- Reverse Bits
- Power(x,n)
- Power of 2
- Power of 3
- Power of 4
- Count Set Bits

# <span style="color:#16A34A">🟢 Binary Search</span>

- Number of Occurrences
- sqrt(x)

# <span style="color:#EA580C">🟠 Recursion & Backtracking</span>

- Combination Sum
- Combinations
- Subsets II
- Permutations

# <span style="color:#DC2626">🔴 Linked Lists</span>

- Create
- Print
- Traverse
- Count Nodes
- Search
- Insert Beginning
- Insert End
- Delete First
- Reverse
- Middle
- Detect Cycle

---

## 📄 Complete Code Collection

```python
answers:

Basic + Bit manip: largest,second largest,move zeroes,single number 1,2,remove duplicates,subsets,pow 2,3,4,(x,n),reverse bits

1.largest num in arr:

arr = list(map(int, input().split()))

print(max(arr))

2.second largest in arr:

n = int(input())#if input is n and then the array
arr = list(map(int, input().split()))
maxx = arr[0]
second_maxx = -1

for i in range(1, len(arr)):
     if arr[i] > maxx:
        second_maxx = maxx
        maxx = arr[i]
     elif arr[i] != maxx and arr[i] > second_maxx:
        second_maxx = arr[i]
print(second_maxx)

3.Move ZEROES
 
i=0
j=0
n = int(input())
nums = list(map(int, input().split()))

while(j<len(nums)):
      if nums[j]!=0:
         nums[i],nums[j]=nums[j],nums[i]
         i+=1
         j+=1
      else:
         j+=1    

4.Single Number 1:

nums = list(map(int, input().split()))
val=nums[0]
        n=len(nums)
        for i in range(1,n):
            val=val^nums[i]
        return val   

5.SIngle Number 2:

def singleNumber(nums):
    ans = 0

    for i in range(32):
        c1 = 0
        for j in range(len(nums)):
            if nums[j] & (1 << i):
                c1 += 1

        if c1 % 3 != 0:
            ans |= (1 << i)

    # Handle negative numbers
    if ans >= 2**31:
        ans -= 2**32

    return ans


n = int(input())
nums = list(map(int, input().split()))

print(singleNumber(nums))



5.Remove Duplicates:

def removeDuplicates(nums):
    if len(nums) == 0:
        return 0

    i = 0

    for j in range(1, len(nums)):
        if nums[j] != nums[i]:
            i += 1
            nums[i] = nums[j]

    return i + 1


n = int(input())
nums = list(map(int, input().split()))

k = removeDuplicates(nums)

print(k)
print(*nums[:k])    # Prints the array after removing duplicates

6.SUBSETS:

def subsets(nums):
    res = []
    n = len(nums)

    for i in range(1 << n):
        row = []
        for j in range(n):
            if i & (1 << j):
                row.append(nums[j])
        res.append(row)

    return res


n = int(input())
nums = list(map(int, input().split()))

ans = subsets(nums)

for subset in ans:
    print(subset)

7.Pow(x,n):

x = float(input())
n = int(input())

if n < 0:
    n = -n
    x = 1 / x

ans = 1

while n > 0:
    if n & 1:
        ans *= x
    x *= x
    n >>= 1

print(ans)

8.reversing bits

n = int(input())

res = 0

for i in range(32):
    res = (res << 1) | (n & 1)
    n = n >> 1

print(res)

9.power of 2:

n = int(input())

if n > 0 and (n & (n - 1)) == 0:
    print(True)
else:
    print(False)  

power of 3:
n = int(input())

if n <= 0:
    print(False)
else:
    while n % 3 == 0:
        n //= 3

    print(n == 1)

power of 4:

n = int(input())

if n <= 0:
    print(False)
else:
    while n % 4 == 0:
        n //= 4

    print(n == 1)


NO of set bits:

while(n!=0):
   n=n&(n-1)
   count+=1

----------------------------------------------Bit manip---------------------------------------------------------

Recursion:combination,combination sum,

Combination sum:
def comb(i, arr, target, row, res):
    if i == len(arr) or target < 0:
        return

    if target == 0:
        res.append(row[:])
        return

    row.append(arr[i])
    comb(i, arr, target - arr[i], row, res)
    row.pop()

    comb(i + 1, arr, target, row, res)


n = int(input())
arr = list(map(int, input().split()))
target = int(input())

res = []
comb(0, arr, target, [], res)

print(res)


Combination:
def comb(i, n, k, arr, row, res):
    if k == 0:
        res.append(row[:])
        return

    if i == n:
        return

    if n - i < k:
        return

    row.append(arr[i])
    comb(i + 1, n, k - 1, arr, row, res)
    row.pop()

    comb(i + 1, n, k, arr, row, res)


n, k = map(int, input().split())

arr = [i for i in range(1, n + 1)]
res = []

comb(0, n, k, arr, [], res)

print(res)


Subsets 2:

def backtrack(start, nums, row, res):
    res.append(row[:])

    for i in range(start, len(nums)):
        if i > start and nums[i] == nums[i - 1]:
            continue

        row.append(nums[i])
        backtrack(i + 1, nums, row, res)
        row.pop()


n = int(input())
nums = list(map(int, input().split()))

nums.sort()

res = []
backtrack(0, nums, [], res)

print(res)


MERge sorted arrays:

m = int(input())
nums1 = list(map(int, input().split()))

n = int(input())
nums2 = list(map(int, input().split()))

nums = nums1[:]

i = 0
j = 0
k = 0

while i < m and j < n:
    if nums[i] < nums2[j]:
        nums1[k] = nums[i]
        i += 1
    else:
        nums1[k] = nums2[j]
        j += 1
    k += 1

while i < m:
    nums1[k] = nums[i]
    i += 1
    k += 1

while j < n:
    nums1[k] = nums2[j]
    j += 1
    k += 1

print(*nums1)

Permutations:

def backtrack(i, nums, res):
    if i == len(nums):
        res.append(nums[:])
        return

    for j in range(i, len(nums)):
        nums[i], nums[j] = nums[j], nums[i]
        backtrack(i + 1, nums, res)
        nums[i], nums[j] = nums[j], nums[i]


n = int(input())
nums = list(map(int, input().split()))

res = []
backtrack(0, nums, res)

print(res)


Number of Occurences:
n = int(input())
arr = list(map(int, input().split()))
target = int(input())

low, high = 0, n - 1
first = -1

while low <= high:
    mid = (low + high) // 2
    if arr[mid] >= target:
        if arr[mid] == target:
            first = mid
        high = mid - 1
    else:
        low = mid + 1

if first == -1:
    print(0)
else:
    low, high = 0, n - 1
    last = -1

    while low <= high:
        mid = (low + high) // 2
        if arr[mid] <= target:
            if arr[mid] == target:
                last = mid
            low = mid + 1
        else:
            high = mid - 1

    print(last - first + 1)


sqrt(x):
x = int(input())

low = 0
high = x
ans = 0

while low <= high:
    mid = (low + high) // 2

    if mid * mid <= x:
        ans = mid
        low = mid + 1
    else:
        high = mid - 1

print(ans)




-----------------------------------------------------Recursion---------------------------------------------------------

LINKED LISTS

1. Node Class

class ListNode(object):
    def __init__(self, val=0, next=None):
        self.val = val
        self.next = next

2. Create a Linked List (HackerRank Style)

Input:

5
1 2 3 4 5

class ListNode(object):
    def __init__(self, val):
        self.val = val
        self.next = None

n = int(input())
arr = list(map(int, input().split()))

head = ListNode(arr[0])
temp = head

for i in range(1, n):
    temp.next = ListNode(arr[i])
    temp = temp.next
3. Print Linked List
temp = head

while temp:
    print(temp.val, end=" ")
    temp = temp.next

Output:

1 2 3 4 5
4. Traverse a Linked List (LeetCode)
temp = head

while temp:
    print(temp.val)
    temp = temp.next
5. Count Nodes
count = 0
temp = head

while temp:
    count += 1
    temp = temp.next

print(count)
6. Search an Element
key = int(input())

temp = head

while temp:
    if temp.val == key:
        print("Found")
        break
    temp = temp.next
else:
    print("Not Found")
7. Insert at Beginning
new = ListNode(10)
new.next = head
head = new
8. Insert at End
new = ListNode(10)

if head is None:
    head = new
else:
    temp = head
    while temp.next:
        temp = temp.next
    temp.next = new
9. Delete First Node
if head:
    head = head.next
10. Reverse Linked List (Iterative)
prev = None
curr = head

while curr:
    nxt = curr.next
    curr.next = prev
    prev = curr
    curr = nxt

head = prev
11. Middle of Linked List (Slow & Fast Pointer)
slow = head
fast = head

while fast and fast.next:
    slow = slow.next
    fast = fast.next.next

print(slow.val)
12. Detect Cycle
slow = head
fast = head

while fast and fast.next:
    slow = slow.next
    fast = fast.next.next

    if slow == fast:
        print("Cycle")
        break
else:
    print("No Cycle")

```

---

## ⭐ Common Time Complexities

| Problem | Complexity |
|---------|------------|
| Largest | O(n) |
| Second Largest | O(n) |
| Move Zeroes | O(n) |
| Remove Duplicates | O(n) |
| Single Number | O(n) |
| Reverse Bits | O(32) |
| Power(x,n) | O(log n) |
| Binary Search | O(log n) |
| sqrt(x) | O(log n) |
| Subsets | O(n·2ⁿ) |
| Permutations | O(n·n!) |
| Combination Sum | Exponential |
| Linked List Reverse | O(n) |
