# Mmap-implementation

## Project Introduction
The program maintains a very large table of square root values in virtual memory. However, the table is too large to fit in physical RAM (we have set a rlimit on the virtual memory size), hence whenever we access the square root of a number that is not there in the table there is a SEGFAULT. This SEGFAULT is captured using a signal handler set during the initialization phase of the program. Now, the task is to allocate some (you can allocate page_size amount) memory by first calculating the correct offset (within the large square root table) of the page fault. Once the memory is allocated, the square root values should be computed for the table's address range(new memory block) corresponding to page faults that occurred.

Your job is to implement the demand faulting mechanism using a signal handler and UNIX memory mapping system calls. To stay within the physical RAM limit, we suggest using the simple strategy of unmapping the last page whenever a new page is faulted in. This is important because we have a hard limit on the size of the virtual memory of the program.

