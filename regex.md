# Regex Basics Cheat Sheet

## What is Regex?
Regular expressions (regex) are patterns used to match character combinations in strings.

## Common Syntax

| Pattern | Matches                          |
|---------|----------------------------------|
| `.`     | Any character except newline     |
| `^`     | Start of string                  |
| `$`     | End of string                    |
| `*`     | 0 or more of the preceding item  |
| `+`     | 1 or more of the preceding item  |
| `?`     | 0 or 1 of the preceding item     |
| `{n}`   | Exactly n repetitions            |
| `{n,}`  | n or more repetitions            |
| `{n,m}` | Between n and m repetitions      |
| `\|`    | Alternation (OR)                 |
| `()`    | Grouping                         |
| `[]`    | Character class                  |
| `\`     | Escape special character         |

## Character Classes

| Pattern   | Matches                         |
|-----------|---------------------------------|
| `[abc]`   | a, b, or c                      |
| `[^abc]`  | Not a, b, or c                  |
| `[a-z]`   | Any lowercase letter            |
| `[A-Z]`   | Any uppercase letter            |
| `[0-9]`   | Any digit                       |
| `[a-zA-Z]`| Any letter                      |

## Predefined Character Classes

| Pattern | Matches                     |
|---------|-----------------------------|
| `\d`    | Digit (0–9)                 |
| `\D`    | Non-digit                   |
| `\w`    | Word character (a–z, A–Z, 0–9, _) |
| `\W`    | Non-word character          |
| `\s`    | Whitespace                  |
| `\S`    | Non-whitespace              |

## Anchors

| Pattern | Meaning            |
|---------|--------------------|
| `^`     | Start of string    |
| `$`     | End of string      |
| `\b`    | Word boundary      |
| `\B`    | Non-word boundary  |

## Common Examples

```regex
^abc$                # Exact match: "abc"
a|b                  # 'a' or 'b'
\d{3}-\d{2}-\d{4}    # Social Security number format
[A-Za-z]+            # One or more letters
````

## Flags (in most languages)

| Flag | Description                              |
| ---- | ---------------------------------------- |
| `i`  | Case-insensitive                         |
| `g`  | Global search                            |
| `m`  | Multiline mode (`^`/`$` match line ends) |
| `s`  | Dot matches newline                      |

---

Reference: [Regular Expressions Info](https://www.regular-expressions.info/)
