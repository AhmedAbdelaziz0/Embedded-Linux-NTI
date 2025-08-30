# User Management Stack

Protecting data privacy by managing file access permissions for all users on the system. The user management stack is part of the file system stack

All processes spawned by the user inherit the permissions of their parent user, and likewise all child processes inherit the permissions of their parent

Every file or directory has permissions which control who has access to it. Inside some directory we can see the following

```
$ ls -al
total 11276
drwxr-xr-x 3 gee gee    4096 Aug 26 07:19 ./
drwxr-xr-x 3 gee gee    4096 Aug 26 07:11 ../
drwxr-xr-x 2 gee gee    4096 Aug 26 07:11 dir/
-rw-r--r-- 1 gee gee 4194304 Aug 26 07:25 file1.txt
-rw-r--r-- 1 gee gee 7340032 Aug 26 07:26 file2.o
```

The leftmost column defines the permission bits for each item inside the directory

- `d`: Describes whether it's a directory or a file
- `r`: Item has read access
- `w`: Item has write access
- `x`: Item has execute access

Each `rwx` trio of bits exists for the user, others and the group, for a total of 8 bits including the `d` bit

## Commands

- `adduser`: Adds a new user
- `deluser`: Removes an existing user
- `usermod`: Modify user properties
- `passwd`: Change user password
- `/etc/passwd`: Database of all users in the system
- `id`: Get information about logged in user
- `addgroup`: Adds a new group 
- `delgroup`: Removes an existing group
- `chgrp`: Change group of listed file(s)
- `chown`: Change owner of listed file(s)
- `chmod`: Modify file access permissions for listed file(s)
