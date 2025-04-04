# Automate the Boring Stuff with Python - Part 6: Dictionaries

## Introduction
- Dictionaries are **mutable collections of many values**, similar to lists [1].
- Unlike lists that use integer indexes, dictionaries use **keys** which can be of many different data types [1].

## Creating Dictionaries
- Dictionaries are created using **curly braces `{}`** [1, 2].
- Inside the curly braces, you define **key-value pairs** separated by a colon `:` [1].
  - Example: `{'size': 'fat'}` where `'size'` is the key and `'fat'` is the value [1].
- You can display a dictionary by entering its name [1].
- You can access values by referencing their keys using **bracket notation** `[]` [1].
  - Example: `my_dict['key']`
- Keys can be integers or other data types [1].
  - Example: `{1: 'one', 2: 'two'}` [1].

## Unordered Nature of Dictionaries
- **Dictionaries are not ordered** [1]. The order in which key-value pairs are defined does not determine equality [1].
- Two dictionaries with the same key-value pairs, but in a different order, will evaluate to `True` when compared [1].

## Key Errors
- Trying to access a key that does not exist in a dictionary will result in a **KeyError** [2, 3].
  - Example: If dictionary `x` does not have a key `'color'`, `x['color']` will raise a `KeyError: 'color'` [3].

## Use Cases for Dictionaries
- Dictionaries are powerful because they allow associating a value with a specific key [3].
- Example: Storing birthdays where people's names are keys and their birthdays are values [3].
- You can check if a key exists in a dictionary using the `in` keyword [2-4].
  - Example: `if 'Alice' in birthdays:` [3].
- You can add new key-value pairs to a dictionary by assigning a value to a new key using bracket notation [3].
  - Example: `birthdays['Eve'] = 'December 5th'` [3].

## Dictionary Methods
- **`keys()`**: Returns a list-like view object of all the keys in the dictionary [5].
  - Example: `spam.keys()`
- **`values()`**: Returns a list-like view object of all the values in the dictionary [5].
  - Example: `spam.values()`
- **`items()`**: Returns a list-like view object of all the key-value pairs in the dictionary as tuples [5].
  - Example: `spam.items()`
- You can loop through the keys, values, or items of a dictionary using these methods with a `for` loop [5].
  - Example (looping through values): `for v in spam.values(): print(v)` [5].
  - Example (looping through keys): `for k in spam.keys(): print(k)` [5].
  - Example (looping through items): `for k, v in spam.items(): print(k, v)` [5].

## Checking for Existence (Revisited)
- You can check if a key exists using `key in my_dict` which implicitly checks the keys [2, 4].
- You can explicitly check if a key exists using `key in my_dict.keys()` [2, 4].
- You can check if a value exists using `value in my_dict.values()` [4, 6].
- You can check if a key does *not* exist using `key not in my_dict.keys()` [4].

## The `get()` Method
- The `get()` method takes two arguments: the key to retrieve and a **fallback value** to return if the key does not exist [4].
- This is a useful way to avoid `KeyError`s [4].
- Example: `picnic_items.get('cups', 0)` will return the value associated with the key `'cups'` if it exists; otherwise, it will return `0` [4].

## The `setdefault()` Method
- The `setdefault()` method checks if a key exists in the dictionary.
- If the key exists, it returns the key's value [7].
- If the key does not exist, it inserts the key with a specified default value into the dictionary and returns that value [7].
- This provides a shorthand to ensure a key exists with a certain default value [4, 6].
- Example: `spam.setdefault('color', 'black')` will add the key `'color'` with the value `'black'` to the `spam` dictionary if `'color'` doesn't already exist [6, 7].

## Example: Character Counting
- The `setdefault()` method is particularly useful for tasks like counting the occurrences of characters in a string [7].
- By iterating through the string and using `setdefault(character, 0)` followed by incrementing the value, you can efficiently count character frequencies [7].

## Pretty Printing
- The `pprint` module in Python provides a `pprint()` function that can display dictionary values in a more organized and readable format than the standard `print()` function, especially for nested dictionaries [6, 7].
- To use it, you first need to import the module: `import pprint` [6, 7].
- Then, you can call the function: `pprint.pprint(my_dict)` [6, 7].

## Modeling Data with Dictionaries
- Dictionaries can be used to model real-world scenarios and data structures [8].
- Example: Representing a chessboard using algebraic notation where keys like `'1h'` map to piece names like `'bking'` [8].
- Example: Modeling a Tic-Tac-Toe board where keys represent positions (`'top-L'`, `'mid-M'`, etc.) and values represent the state of that position (`'X'`, `'O'`, `' '`) [8, 9].

## Nested Dictionaries
- Dictionaries can be nested within other dictionaries, allowing for more complex hierarchical data organization [2, 9].
- Example: Organizing picnic items by who is bringing them, where the keys are item names and the values are dictionaries of people and the quantity they are bringing [9].

## Practice Questions and Answers
- **What does the code for an empty dictionary look like?** `{}` [2]
- **What does the dictionary value with the key 'foo' and the value 42 look like?** `{'foo': 42}` [2]
- **What is the main difference between a dictionary and a list?** A dictionary stores **key-value pairs** and is **unordered**, with keys that can be of different data types. A list is **ordered** and its elements are accessed by **integer indexes** [2].
- **What happens if you try to access the key 'foo' inside the spam dictionary if spam doesn't have a key like that?** A **KeyError** will be raised [2, 3].
- **If a dictionary is stored in spam, what is the difference between the expression `'cat' in spam` and `'cat' in spam.keys()`?** By default, when you use the `in` operator with a dictionary, it checks if the value exists as a **key**. Therefore, there is **no effective difference** between `'cat' in spam` and `'cat' in spam.keys()` [2].
- **If a dictionary is stored in spam, what is the difference between the expression `'cat' in spam` and `'cat' in spam.values()`?** `'cat' in spam` checks if `'cat'` exists as a **key** in the `spam` dictionary, while `'cat' in spam.values()` checks if `'cat'` exists as a **value** in any of the key-value pairs within `spam` [6].
- **What is the shortcut for the following code?**
  ```python
  if 'color' not in spam:
      spam['color'] = 'black'
The shortcut is to use the setdefault() method: spam.setdefault('color', 'black').

• What module and function can be used to pretty print dictionary values? The pprint module and its pprint() function.

## Conclusion

• Dictionaries are a versatile and essential data structure in Python for storing and organizing data using key-value pairs.

•
Understanding the properties and methods of dictionaries is crucial for effective programming.
