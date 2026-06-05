# PseudoLang v1

## Overview

PseudoLang is a lightweight, model-agnostic pseudocode format for software development.

Its purpose is to describe behavior and requirements in a clear, structured way so that any AI can convert it into executable code.

PseudoLang is not a programming language. It is an intermediate specification between human intent and implementation.

---

# Structure

```pseudolang
GOAL:
    What to build

TARGET:
    Technology stack

CONSTRAINTS:
    Optional requirements

CODE:
    Pseudocode implementation
```

---

# Reserved Words

## Metadata

| Keyword     | Description                                                           |
| ----------- | --------------------------------------------------------------------- |
| GOAL        | Defines the objective of the implementation                           |
| TARGET      | Defines the target language, framework, platform, or technology stack |
| CONSTRAINTS | Defines mandatory requirements or limitations                         |
| CODE        | Contains the pseudocode implementation                                |

---

## Functions

Functions declare parameters directly in the signature.

```pseudolang
FUNCTION Login(email, password)

    ...

END
```

```pseudolang
FUNCTION SendEmail(recipient, subject, content)

    ...

END
```

A function may return a value using `RETURN`.

If a function does not return a value, it is treated as a procedure.

| Keyword  | Description                       |
| -------- | --------------------------------- |
| FUNCTION | Defines a callable block of logic |
| RETURN   | Returns a value or result         |
| END      | Closes a block                    |

---

## Conditions

| Keyword | Description                                |
| ------- | ------------------------------------------ |
| IF      | Starts a conditional statement             |
| ELSE IF | Additional conditional branch              |
| ELSE    | Alternative branch when condition is false |

---

## Loops

| Keyword  | Description                               |
| -------- | ----------------------------------------- |
| FOR      | Repeats a block for a fixed iteration     |
| FOREACH  | Iterates through a collection             |
| WHILE    | Repeats a block while a condition is true |
| BREAK    | Stops the current loop                    |
| CONTINUE | Skips to the next iteration               |

---

## Common Operations

These are recommended actions, not reserved words.

| Action   | Description                 |
| -------- | --------------------------- |
| CREATE   | Create a resource           |
| READ     | Retrieve data               |
| UPDATE   | Modify data                 |
| DELETE   | Remove data                 |
| VALIDATE | Check correctness of data   |
| SAVE     | Persist data                |
| FIND     | Search for data             |
| GENERATE | Produce a value or artifact |
| SEND     | Transmit data               |
| RECEIVE  | Accept data                 |

---

# Operators

PseudoLang supports a minimal set of language-agnostic operators.

---

## Assignment

Assign a value to a variable.

```pseudolang
user = FindUserByEmail(email)
count = 0
isValid = true
```

| Operator | Description  |
| -------- | ------------ |
| =        | Assign value |

---

## Comparison

Compare values.

```pseudolang
IF user == null
    RETURN error
END

IF age >= 18
    RETURN allowed
END
```

| Operator | Description           |
| -------- | --------------------- |
| ==       | Equal                 |
| !=       | Not equal             |
| >        | Greater than          |
| <        | Less than             |
| >=       | Greater than or equal |
| <=       | Less than or equal    |

---

## Logical

Combine conditions.

```pseudolang
IF user != null AND isActive == true
    RETURN success
END
```

| Operator | Description |
| -------- | ----------- |
| AND      | Logical AND |
| OR       | Logical OR  |
| NOT      | Logical NOT |

---

## Arithmetic

Perform mathematical operations.

```pseudolang
total = price * quantity
counter = counter + 1
```

| Operator | Description    |
| -------- | -------------- |
| +        | Addition       |
| -        | Subtraction    |
| *        | Multiplication |
| /        | Division       |
| %        | Modulo         |

---

## Compound Assignment

Shortcut assignments.

```pseudolang
counter += 1
total -= discount
score *= multiplier
```

| Operator | Description         |
| -------- | ------------------- |
| +=       | Add and assign      |
| -=       | Subtract and assign |
| *=       | Multiply and assign |
| /=       | Divide and assign   |

---

## Collection Access

Access items in collections.

```pseudolang
user = users[0]
product = products[index]
```

| Operator | Description  |
| -------- | ------------ |
| []       | Index access |

---

## Member Access

Access object properties.

```pseudolang
user.email
user.name
order.total
```

| Operator | Description     |
| -------- | --------------- |
| .        | Property access |

---

## Safe Navigation

Access a property only when the object exists.

```pseudolang
email = user?.email
```

| Operator | Description             |
| -------- | ----------------------- |
| ?.       | Null-safe member access |

---

## Null Coalescing

Provide a fallback value when null.

```pseudolang
name = user.name ?? "Guest"
```

| Operator | Description                                  |
| -------- | -------------------------------------------- |
| ??       | Return fallback value when left side is null |

---

## Range

Define iteration ranges.

```pseudolang
FOR i IN 1..10
    PRINT i
END
```

| Operator | Description |
| -------- | ----------- |
| ..       | Range       |

---

## Membership

Check existence within a collection.

```pseudolang
IF email IN blockedEmails
    RETURN denied
END
```

| Operator | Description                  |
| -------- | ---------------------------- |
| IN       | Exists in collection         |
| NOT IN   | Does not exist in collection |

---

## Pipeline

Pass the result of one operation to the next.

```pseudolang
result = data
    |> Validate
    |> Transform
    |> Save
```

| Operator | Description |                                        |
| -------- | ----------- | -------------------------------------- |
|          | >           | Pass previous result to next operation |

Equivalent:

```pseudolang
result = Validate(data)
result = Transform(result)
result = Save(result)
```

---

# Literals

| Literal | Description   |
| ------- | ------------- |
| null    | No value      |
| true    | Boolean true  |
| false   | Boolean false |

---

# Recommended Precedence

```text
()
.
?.
[]
NOT

* / %

+ -

== != > < >= <=

IN
NOT IN

AND

OR

??

|>

=
```

---

# Example

```pseudolang
FUNCTION Login(email, password)

    user = FindUserByEmail(email)

    IF user == null
        RETURN unauthorized
    END

    IF NOT VerifyPassword(password, user.passwordHash)
        RETURN unauthorized
    END

    token = GenerateJWT(user)

    RETURN token

END
```

---

# Complete Example

```pseudolang
GOAL:
    User authentication service

TARGET:
    C# ASP.NET Core

CONSTRAINTS:
    JWT authentication
    Clean architecture

CODE:

FUNCTION Login(email, password)

    user = FindUserByEmail(email)

    IF user == null
        RETURN unauthorized
    END

    IF NOT VerifyPassword(password, user.passwordHash)
        RETURN unauthorized
    END

    token = GenerateJWT(user)

    RETURN token

END
```

---

# Interpretation Rules

1. CODE is the source of truth.
2. GOAL provides implementation context.
3. TARGET determines the output technology.
4. CONSTRAINTS are mandatory.
5. Missing implementation details may be inferred.
6. Generated code must preserve the described behavior.
7. Generated code should follow the best practices of the target technology.

---

# Design Principles

1. Human-readable first.
2. Language-agnostic.
3. Model-agnostic.
4. Minimal reserved words.
5. Behavior-focused rather than implementation-focused.
6. Familiar to developers regardless of programming background.
7. Easy for AI systems to translate into executable code.

```
```
