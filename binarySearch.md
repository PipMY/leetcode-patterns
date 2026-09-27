# Binary Search

So, you have to find the monotonic function for whatever array / range you're trying to find a value from, i.e. you have to take an array:

```cpp
vector<int> example{0,1,2,3,5,6,7,8};

```
and if we want to find the first number that is greater than 3 we could then conceptually make the array:

```cpp
vector<bool> monoExample{F,F,F,F,T,T,T,T};
```

Careful, because vector<bool> is actually special, anyway.

We then can just find the left boundary of this array of truths. And yeah, your task is basically just to find that monotonic function.

## Generic Template

```cpp
int binary_search(std::vector<int> arr, int target) {
  int left = 0;
  int right = arr.size() - 1;
  int firstTrueIndex = -1;
  while (left <= right) {
    int mid = left + (right - left) / 2;

    if (feasible(mid)) {
      firstTrueIndex = mid;
      right = mid - 1;
    }

    else {
      left = mid + 1;
    }
  }

  return firstTrueIndex;
}
```
```
```
```
```
```
```

