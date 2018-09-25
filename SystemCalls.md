# Assignment 2: System Calls

##System Calls

### fork()
creates a new process by duplicating the calling process. The new process is referred to as the child process.
The calling process is referred to as the parent process. On success, the PID of the child process is returned in the parent, and 0 is returned in the child.  On failure, -1 is returned in the parent, no child process is created.

###stat()
These functions return information about a file, in the buffer pointed to by statbuf. No permissions are required on the file itself, but—in the case of stat(), fstatat(), and lstat()—execute (search) permission is required on all of the directories in pathname that lead to the file.

stat() and fstatat() retrieve information about the file pointed to by pathname; the differences for fstatat() are described below.

lstat() is identical to stat(), except that if pathname is a symbolic link, then it returns information about the link itself, not the file that it refers to.

fstat() is identical to stat(), except that the file about which information is to be retrieved is specified by the file descriptor fd.

int stat(const char *pathname, struct stat *statbuf);
int fstat(int fd, struct stat *statbuf);
int lstat(const char *pathname, struct stat *statbuf);
int fstatat(int dirfd, const char *pathname, struct stat *statbuf, int flags);
