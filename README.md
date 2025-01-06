
# ACL Commands Reference Guide

This guide provides a quick reference to essential ACL commands for Linux.

---

## 1. **Check ACL Support**
To verify if a filesystem supports ACLs:

```bash
tune2fs -l /dev/<device> | grep "Default mount options"
```

To enable ACL support on a filesystem:

```bash
mount -o remount,acl /path/to/mountpoint
```

---

## 2. **View ACLs**
To view ACL entries for a file or directory:

```bash
getfacl <file_or_directory>
```

---

## 3. **Set ACLs**
- Grant a user specific permissions:

```bash
setfacl -m u:username:permissions <file_or_directory>
```
Example:

```bash
setfacl -m u:johndoe:rw <file>
```
- Grant a group specific permissions:

```bash
setfacl -m g:groupname:permissions <file_or_directory>
```
Example:

```bash
setfacl -m g:developers:rwx <file>
```

- Set default ACLs for a directory (applies to new files):

```bash
setfacl -d -m u:username:permissions <directory>
```
Example:

```bash
setfacl -d -m u:johndoe:rw <directory>
```

---

## 4. **Remove ACLs**
- Remove specific ACL entries:

```bash
setfacl -x u:username <file_or_directory>
```
Example:

```bash
setfacl -x u:johndoe <file>
```

- Remove all ACLs:

```bash
setfacl -b <file_or_directory>
```

- Remove default ACLs:

```bash
setfacl -k <directory>
```

---

## 5. **Backup and Restore ACLs**
- Backup ACLs:

```bash
getfacl -R <directory> > acl_backup.txt
```

- Restore ACLs:

```bash
setfacl --restore=acl_backup.txt
```

---

## Permissions Reference
- **r**: Read

- **w**: Write

- **x**: Execute


---

Keep this guide handy to simplify your ACL management tasks in Linux!
