# Finding specific large elements from a list using heapsort 

##  heapfiy , min heap

## TC = NLOGN
## SC= constant


```python
import heapq


def heapify(arr,N,i):
    smallest=i
    l=2*i+1
    r=2*i+2

    if l < N and arr[smallest] > arr[l]:
        smallest=l
    if r < N and arr[smallest] > arr[r]:
        smallest=r

    if smallest !=i:
        arr[i],arr[smallest]=arr[smallest],arr[i]

        heapify(arr,N,smallest)

def heapsort(arr):
    N=len(arr)


    for i in range(N//2-1,-1,-1):
        heapify(arr,N,i)

    for i in range(N-1,0,-1):
        arr[i],arr[0]=arr[0],arr[i]
        heapify(arr,i,0)


if __name__=='__main__':
    arr=[12,11,13,5,6,7]
    heapsort(arr)
    N=len(arr)
    selectCount=3

    print("Sorted array in descending order is ")
    for i in range(N):
        print("%d" % arr[i],end=" ")
    print("\n")
    print("the first three largest elements are as follows-:")
    largest=heapq.nlargest(selectCount,arr)
    print(largest)
```


## Time and Space Complexity Analysis

### Heapify Function (`heapify(arr, N, i)`)

- **Time Complexity**: The `heapify` function is called recursively, and in the worst case, it runs for `O(log N)` times for each element. Therefore, the time complexity of a single call to `heapify` is `O(log N)`.

- **Space Complexity**: The `heapify` function uses a constant amount of space, `O(1)`, but the recursive stack space can be `O(log N)` in the worst case.

### Heap Sort Function (`heapsort(arr)`)

1. **Building the Heap**: 
   - The loop runs from `N//2 - 1` to `0`, and for each element, the `heapify` function is called. Therefore, the total time complexity for building the heap is `O(N)`.

2. **Extracting Elements from Heap**:
   - The second loop runs `N-1` times, and for each iteration, the `heapify` function is called, which takes `O(log N)` time. So, the time complexity for this part is `O(N log N)`.

- **Overall Time Complexity**: 
  - The overall time complexity of the `heapsort` function is `O(N log N)`.

- **Space Complexity**:
  - The space complexity is `O(1)` for the `heapsort` function as it sorts the array in place, except for the recursive stack space used by `heapify`, which is `O(log N)`.

### Finding the Largest Elements (`heapq.nlargest(selectCount, arr)`)

- **Time Complexity**: 
  - The `heapq.nlargest()` function uses a heap to find the `k` largest elements in `O(N log k)` time.

- **Space Complexity**:
  - The space complexity is `O(k)` where `k` is the number of largest elements to find.

### Overall Complexity

- **Overall Time Complexity**: 
  - The overall time complexity of the entire program (including heap sort and finding the largest elements) is `O(N log N)`.

- **Overall Space Complexity**:
  - The overall space complexity of the entire program is `O(1)` (ignoring the space used by `heapify` recursion stack and the space used by `heapq.nlargest()`).



# Heap Sort and Extracting Top K Largest Elements

## Approach



### Step 1: Heapify the Array
- Start by building a min-heap from the input array.
- Iterate from the last non-leaf node to the root node, applying the `heapify` function.
- `heapify` ensures that each subtree rooted at any index follows the min-heap property.

### Step 2: Perform Heap Sort
- Swap the root of the heap (the smallest element) with the last element of the heap.
- Reduce the heap size by one and call `heapify` on the new root.
- Repeat this process until the heap is reduced to a single element.
- This results in a sorted array in descending order since the smallest element is moved to the end in each iteration.

### Step 3: Extract the Largest Elements
- Use Python's `heapq.nlargest` to extract the `selectCount` largest elements from the sorted array.
- This function efficiently retrieves the top `selectCount` largest elements from the array.

### Step 4: Output the Results
- Print the sorted array.
- Print the first three largest elements from the array.


