# OS1300: Advanced Open-Source Operating System Computing (Summer 2024)
## Course Overview
__From the catalog...__
"In this course, students will recreate a standard library function for managing manually the operating system memory."

__What it means...__
In this course, we will be implementing our own versions of `malloc` and `free` from scratch. 

## Project Overview
- `C - malloc`
    - Opens _Friday, May 10_
    - Due _Wednesday, May 22 @ 11:59PM_ (open 13 calendar days)
    - In this project...
        - You will first create a "naive" implementation of `malloc` (naive because it does not have the necessary bookkeeping to implement `free`)
        - Then you will implement a version of `malloc` that _does_ support `free`-ing of memory blocks (and the `free` function too but that's no problem if you did `malloc` correctly)
    - The implementation of a simple version of `malloc` (that is `free`-able) involves the following basic steps...
        - Use the `sbrk` system call (`man 2 sbrk`) to get the virtual memory address of the program break and extend the program break where necessary. The heap segment is defined by the program break (the memory space right before it).
        - When extending the program break, you should do it in multiples of the system's memory page size (typically `4096` but there are standard macros you can use for the memory-page size)
        - When `malloc` is called, the memory address that is returned is not the start of the block of memory that has been allocated. The caller is actually returned the address right after a memory-block header. This block header handles the allocation bookkeeping and its presence is the reason that `free` only needs to be passed a pointer (doesn't need to be passed the number of bytes to free at that address).
        - At the very least, your memory-block header should consist of (though it's not the only way to do it)...
            - A `size_t` for the total usable memory size in the block (number of bytes)
            - A `size_t` for the number of bytes currently occupied in the block
        - You need to make sure your memory is properly aligned. The easiest way to do this is to make sure the size of the blocks is a multiple of `8` (i.e., `64` bits). For example...
            - Say `malloc(9)` is called
            - If your memory-block header (for which you should create a `struct`) has a size of `16` bytes, then you need `9 + 16 = 25` bytes
            - However, a `25`-byte block will cause the next block created in the heap to be poorly aligned, so you want to actually allocate the next value that is a multiple of `8`, which is `32`.
    - If you follow the above approach when implementing `malloc`, then implementing `free` is as simple as zero-ing out the count of "occupied" bytes in a memory block. You don't have to delete anything or shrink the heap or anything like that.

## Peer Learning Days (PLDs)

This course has 2 required PLDs
- Thursday, May 16
- Thursday, May 23

## Project Pacing Guide

---

### Week 0 (May 10)

<table>
    <tbody>
        <tr>
            <th align="center">Projects Closing</th>
            <th align="center">Projects Opening (Friday morning)</th>
        </tr>
        <tr>
            <td>
                <ul>
                    <li><code>C - strace</code> (from last course)</li>
                    <li><code>Multithreading</code> (from last course)</li>
                </ul>
            </td>
            <td>
                <ul>
                    <li><code>C - malloc</code></li>
                </ul>
            </td>
        </tr>
    </tbody>
</table>

#### Friday
- `C - malloc`
    - Review the `Concepts` and `Resources` pages
    - Complete the quiz

---

### Week 1 (May 13 - May 17)
<table>
    <tbody>
        <tr>
            <th align="center">Projects Closing</th>
            <th align="center">Projects Opening</th>
        </tr>
        <tr>
            <td>
                <ul>
                    <li>N/A</li>
                </ul>
            </td>
            <td>
                <ul>
                    <li>N/A</li>
                </ul>
            </td>
        </tr>
    </tbody>
</table>

(Continuing to work on `C - malloc` this week)

#### Monday - Wednesday
- `C - malloc`
    - Complete `Task 0`

#### Thursday
- _PLD, 9:00AM-3:00PM_
- `C - malloc`
    - Begin working on `Task 1`

#### Friday
- `C - malloc`
    - Continue working on `Task 1`

---

### Week 2 (May 20 - May 24)

<table>
    <tbody>
        <tr>
            <th align="center">Projects Closing</th>
            <th align="center">Projects Opening (Friday morning)</th>
        </tr>
        <tr>
            <td>
                <ul>
                    <li><code>C - malloc</code></li>
                </ul>
            </td>
            <td>
                <ul>
                    <li><code>Sorting algorithms advanced</code> (next course)</li>
                    <li><code>C - Hash tables</code> (next course)</li>
                </ul>
            </td>
        </tr>
    </tbody>
</table>

#### Monday - Tuesday
- `C - malloc`
    - Complete `Task 1`

#### Wednesday
- `C - malloc`
    - Complete `Task 2`
        - As mentioned above, if you implemented `Task 1` correctly, then your `free` will simply just zero-out the number of bytes that are "in use" in the memory-block header corresponding to the pointer passed to the function.

#### Thursday
- _Course closes at 11:59PM!_
    - Today is the last day to get any additional points on `C - malloc`
- _PLD, 9:00AM-3:00PM_
