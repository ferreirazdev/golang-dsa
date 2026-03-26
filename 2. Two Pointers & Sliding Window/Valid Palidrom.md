# Valid Palindrome

## Example Walkthrough

**Input**

```text
s = "A man, a plan, a canal: Panama"
```

**Goal**

Return `true` if `s` is a palindrome after:

- ignoring non-alphanumeric characters
- comparing characters case-insensitively

Otherwise, return `false`.

## Steps

Use two pointers, `l` (left) and `r` (right).

```text
l = 0, r = len(s) - 1
while l < r:
  if s[l] is not alphanumeric: l++
  else if s[r] is not alphanumeric: r--
  else if lower(s[l]) != lower(s[r]): return false
  else: l++, r--
return true
```

## Flowchart (original)

```text
| l   | r   | s[l]       | s[r]     | Action |
| --- | --- | ---------- | -------- | ------ |
| 0   | end | 'A'        | 'a'      | equal  |
| →   | ←   | skip space | skip ':' |        |
| ... | ... | 'm'        | 'm'      | equal  |

            ┌───────────────┐
            │    START      │
            └──────┬────────┘
                   │
                   ▼
      ┌─────────────────────────┐
      │ l = 0, r = len(s) - 1  │
      └────────┬────────────────┘
               │
               ▼
        ┌───────────────┐
        │  l < r ?      │
        └──────┬────────┘
               │Yes
               ▼
   ┌──────────────────────────────┐
   │ is s[l] alphanumeric?        │
   └──────┬───────────────────────┘
          │No
          ▼
      l++ (skip) ────────┐
                         │
                         ▼
              (repeat check)
                         │
          Yes            ▼
   ┌──────────────────────────────┐
   │ is s[r] alphanumeric?        │
   └──────┬───────────────────────┘
          │No
          ▼
      r-- (skip) ────────┐
                         │
                         ▼
              (repeat check)
                         │
          Yes            ▼
   ┌──────────────────────────────┐
   │ Compare lower(s[l], s[r])    │
   └──────┬───────────────────────┘
          │Not equal
          ▼
      RETURN false ❌

          │Equal
          ▼
   ┌──────────────────────────────┐
   │ l++, r-- (move inward)       │
   └──────────────┬───────────────┘
                  │
                  ▼
              (loop again)

                  │No (l >= r)
                  ▼
        ┌───────────────┐
        │ RETURN true ✅ │
        └───────────────┘
```

## Result

`true`

## Go Solution

```go
package main

import "unicode"

func isPalindrome(s string) bool {
	// Convert to runes so we can index safely while comparing.
	runes := []rune(s)
	l, r := 0, len(runes)-1

	for l < r {
		// Move l to the next alphanumeric character.
		for l < r && !isAlphaNum(runes[l]) {
			l++
		}
		// Move r to the next alphanumeric character.
		for l < r && !isAlphaNum(runes[r]) {
			r--
		}

		// Compare case-insensitively.
		if unicode.ToLower(runes[l]) != unicode.ToLower(runes[r]) {
			return false
		}

		l++
		r--
	}

	return true
}

func isAlphaNum(ch rune) bool {
	return unicode.IsLetter(ch) || unicode.IsDigit(ch)
}
```

## Complexity

- Time: `O(n)`
- Space: `O(n)` (due to `[]rune` conversion)