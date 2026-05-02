# YAML Tutorial: A Complete Guide to Language, Format, and Syntax

## 📘 Introduction

**YAML (YAML Ain't Markup Language)** is a human-readable data serialization language commonly used for configuration files and data exchange. It is often compared to JSON and can serve as a cleaner, more readable alternative.

### Why YAML?
- Easy to read and write
- Supports complex data structures
- Maps naturally to programming data types
- Widely used in DevOps, CI/CD, and configuration management

---

## 🚀 Quick Start: Your First YAML File

```yaml
---
doe: "a deer, a female deer"
ray: "a drop of golden sun"
pi: 3.14159
xmas: true
french-hens: 3
calling-birds:
  - huey
  - dewey
  - louie
  - fred
xmas-fifth-day:
  calling-birds: four
  french-hens: 3
  golden-rings: 5
  partridges:
    count: 1
    location: "a pear tree"
  turtle-doves: two
````

### Key Concepts:

* `---` indicates the start of a YAML document
* Uses **key-value pairs**
* Supports multiple data types:

  * Strings
  * Numbers
  * Booleans
  * Lists (arrays)
  * Dictionaries (objects)

---

## 🔁 YAML vs JSON

Equivalent JSON:

```json
{
  "doe": "a deer, a female deer",
  "ray": "a drop of golden sun",
  "pi": 3.14159,
  "xmas": true,
  "french-hens": 3,
  "calling-birds": ["huey", "dewey", "louie", "fred"],
  "xmas-fifth-day": {
    "calling-birds": "four",
    "french-hens": 3,
    "golden-rings": 5,
    "partridges": {
      "count": 1,
      "location": "a pear tree"
    },
    "turtle-doves": "two"
  }
}
```

---

## 📏 Indentation & Formatting Rules

* YAML uses **spaces (not tabs)** for indentation
* Indentation defines structure and nesting

```yaml
foo: bar
pleh: help
stuff:
  foo: bar
  bar: foo
```

---

## 🐍 Python Example (Using PyYAML)

```python
import yaml

from yaml import load
try:
    from yaml import CLoader as Loader
except ImportError:
    from yaml import Loader

if __name__ == '__main__':
    stream = open("foo.yaml", 'r')
    dictionary = yaml.load(stream, Loader=Loader)
    for key, value in dictionary.items():
        print(key + " : " + str(value))
```

---

## 💬 Comments

```yaml
# This is a full line comment
foo: bar  # Inline comment
```

---

## 🔢 Data Types

### Numbers

```yaml
decimal: 12345
hex: 0x12d4
octal: 023332
float: 1230.15
exp: 12.3015e+05
```

### Special Values

```yaml
infinity: .inf
neg_infinity: -.Inf
not_a_number: .NAN
```

---

## 🔤 Strings

```yaml
normal: this is a string
quoted: "this is a string with \n newline"
single_quote: 'no escape sequences here'
```

### Multi-line Strings

**Folded (`>`)**:

```yaml
text: >
  this is a long
  line that becomes
  a single line
```

**Literal (`|`)**:

```yaml
text: |
  this is preserved
  exactly as written
```

---

## ❓ Null Values

```yaml
foo: ~
bar: null
```

---

## ✅ Boolean Values

```yaml
yes_value: Yes
true_value: True
on_value: On

no_value: No
false_value: False
off_value: Off
```

---

## 📚 Lists (Arrays)

### Inline

```yaml
items: [1, 2, 3, 4]
```

### Multi-line

```yaml
items:
  - 1
  - 2
  - 3
```

### Complex Lists

```yaml
items:
  - thing:
      name: huey
  - thing:
      name: dewey
```

---

## 🧱 Dictionaries (Objects)

```yaml
person:
  name: John
  age: 30
```

### Inline Dictionary

```yaml
person: { name: John, age: 30 }
```

---

## 🔀 Advanced Features

### Chomp Modifiers

```yaml
strip: |-
  removes trailing newline

keep: >+
  preserves trailing newline
```

---

## 📄 Multiple Documents

```yaml
---
foo: bar
...
---
hello: world
```

### Python Example

```python
dictionary = yaml.load_all(stream, Loader=Loader)

for doc in dictionary:
    print("New document:")
    for key, value in doc.items():
        print(key + " : " + str(value))
```

---

## 🧠 Summary

YAML is:

* Clean and readable
* Powerful for configuration and data modeling
* Flexible with nested and mixed data types

---

## 📚 Further Learning Topics

* YAML in DevOps (CI/CD pipelines)
* Kubernetes YAML configurations
* Configuration as Code (CasC)
* YAML schema validation

---

## 📌 Conclusion

Mastering YAML helps you:

* Write cleaner configuration files
* Improve readability in projects
* Work efficiently with modern DevOps tools

---

**Happy coding! 🚀**


