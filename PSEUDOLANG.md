# PseudoLang v1.3

## Overview

PseudoLang is a lightweight, model-agnostic pseudocode format for software development.

Its purpose is to describe behavior, structure, and requirements in a clear, structured way so that any AI can convert it into executable code.

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

A function may return a value using `RETURN`.

If a function does not return a value, it is treated as a procedure.

| Keyword  | Description                       |
| -------- | --------------------------------- |
| FUNCTION | Defines a callable block of logic |
| RETURN   | Returns a value or result         |
| END      | Closes a block                    |

---

## Object-Oriented Programming

### Classes

```pseudolang
CLASS User

    PROPERTY id
    PROPERTY name
    PROPERTY email

END
```

| Keyword  | Description            |
| -------- | ---------------------- |
| CLASS    | Defines an object type |
| PROPERTY | Defines object data    |

---

### Constructors

```pseudolang
CLASS User

    PROPERTY name
    PROPERTY email

    CONSTRUCTOR(name, email)

        THIS.name = name
        THIS.email = email

    END

END
```

| Keyword     | Description                    |
| ----------- | ------------------------------ |
| CONSTRUCTOR | Initializes an object          |
| THIS        | Refers to the current instance |

---

### Methods

Methods use the same FUNCTION syntax as regular functions.

```pseudolang
CLASS User

    FUNCTION GetDisplayName()

        RETURN THIS.name

    END

END
```

---

### Inheritance

```pseudolang
CLASS AdminUser EXTENDS User

END
```

| Keyword | Description                 |
| ------- | --------------------------- |
| EXTENDS | Inherits from another class |

---

### Interfaces

```pseudolang
INTERFACE UserRepository

    FUNCTION FindById(id)

    FUNCTION Save(user)

END
```

```pseudolang
CLASS SqlUserRepository IMPLEMENTS UserRepository

END
```

| Keyword    | Description                       |
| ---------- | --------------------------------- |
| INTERFACE  | Defines a contract                |
| IMPLEMENTS | Implements one or more interfaces |

---

### Abstract Classes

```pseudolang
ABSTRACT CLASS Repository

    FUNCTION FindById(id)

END
```

```pseudolang
CLASS UserRepository EXTENDS Repository

END
```

| Keyword  | Description                                          |
| -------- | ---------------------------------------------------- |
| ABSTRACT | Defines an abstract type that cannot be instantiated |

---

### Combined Relationships

```pseudolang
CLASS UserRepository
    EXTENDS BaseRepository
    IMPLEMENTS Repository, Cacheable

END
```

Or in a single line:

```pseudolang
CLASS UserRepository EXTENDS BaseRepository IMPLEMENTS Repository, Cacheable

END
```

---

### Object Creation

```pseudolang
user = NEW User(name, email)
```

| Keyword | Description                |
| ------- | -------------------------- |
| NEW     | Creates an object instance |

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

## Data Operations

These are recommended actions, not reserved words.

| Action      | Description                   |
| ----------- | ----------------------------- |
| FIND        | Retrieve a single record      |
| FIND_ALL    | Retrieve multiple records     |
| CREATE      | Create a new record           |
| UPDATE      | Update an existing record     |
| DELETE      | Delete a record               |
| UPSERT      | Create or update a record     |
| EXISTS      | Check whether a record exists |
| COUNT       | Count matching records        |
| SAVE        | Persist changes               |
| TRANSACTION | Execute operations atomically |

### Examples

```pseudolang
user = FIND User WHERE email == email

users = FIND_ALL User WHERE isActive == true

exists = EXISTS User WHERE email == email

count = COUNT User WHERE status == "active"

CREATE User

UPDATE User

DELETE User

UPSERT User
```

```pseudolang
TRANSACTION

    CREATE User

    CREATE AuditLog

END
```

---

# Operators

PseudoLang supports a minimal set of language-agnostic operators.

---

## Assignment

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

```pseudolang
IF user == null
    RETURN error
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

```pseudolang
total = price * quantity
counter += 1
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

| Operator | Description         |
| -------- | ------------------- |
| +=       | Add and assign      |
| -=       | Subtract and assign |
| *=       | Multiply and assign |
| /=       | Divide and assign   |

---

## Collection Access

```pseudolang
user = users[0]
```

| Operator | Description  |
| -------- | ------------ |
| []       | Index access |

---

## Member Access

```pseudolang
user.email
```

| Operator | Description     |
| -------- | --------------- |
| .        | Property access |

---

## Safe Navigation

```pseudolang
email = user?.email
```

| Operator | Description             |
| -------- | ----------------------- |
| ?.       | Null-safe member access |

---

## Null Coalescing

```pseudolang
name = user.name ?? "Guest"
```

| Operator | Description                                  |
| -------- | -------------------------------------------- |
| ??       | Return fallback value when left side is null |

---

## Range

```pseudolang
FOR i IN 1..10

END
```

| Operator | Description |
| -------- | ----------- |
| ..       | Range       |

---

## Membership

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

INTERFACE UserRepository

    FUNCTION FindByEmail(email)

END

ABSTRACT CLASS BaseRepository

    FUNCTION Save(entity)

END

CLASS SqlUserRepository EXTENDS BaseRepository IMPLEMENTS UserRepository

    FUNCTION FindByEmail(email)

        RETURN FIND User WHERE email == email

    END

END

CLASS AuthService

    PROPERTY repository

    CONSTRUCTOR(repository)

        THIS.repository = repository

    END

    FUNCTION Login(email, password)

        user = THIS.repository.FindByEmail(email)

        IF user == null
            RETURN unauthorized
        END

        IF NOT VerifyPassword(password, user.passwordHash)
            RETURN unauthorized
        END

        token = GenerateJWT(user)

        RETURN token

    END

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
