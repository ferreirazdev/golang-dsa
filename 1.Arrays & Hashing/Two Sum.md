# Two Sum

## Example Walkthrough

**Input**

```text
nums = [2, 7, 11, 15]
target = 9
```

**Goal**

Return the two distinct indices `i` and `j` such that `nums[i] + nums[j] == target`.

## Steps

```text
Start:
map = {}

Step 1: i = 0, nums[0] = 2
- complement = target - 2 = 7 → not in map
- store value -> index: map[2] = 0
map = {2: 0}

Step 2: i = 1, nums[1] = 7
- complement = target - 7 = 2 → exists in map at index 0
→ return [0, 1]
```

**Result:** `[0, 1]`
