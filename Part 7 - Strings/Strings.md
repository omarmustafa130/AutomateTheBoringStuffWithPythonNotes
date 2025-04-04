# Study Notes: Working with Strings in Python

## String Creation [1]
*   Strings can be created using **single quotes** (`'`) or **double quotes** (`"`) [1].
*   **Issue with using the same quote within a string:**
    *   Python interprets the second identical quote as the end of the string, leading to a syntax error [1].
    *   Example: `'Alice's cat'` will cause an error [1].
*   **Solutions:**
    *   Use the **other type of quote** to enclose the string. For example, `"Alice's cat"` or `'He said, "Hello!"'` [1].
    *   Use an **escape character** (`\`) before the quote you want to include [1]. For example, `'Alice\'s cat'` [1].

## Escape Characters [1, 2]
*   Escape characters allow you to include characters in a string that are otherwise difficult to represent [1].
*   The backslash (`\`) is the escape character [1].
*   Common escape characters:
    *   `\'`: Single quote [1, 3]
    *   `\"`: Double quote [1]
    *   `\t`: Tab [1, 2]
    *   `\n`: Newline [1, 2]
    *   `\\`: Backslash itself [2]

## Raw Strings [2, 4]
*   **Raw strings** ignore the meaning of escape characters [4].
*   Created by prefixing the string literal with an `r` [4].
*   Example: `r'C:\Users\Documents'` will treat `\` as a literal backslash [2, 4].
*   Useful for regular expressions and file paths [4].

## Multi-line Strings [2, 4]
*   Used for long blocks of text [4].
*   Created using **three single quotes** (`'''`) or **three double quotes** (`"""`) at the beginning and end of the string [4].
*   Newlines within the triple quotes are automatically included in the string [2, 4].

## Multi-line Comments [4]
*   Triple single or double quotes can also be used for **multi-line comments** to describe code [4].

## String Indexing and Slicing [2, 5]
*   Strings are ordered sequences, and each character has an **index**, starting from 0 [5].
*   Individual characters can be accessed using **bracket notation** with the index [5].
    *   Example: `spam` gives the first character [5].
    *   Negative indexing can be used to access characters from the end (e.g., `spam[-1]` is the last character) [5].
*   **Slicing** allows you to extract substrings [2, 5].
    *   Syntax: `[start:end]`. Includes characters from `start` up to (but not including) `end` [5].
    *   Omitting `start` defaults to the beginning [2, 5].
    *   Omitting `end` defaults to the end [2, 5].
    *   Example: `hello_world[0:5]` or `hello_world[:5]` gives `"hello"` [2, 5].
    *   Example: `hello_world[3:]` gives `"lo world"` [2].

## Checking for Substrings [5]
*   The `in` operator checks if a substring exists within a string [5]. Returns `True` or `False` [5].
    *   Example: `'hello' in 'hello world'` evaluates to `True` [5].
*   The `not in` operator checks if a substring does not exist within a string [5]. Returns `True` or `False` [5].
    *   Example: `'HELLO' not in 'hello world'` evaluates to `True` (case-sensitive) [5].

## String Interpolation (f-strings) [5]
*   **f-strings** provide a concise way to embed expressions inside string literals [5].
*   Prefix the string with an `f` [5].
*   Variables or expressions within curly braces `{}` are evaluated and inserted into the string [5].
    *   Example: `name = 'Al'; age = 4000; print(f'My name is {name} and I am {age}.')` [5].
*   Supported in Python 3.6 and later [5].

## String Methods [6-12]
*   String methods are built-in functions that can be called on string objects to perform various operations [6].
*   **Case Manipulation:**
    *   `.upper()`: Returns a new string with all characters in uppercase [6, 11].
    *   `.lower()`: Returns a new string with all characters in lowercase [6, 11].
    *   `.isupper()`: Returns `True` if all characters in the string are uppercase and the string is not empty, `False` otherwise [6].
    *   `.islower()`: Returns `True` if all characters in the string are lowercase and the string is not empty, `False` otherwise [6].
*   **Checking String Content:** [6, 7]
    *   `.isalpha()`: Returns `True` if the string consists only of letters and is not blank [6].
    *   `.isdecimal()`: Returns `True` if the string consists only of numeric characters and is not blank [6, 7].
    *   `.isalnum()`: Returns `True` if the string consists only of letters or numbers and is not blank [7].
    *   `.isspace()`: Returns `True` if the string consists only of whitespace characters and is not blank [7].
    *   `.istitle()`: Returns `True` if the string is titlecased (first letter of each word is uppercase) and contains at least one letter [7].
    *   `.startswith(prefix)`: Returns `True` if the string begins with the specified `prefix` [7].
    *   `.endswith(suffix)`: Returns `True` if the string ends with the specified `suffix` [7].
*   **Working with Lists and Strings:** [7, 8, 11]
    *   `.join(iterable)`: Concatenates the elements of an `iterable` (like a list) into a single string, using the string on which the method is called as a separator [7, 11].
        *   Example: `', '.join(['apples', 'bananas', 'cherries'])` gives `'apples, bananas, cherries'` [7].
    *   `.split(sep=None)`: Splits the string into a list of substrings. If `sep` is not provided, it splits on whitespace [8, 11].
        *   Example: `'My name is Simon'.split()` gives `['My', 'name', 'is', 'Simon']` [8, 11].
        *   Example: `'sentence1. sentence2.'.split('.')` gives `['sentence1', ' sentence2', '']` [8].
        *   Example: `'line1\nline2\nline3'.split('\n')` gives `['line1', 'line2', 'line3']` [8].
    *   `.partition(sep)`: Splits the string at the first occurrence of `sep` and returns a tuple containing the part before `sep`, the `sep` itself, and the part after `sep` [8].
        *   Example: `'hello world'.partition('w')` gives `('hello ', 'w', 'orld')` [8].
        *   Example: `'hello world'.partition('world')` gives `('hello ', 'world', '')` [8].
*   **Adjusting String Alignment:** [8, 9, 11, 12]
    *   `.rjust(width, fillchar=' ')`: Returns a right-justified string of a specified `width`. The remaining space on the left is filled with `fillchar` (default is a space) [8, 9, 12].
    *   `.ljust(width, fillchar=' ')`: Returns a left-justified string of a specified `width`. The remaining space on the right is filled with `fillchar` (default is a space) [9, 12].
    *   `.center(width, fillchar=' ')`: Returns a centered string of a specified `width`. The remaining space on both sides is filled with `fillchar` (default is a space) [9, 12].
*   **Removing Whitespace:** [10, 12]
    *   `.strip()`: Returns a new string with leading and trailing whitespace removed [10, 12].
    *   `.lstrip()`: Returns a new string with leading whitespace removed [10, 12].
    *   `.rstrip()`: Returns a new string with trailing whitespace removed [10, 12].

## Unicode and Character Codes [10]
*   Each character has a unique numeric value called a **Unicode code point** [10].
*   `ord(char)`: Returns the Unicode code point of a single-character string [10].
    *   Example: `ord('A')` returns `65` [10].
*   `chr(code)`: Returns the string representing a character whose Unicode code point is the integer `code` [10].
    *   Example: `chr(65)` returns `'A'` [10].
*   Useful for comparing and ordering characters [13].

## Working with the Clipboard (paperclip module) [12-14]
*   The `paperclip` module allows Python to interact with the system clipboard [13].
*   It's a third-party module and needs to be installed (e.g., using `pip install paperclip`) [13].
*   `paperclip.copy(text)`: Copies the given `text` to the clipboard [13].
*   `paperclip.paste()`: Returns the text currently in the clipboard [13].
*   Example program demonstrates using `paperclip` to store and retrieve predefined messages based on keywords provided as command-line arguments [13, 14].


## Practice Questions and Answers [2, 3, 11, 12]
*   **What are escape characters?** Used within strings for special meaning, like including quotes or newlines [3].
*   **What do `\n` and `\t` represent?** `\n` is a newline, and `\t` is a tab [2].
*   **How can you put a backslash in a string?** Use a raw string (e.g., `r'\'`) or escape it (e.g., `'\\'`) [2].
*   **Why isn't the single quote in "Alice's house" a problem if the string is `'moving castle'`?** The issue arises when the outer quotes are single, and there's an unescaped single quote inside. In `'moving castle'`, there are no such conflicts. For "Alice's house", using double quotes like `"Alice's house"` solves it [2].
*   **How to write a string with newlines without `\n`?** Use triple single or double quotes and include the newlines directly in the text [2].
*   **What does `hello world[1]` evaluate to?** `'e'` (second character, 0-indexed) [2].
*   **What does `hello world[0:5]` evaluate to?** `'hello'` [2].
*   **What does `hello world[:5]` evaluate to?** `'hello'` [2].
*   **What does `hello world[3:]` evaluate to?** `'lo world'` [2].
*   **What does `hello.upper()` evaluate to?** `'HELLO'` [11].
*   **What does `'Hello'.upper().isupper()` evaluate to?** `True` [11].
*   **What does `'Hello'.upper().lower()` evaluate to?** `'hello'` [11].
*   **What does `'Remember, remember, the fifth of November.'.split()` evaluate to?** `['Remember,', 'remember,', 'the', 'fifth', 'of', 'November.']` (splits on whitespace) [11].
*   **What does `'-'.join('There can be only one.'.split())` evaluate to?** `'There-can-be-only-one.'` (splits on whitespace, then joins with '-') [11].
*   **What string methods for right, left, and center justify?** `.rjust()`, `.ljust()`, and `.center()` [12].
*   **How to trim whitespace from beginning/end?** `.strip()`, `.lstrip()`, and `.rstrip()` [12].
Start typing...
1 source




