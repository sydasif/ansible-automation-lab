# YAML Basics for Ansible Beginners

YAML ("YAML Ain't Markup Language") is the backbone of Ansible playbooks. It is simple, human-readable, and designed for configuration tasks. Let’s walk through the basics to help new learners.

## Structure of YAML Files

YAML files often start with three dashes (`---`) to mark the beginning of a document. This is optional in Ansible, but it’s considered good practice.

### Key Features of YAML

#### 1. **Comments**

Use `#` to add comments. These are ignored by the parser.

```yaml
# This is a comment
name: John Doe  # Inline comment
```

#### 2. **Key-Value Pairs**

The simplest data structure in YAML is a key-value pair:

```yaml
name: John Doe
age: 30
```

Keys must be unique within the same level.

#### 3. **Strings**

Strings can be written with or without quotes. Use quotes if the string contains special characters or spaces.

```yaml
name: "John Doe"
title: Software Developer
```

#### 4. **Booleans**

YAML supports boolean values, written as `true`/`false` or `yes`/`no`:

```yaml
enabled: true
debug: no
```

#### 5. **Lists**

Lists in YAML are ordered collections, written with dashes (`-`):

```yaml
fruits:
  - Apple
  - Banana
  - Cherry
```

Or inline:

```yaml
fruits: [Apple, Banana, Cherry]
```

#### 6. **Dictionaries**

Dictionaries are collections of key-value pairs:

```yaml
person:
  name: John Doe
  age: 30
  city: New York
```

You can also write them inline:

```yaml
person: {name: John Doe, age: 30, city: New York}
```
#### 7. **Multi-Line Strings**

For long strings, YAML provides two ways to write them:

##### Folded Style (`>`)

Collapses into a single line, keeping spaces:

```yaml
address: >
  123 Main Street,
  Springfield, USA
```

Result:

```plaintext
123 Main Street, Springfield, USA
```

##### Literal Style (`|`)

Preserves line breaks:

```yaml
description: |
  This is a multi-line string.
  The line breaks will be preserved.
```

Result:

```plaintext
This is a multi-line string.
The line breaks will be preserved.
```

#### 8. **Indentation and Formatting**

- YAML uses spaces for indentation. Never use tabs.
- Ensure consistent indentation for readability and proper parsing.

## Summary

- YAML is simple and human-readable.
- Start with basic key-value pairs and move on to lists and dictionaries.
- Use comments to make your playbooks more understandable.
- Leverage multi-line strings to keep files clean and organized.

Mastering YAML is the first step in writing effective Ansible playbooks. With this foundation, you're ready to start automating tasks!
