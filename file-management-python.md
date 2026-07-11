File and Database Management are essential parts of Python programming. Below are the details with examples.

# 1. File Management in Python

File management refers to creating, reading, writing, appending, and deleting files.

## Common File Modes

| Mode | Description                                     |
| ---- | ----------------------------------------------- |
| `r`  | Read (default)                                  |
| `w`  | Write (creates new or overwrites existing file) |
| `a`  | Append data                                     |
| `x`  | Create a new file                               |
| `rb` | Read binary file                                |
| `wb` | Write binary file                               |

---

## Example 1: Writing to a File

```python
file = open("student.txt", "w")
file.write("Name: John\n")
file.write("Age: 20\n")
file.close()

print("Data written successfully.")
```

**Output (student.txt)**

```
Name: John
Age: 20
```

---

## Example 2: Reading a File

```python
file = open("student.txt", "r")
content = file.read()
print(content)
file.close()
```

**Output**

```
Name: John
Age: 20
```

---

## Example 3: Appending Data

```python
file = open("student.txt", "a")
file.write("Course: Python\n")
file.close()
```

After appending, the file contains:

```
Name: John
Age: 20
Course: Python
```

---

## Example 4: Using `with` Statement (Recommended)

```python
with open("student.txt", "r") as file:
    print(file.read())
```

The `with` statement automatically closes the file after use.

---

# 2. Database Management in Python

Database management involves storing, retrieving, updating, and deleting data from databases. Python commonly uses **SQLite**, which is included in the standard library.

## Steps

1. Import `sqlite3`
2. Connect to a database
3. Create a table
4. Insert records
5. Retrieve records
6. Update records
7. Delete records
8. Close the connection

---

## Example 1: Create Database and Table

```python
import sqlite3

conn = sqlite3.connect("school.db")
cursor = conn.cursor()

cursor.execute("""
CREATE TABLE IF NOT EXISTS students(
    id INTEGER PRIMARY KEY,
    name TEXT,
    age INTEGER
)
""")

conn.commit()
conn.close()

print("Database and table created.")
```

---

## Example 2: Insert Data

```python
import sqlite3

conn = sqlite3.connect("school.db")
cursor = conn.cursor()

cursor.execute(
    "INSERT INTO students(name, age) VALUES (?, ?)",
    ("John", 20)
)

conn.commit()
conn.close()

print("Record inserted successfully.")
```

---

## Example 3: Retrieve Data

```python
import sqlite3

conn = sqlite3.connect("school.db")
cursor = conn.cursor()

cursor.execute("SELECT * FROM students")

rows = cursor.fetchall()

for row in rows:
    print(row)

conn.close()
```

**Output**

```
(1, 'John', 20)
```

---

## Example 4: Update Data

```python
import sqlite3

conn = sqlite3.connect("school.db")
cursor = conn.cursor()

cursor.execute(
    "UPDATE students SET age = ? WHERE name = ?",
    (21, "John")
)

conn.commit()
conn.close()

print("Record updated.")
```

---

## Example 5: Delete Data

```python
import sqlite3

conn = sqlite3.connect("school.db")
cursor = conn.cursor()

cursor.execute(
    "DELETE FROM students WHERE name = ?",
    ("John",)
)

conn.commit()
conn.close()

print("Record deleted.")
```

---

# Difference Between File Management and Database Management

| File Management                                             | Database Management                                               |
| ----------------------------------------------------------- | ----------------------------------------------------------------- |
| Stores data in text or binary files                         | Stores data in structured tables                                  |
| Suitable for small amounts of data                          | Suitable for large amounts of data                                |
| Slower for searching large files                            | Faster due to indexing and queries                                |
| No built-in relationships between data                      | Supports relationships between tables                             |
| Uses file operations like `open()`, `read()`, and `write()` | Uses SQL commands like `SELECT`, `INSERT`, `UPDATE`, and `DELETE` |
| Example: `.txt`, `.csv`, `.json` files                      | Example: SQLite, MySQL, PostgreSQL                                |

## Summary

* **File Management** is used to store and manipulate data in files using functions such as `open()`, `read()`, `write()`, and `close()`.
* **Database Management** is used to efficiently store and manage structured data using databases like SQLite with SQL operations such as `CREATE`, `INSERT`, `SELECT`, `UPDATE`, and `DELETE`.
* For small applications, file management is often sufficient, while database management is better for applications that require efficient storage, searching, and handling of large or related datasets.
