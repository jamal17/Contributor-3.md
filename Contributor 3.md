Linux Permission

We must set the permission for operating system users by using their user ID. The user information stored in the text file/etc/passwd, each line of this file contains information about the users of the system such as their username, UID, group ID, and their home directory, also we must set the permission for the groups, so the group users will have same access. This will be easy than having individually assign permissions to each user in that group, the information for the group will be stored in /etc/group file, each line of this file will have the information for the group such as the name of the group, ID of the group or GID, and the username of the members.

we need to understand how to read the file permission, and how to change their permission. Linux is a multiuser operating system; a user cannot access or modify files or directories if they do not have an access or permission. We will learn how to manage file permission, and how change permission levels, with examples.

Permission levels.

There are three permission levels.

1- User owner: the user who created that object or designated as user owner by actual owner or root user.

2- Group owner: it is the primary group of user owner or disgnated group by actual owner or root user.

3- All remaining users and groups are considered as others.

Also each permission levels have three permission types:

1- Read; allows the user to view the contents of file.

2- Write; allows the user to overwrite to the file or delete it.

3- Execute; allows the user to execute the code contained in the file.

Permission levels and permission types are always mapped in the following sequence.

1- User(read, Write, Execute)

2- Group(Read, Write, Execute)

3- Other(Read, Write, Execute)

Viewing and modifying permissions.

root/h/jamal>>> ls -l /etc/passwd

-rw-r--r-- 1 root root 1425 Nov 19 16:19 /etc/passwd

The firs charactar is dash because the passwd is a regular file. The next three characters show the permission types for the user owner with permission for read and write, but not for execute. The next three characters show the permission for the group owner only for read. The last three characters show the permission for the others owner it is read only. The first root is the name of the owner and the second root is the name of the group whose users can read this file.

To execute the following command.

root/h/jamal>>> ls -l /bin/ls

-rwxr-xr-x 1 root root 112700 Jan 26 2013 /bin/ls

We see how the permission types change after we execute it, and show the permissions associated with the ls command. The last three 
characters show the permission for the others (everyone) is allowed to execute the code inside it.

Finally we will execute the following command.

root/h/jamal>>> ls -l /

drwxr-xr-x 2 root root 2140 Sep 21 18:09 bin

.........

The first characters isn't start with dash, but with the letter 'd' because we are listing everything in the /directory, so the output shows the permission for /bin directory.

Changing the permission.

Linux, like any other operating system, organizes itself by using files, and directories that can be accessed, modified, and executed. To prevent any internal chaos, Linux gives different levels of permission to interact with those files and directories. We use the command "chmod"(change mode) to change these permissions. chmod command can change the permission either by using numeric or alphanumeric options, we will start with using numeric option.

First, we will create a new file.

root/h/jamal>>> touch file.sh

root/h/jamal>>> ls -l file.sh

-rw-r--r-- 1 root root 0 Nov 19 19:48 file.sh

The touch command create a new empty file named file.sh this file has been created with the permission -rw-r--r--.

to execute this file, we must add the execute permission.

root/h/jamal>>> chmod 755 file.sh

root/h/jamal>>> ls -l file.sh

-rwxr-xr-x 1 root root 0 Nov 19 19:48 file.sh

Using chmod, we specify the permission to be associated with the file and the path to the file. The permissions here are represented by 
755. This mean it will give read, write, and execute permission to the user owner, and read with execute permissions to the group owner and others(everyone).

The number 755 mean.

4- Read permission granted.

2- Write permission granted.

1- Execute permission granted

The number 755 it comes from adding 4,2 and 1 specify 7 in the first place, so we give the user owner full permission. Similarly, we are adding 4 and 1 specify 5 for group owner and others to give them read and execute permission only. The first number 7 applies to the user, the second number 5 applies to the group and the last number 5 applies to others.

This is how to change the permission levels by using numeric option, also we can use the alphanumeric option to change the permission levels.

We will use the same file we create in the first example.

root/h/jamal>>> chmod u+rwx,g+rx,o+rx file.sh

root/h/jamal>>> ls -l file.sh

-rwxr-xr-x 1 root root 0 Nov 19 19:48 file.sh
The (+)and(-) sign are used to add or remove the permission, and user is represented by letter(u), group by letter(g), and the others by letter(O).

Now we will execute this file by writing something in the file. We will use the command echo.

root/h/jamal>>> echo "echo hello class">> file.sh

root/h/jamal>>> ./file.sh

hello class

As we see without the correct permission levels, we cannot be able to execute the file.sh.

Debian Package Management

Debian Package Management details can be found in the Debian Manuals
