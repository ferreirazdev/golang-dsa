# Valid Anagram

## Example Walkthrough

**Input**

```text
s = "anagram"
t = "nagaram"
```

**Goal**

Return `true` if `t` is an anagram of `s` (same characters with the same frequencies); otherwise return `false`.

## Steps

```text
Start:
count = {}

Step 1: scan s = a n a g r a m
   ↓ ↓ ↓ ↓ ↓ ↓ ↓
   + + + + + + +
- each letter increments count
count: a:3 n:1 g:1 r:1 m:1

Step 2: scan t = n a g a r a m
   ↓ ↓ ↓ ↓ ↓ ↓ ↓
   - - - - - - -
- each letter decrements count
count: a:0 n:0 g:0 r:0 m:0

Step 3: all counts are zero -> valid anagram
```

**Result:** `true`
