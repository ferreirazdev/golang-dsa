# Contains Duplicate

## Example Walkthrough

**Input**

```text
nums = [1, 2, 3, 1]
```

**Goal**

Return `true` if any value appears at least twice; otherwise return `false`.

## Steps

```text
Start:
seen = {}

Step 1: read 1
- 1 is not in seen -> add it
seen = {1}

Step 2: read 2
- 2 is not in seen -> add it
seen = {1, 2}

Step 3: read 3
- 3 is not in seen -> add it
seen = {1, 2, 3}

Step 4: read 1
- 1 is already in seen -> duplicate found
```

**Result:** `true`