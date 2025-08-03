# Lab 4: Authentication, Authorization, and Accounting (AAA)

## Objectives

In this lab, I worked on implementing the core principles of Authentication, Authorization, and Accounting in a Linux environment. The main focus was on creating and managing users and groups, verifying account information, and applying different types of file permissions.

---

## Requirements

- Ubuntu 16.04 LTS running in VirtualBox or VMware
- Terminal access with root or sudo privileges

---

## Lab Summary

1. Managing users and groups  
2. Validating account configurations  
3. Applying symbolic file permissions  
4. Applying absolute (numeric) file permissions

---

## 1. User and Group Management

### Elevating to Root

To begin, I switched to the root user:

```bash
sudo su
```

### Creating a Group

I created a group called `HR`:

```bash
groupadd HR
```

### Adding Users and Assigning Them to the Group

I added two users, `jenny` and `joe`, and assigned them to the HR group:

```bash
adduser jenny
usermod -G HR jenny

adduser joe
usermod -G HR joe
```

---

## 2. Verifying Accounts

### Checking Group Memberships

To confirm that the group was created and the users were added, I used:

```bash
cat /etc/group
```

### Verifying User Entries

To inspect user details, I reviewed the `/etc/passwd` and `/etc/shadow` files:

```bash
cat /etc/passwd
cat /etc/shadow
```

---

## 3. Symbolic Permissions

### Switching to User `jenny`

```bash
su -l jenny
```

### Exploring the File System

I checked my current location and navigated to other directories to observe permissions:

```bash
pwd
cd ..
ls -l
cd joe  # Initially accessible
cd ..
```

### Restricting Access

Back as root, I removed execute permission for others from `joe`'s directory:

```bash
sudo -i
cd /home
chmod o-x joe
ls -l
```

After that, I tried accessing Joe’s directory again as Jenny. As expected, access was denied:

```bash
cd joe  # Access denied
```

---

## 4. Absolute Permissions

### Logging in as Joe

```bash
su -l joe
cd ..
ls -l
chmod 705 joe
```

### Creating a Test File

```bash
cd joe
touch test.txt
```

### Testing Access as Jenny

Then I switched back to Jenny and attempted to enter Joe's directory and create a file:

```bash
su -l jenny
cd /home/joe
ls -l
touch jenny.txt  # File creation was denied due to lack of write permissions
```

---

## Permissions Reference

| Octal | Binary | Permissions | Description            |
|-------|--------|-------------|------------------------|
| 7     | 111    | rwx         | Read, write, execute   |
| 6     | 110    | rw-         | Read, write            |
| 5     | 101    | r-x         | Read, execute          |
| 4     | 100    | r--         | Read only              |
| 3     | 011    | -wx         | Write, execute         |
| 2     | 010    | -w-         | Write only             |
| 1     | 001    | --x         | Execute only           |
| 0     | 000    | ---         | No permissions         |

---

## Conclusion

This lab helped solidify my understanding of how Linux manages user accounts and file permissions. I practiced both symbolic (chmod o-x) and absolute (chmod 705) methods for modifying access. By performing access tests using different user accounts, I clearly saw the effect of these permissions in action. These foundational skills are critical for securing any multi-user Linux system.
