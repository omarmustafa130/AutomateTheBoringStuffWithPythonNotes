
# 🐍 Regular Expressions in Python with the `re` Module

## 📘 Introduction

Regular expressions (regex) are a powerful tool for **searching and manipulating patterns in text**. In Python, the `re` module makes it easy to integrate regex into your programs for tasks like validating emails, extracting phone numbers, and more.

This guide expands on the concepts from *Automate the Boring Stuff with Python* - Chapter 8.

---

## 🚫 The Problem Without Regular Expressions

To validate a U.S. or Canadian phone number like `415-555-4242`, you'd have to:

```python
def is_phone_number(text):
    if len(text) != 12:
        return False
    if text[3] != '-' or text[7] != '-':
        return False
    if not (text[:3] + text[4:7] + text[8:]).isdigit():
        return False
    return True
```

This only works for one format, and you'd need even more code to support other formats.

---

## ✅ Solving the Problem with Regular Expressions

### Creating a Regex Object

```python
import re
phone_regex = re.compile(r'\d{3}-\d{3}-\d{4}')
```

Use **raw strings** (`r''`) to prevent Python from interpreting backslashes as escape sequences.

### Searching for a Pattern

```python
mo = phone_regex.search("My number is 415-555-4242.")
print("Phone number found:", mo.group())
```

### Finding All Matches

```python
text = "Call 415-555-4242 or 408-555-9999."
all_matches = phone_regex.findall(text)
print(all_matches)
```

### Grouping with Parentheses

```python
phone_regex = re.compile(r'(\d{3})-(\d{3}-\d{4})')
mo = phone_regex.search("Call me at 415-555-4242.")
print(mo.groups())  # ('415', '555-4242')
```

### Pipe `|` for Multiple Options

```python
bat_regex = re.compile(r'Bat(man|mobile|copter|woman)')
mo = bat_regex.search("Batmobile lost a wheel")
print(mo.group())      # Batmobile
print(mo.group(1))     # mobile
```

### Optional `?`, Zero-or-More `*`, One-or-More `+`

```python
re.compile(r'Bat(wo)?man')     # Optional "wo"
re.compile(r'Bat(wo)*man')     # Zero or more "wo"
re.compile(r'Bat(wo)+man')     # One or more "wo"
```

### Specific Repetitions `{}`

```python
ha_regex = re.compile(r'(Ha){3}')
print(ha_regex.search("HaHaHa").group())  # HaHaHa
```

---

## 🔁 Greedy vs Non-Greedy Matching

- `.*` matches as much as possible (greedy)
- `.*?` matches as little as possible (non-greedy)

---

## 🔤 Character Classes

| Class | Description |
|-------|-------------|
| `\d` | Digit (0-9) |
| `\D` | Not a digit |
| `\w` | Word char (letters, digits, _) |
| `\W` | Not a word char |
| `\s` | Whitespace |
| `\S` | Not whitespace |

Custom classes:

```python
re.compile(r'[aeiouAEIOU]')  # vowels
re.compile(r'[^0-9]')        # not digits
```

---

## 📍 Anchors and Wildcards

- `^Hello` → begins with Hello
- `\d+$` → ends with digits
- `.` → matches any character (except newline)

To include newline: `re.DOTALL`

---

## 🔡 Case-Insensitive Matching

```python
re.compile(r'robocop', re.IGNORECASE)
```

---

## 🔄 Substitution

```python
re.compile(r'Agent \w+').sub('CENSORED', "Agent Alice met Agent Bob.")
# → CENSORED met CENSORED

re.compile(r'Agent (\w)\w*').sub(r'\1****', "Agent Alice and Agent Carol")
# → A**** and C****
```

---

## 🧼 Verbose Mode

```python
phone_regex = re.compile(r'''(
    (\d{3}|\(\d{3}\))?        # area code
    (\s|-|\.)?                  # separator
    \d{3}                        # first 3 digits
    (\s|-|\.)                   # separator
    \d{4}                        # last 4 digits
    (\s*(ext|x|ext.)\s*\d{2,5})?  # extension
)''', re.VERBOSE)
```

---

## 🔐 Escaping Special Characters

To match a literal `.` or `(`, use a backslash: `\.` or `\(`

---

## 📦 Mini Project: Extract Phone Numbers & Emails

```python
import re, pyperclip

phone_regex = re.compile(r'''
    (\d{3}|\(\d{3}\))?       # area code
    (\s|-|\.)?                 # separator
    \d{3}                       # first 3 digits
    (\s|-|\.)                  # separator
    \d{4}                       # last 4 digits
    (\s*(ext|x|ext.)\s*\d{2,5})?  # extension
''', re.VERBOSE)

email_regex = re.compile(r'[\w.+-]+@[\w-]+\.[a-z]{2,}')

text = pyperclip.paste()

matches = phone_regex.findall(text)
emails = email_regex.findall(text)
all_matches = [match[0] for match in matches] + emails

pyperclip.copy('\n'.join(all_matches))
```

---

## 📝 Common Regex Symbols Summary

| Symbol | Meaning |
|--------|---------|
| `?`    | Optional |
| `*`    | 0 or more |
| `+`    | 1 or more |
| `{n}`  | Exactly n |
| `{m,n}`| Between m and n |
| `^`    | Start of string |
| `$`    | End of string |
| `.`    | Any char (except `\n`) |
| `[]`   | Character class |
| `|`    | Or |
| `()`   | Group |

---

## 🧠 Practice Suggestions

Try writing regexes for:

- U.S. Social Security numbers
- Time formats like `HH:MM`
- Hex color codes `#a1b2c3`
- URL formats

---

## 🧾 Conclusion

With the `re` module, you can efficiently search, extract, and manipulate complex text patterns in Python. Mastering regular expressions is an essential step toward becoming a power user in automation and data processing tasks.

---

Happy coding! 🚀
