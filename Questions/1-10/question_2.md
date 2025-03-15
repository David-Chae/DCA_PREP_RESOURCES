## 2. Excluding Python Byte-Code Files During Docker Image Creation: Which patterns would exclude all Python byte-code files from being copied?

```sh
1. **.pyc
2. **/*.pyc
3. *.pyc
4. /*.pyc
```

To exclude all Python bytecode files (`.pyc`) from being copied during Docker image creation (when using `COPY` or `ADD` in a `Dockerfile`), the correct patterns to use in a `.dockerignore` file are:

### Correct Patterns:
1. `**/*.pyc` ✅  
   - This pattern ensures that **all** `.pyc` files, no matter where they are in the directory structure, are excluded.

2. `*.pyc` ✅  
   - This only excludes `.pyc` files in the root directory, **not** in subdirectories.

### Incorrect or Incomplete Patterns:
1. `**.pyc` ❌  
   - This is incorrect because `**` matches directories, but `**.pyc` is not a valid pattern in `.dockerignore`.

2. `/*.pyc` ❌  
   - This only excludes `.pyc` files **directly in the root directory**, not in subdirectories.

### Recommended `.dockerignore` Entry:
To exclude all Python bytecode files, use:

```
**/*.pyc
```

or

```
*.pyc
**/*.pyc
```

for full coverage.

In a `.dockerignore` file, `*` and `**` have different meanings when used in patterns:

### `*` (Single Asterisk)  
- Matches **any sequence of characters within a single directory** (excluding `/`).
- Does **not** match across directory boundaries.

#### Examples:
```
*.pyc
```
- Matches any `.pyc` file **only in the root directory**.
- Does **not** match files in subdirectories.

```
dir/*.pyc
```
- Matches `.pyc` files **inside `dir/`** but **not** in `dir/subdir/`.

---

### `**` (Double Asterisk)  
- Matches **any sequence of directories and files recursively**.
- Can be used to include all subdirectories.

#### Example:
```
**/*.pyc
```
- Matches `.pyc` files **in any directory at any depth** (e.g., `file.pyc`, `dir/file.pyc`, `dir/subdir/file.pyc`).

---

### Key Differences:
| Pattern       | Matches                                         | Does Not Match                         |
|--------------|---------------------------------|---------------------------------|
| `*.pyc`      | `file.pyc` (root directory) | `dir/file.pyc` |
| `dir/*.pyc`  | `dir/file.pyc` | `dir/subdir/file.pyc` |
| `**/*.pyc`   | `file.pyc`, `dir/file.pyc`, `dir/subdir/file.pyc` | (matches all `.pyc` files) |

---

### Best Practice:
To exclude **all** `.pyc` files at **any depth**, use:
```
**/*.pyc
```
