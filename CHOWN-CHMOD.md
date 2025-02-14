# **CHOWN** and **CHMOD**

In Linux, **file ownership and permissions** are crucial for security and access control. The `chown` and `chmod` commands help manage these aspects effectively.  

---

## **1. `chown` (Change Owner)**
### **Definition:**  
The `chown` command is used to change the **owner** and/or **group** of a file or directory.  

### **Syntax:**  
```bash
chown [OPTIONS] [USER][:GROUP] FILE
```

### **Changing File Owner:**
```bash
chown newuser filename
```
- Assigns `newuser` as the owner of `filename`.

### **Changing File Group:**
```bash
chown :newgroup filename
```
- Changes the group ownership of `filename` to `newgroup`.

### **Changing Both Owner and Group:**
```bash
chown newuser:newgroup filename
```
- Assigns both `newuser` as the owner and `newgroup` as the group.

### **Changing Ownership Recursively:**
```bash
chown -R newuser:newgroup directory/
```
- Changes ownership of **all files and subdirectories** inside `directory/`.

### **Checking Ownership:**
```bash
ls -l filename
```
- Displays the current owner and group of the file.

---

## **2. `chmod` (Change File Permissions)**
### **Definition:**  
The `chmod` command is used to change the **permissions** of a file or directory, defining who can read, write, or execute it.  

### **Permission Representation:**
| Symbol | User | Permission Type |
|--------|------|----------------|
| `r` | Read | Can read the file (4) |
| `w` | Write | Can modify the file (2) |
| `x` | Execute | Can execute the file (1) |

### **Syntax:**  
```bash
chmod [OPTIONS] MODE FILE
```

### **Changing Permissions Using Numeric (Octal) Mode:**
Each permission has a numeric value:
- Read (`r`) = **4**
- Write (`w`) = **2**
- Execute (`x`) = **1**

To set permissions:
```bash
chmod 755 script.sh
```
- **Owner:** `7` (`rwx` = 4+2+1)
- **Group:** `5` (`r-x` = 4+0+1)
- **Others:** `5` (`r-x` = 4+0+1)

### **Changing Permissions Using Symbolic Mode:**
```bash
chmod u+rwx,g+rx,o+r script.sh
```
- **u+rwx** → User gets **read, write, execute**.
- **g+rx** → Group gets **read and execute**.
- **o+r** → Others get **read** permission.

### **Common Permission Settings:**
| Command | Meaning |
|---------|---------|
| `chmod 777 file` | Everyone can read, write, and execute (⚠️ Security risk) |
| `chmod 755 file` | Owner has all permissions, others can read and execute |
| `chmod 644 file` | Owner can read/write, others can only read |
| `chmod 600 file` | Only owner can read/write |
| `chmod 400 file` | Only owner can read (no write/execute) |
| `chmod 000 file` | No one can access the file |

### **Changing Permissions Recursively:**
```bash
chmod -R 755 directory/
```
- Applies permissions to **all files and subdirectories** inside `directory/`.

---

---

## **Conclusion**
- **Use `chown`** to change file ownership.
- **Use `chmod`** to set file permissions.
- **Use octal (`755`) or symbolic (`u+x`) notation** for permission changes.
- **Be careful with `chmod 777`**—it gives **everyone** full control!
- **Use `-R`** for recursive changes.


