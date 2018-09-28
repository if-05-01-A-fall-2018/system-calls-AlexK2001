# Assignment 2: System Calls

##System Calls

### fork()
creates a new process by duplicating the calling process. The new process is referred to as the child process.
The calling process is referred to as the parent process. On success, the PID of the child process is returned in the parent, and 0 is returned in the child.  On failure, -1 is returned in the parent, no child process is created.

###stat()
These functions return information about a file, in the buffer pointed to by a buffer. No permissions are required on the file itself, but—in the case of stat(), fstatat(), and lstat()—execute (search) permission is required on all of the directories in pathname that lead to the file.

stat() and fstatat() retrieve information about the file pointed to by pathname; the differences for fstatat() are described below.

lstat() is identical to stat(), except that if pathname is a link, then it returns information about the link itself, not the file that it refers to.

fstat() is identical to stat(), except that the file about which information is to be retrieved is specified by the file descriptor fd.


### kill()
kill is a command that is used in several popular operating systems to send signals to running processes

Anytime you use kill on a process, you’re actually sending the process a signal.Standard C applications have a header file that contains the steps that the process should follow if it receives a own signal.

for example kill 213
This would send a signal called SIGTERM to the process. Once the process receives the notice, a few different things can happen:

  - the process may stop immediately
  - the process may stop after a short delay after cleaning up resources
  - the process may keep running endlessly

for example kill -9 2562
kill -9 Meaning: The process will be killed by the kernel; this signal cannot be ignored.

###mmap

mmap, munmap - map or unmap files or devices into memory

mmap() creates a new mapping in the virtual address space of the calling process. The starting address for the new mapping is specified in addr.

1. PROT_EXEC  Pages may be executed.
2. PROT_READ  Pages may be read.
3. PROT_WRITE Pages may be written.
4. PROT_NONE  Pages may not be accessed.

###chmod

chmod - changes file modes.

chmod changes the file mode bits of each given file according to mode.

###waitpid

waitpid — wait for a child process to terminate

The waitpid() functions shall obtain status information pertaining to one of the caller's child processes. Various options permit status information to be obtained for child processes that have terminated or stopped.

The waitpid() function shall be equivalent to wait() if the pid argument is (pid_t)−1 and the options argument is 0. The pid argument specifies a set of child processes for which status is requested.

###SYSTEM CALL FAILS:

- fork: will fail to allocate the kernel structures if there's not enough memory
- exec:   an Input/Output error appears
- unlink: The file pathname can't be unlinked because it is being used by the system or another process or can't unlink if the pathname refers to a directory
- read: will fail if the file descriptor is not valid or if the buffer is outside the accessible address space
- mount: will fail if the source is already  mounted or can't be mounted because the target is still busy (e.g. has open files)
- chmod: will fail if the file doesn't exist, the fd (file descriptor) is not valid or if there isn't enough kernel memory
- kill: will fail if the pID doesn't exist or if there was an invalid signal

TRAPS:

A trap is used to enter kernel mode. The system (kernel) instruction is loaded and the trap is called and those loaded instructions will be done.
for example you go into the drugstore at midnight and give the pharmacist the recipe.
