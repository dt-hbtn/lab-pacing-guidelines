# LP1300: Low-Level Programming Applications (Fall 2024)
## Course Overview
__From the catalog...__
"This course focuses on the creation and analysis of concurrent applications. Students will work toward solving real-live situations related to image processing and time-consuming computing."

__What it means...__
In this course, we will continue developing skills with interprocess communication and adding multithreading as another means of computational concurrency on a Linux system.

## Project Overview
- `C - Strace`
    - Opens _Monday, August 26_
    - Due _Wednesday, September 4 @ 11:59PM_ (open 10 calendar days)
    - In this project...
        - You will be building a rudimentary version of the `strace` utility.
        - You will use the `ptrace` library to trace a process's system calls and display some information about them
        - You will spawn the target application as a child process via `execve` and use functionality of the `ptrace` library that listens for signals that indicate the child process is making a system call.
- `Multithreading`
    - Opens _Monday, August 26_
    - Due _Wednesday, September 4 @ 11:59PM_ (open 10 calendar days)
    - In this project...
        - You will get some exposure to multithreading via the `pthreads` (POSIX threads) library
        - You will use synchronization primitives (e.g., mutex) to prevent concurrent threads from stepping on one-another's toes

Note: `C - Strace` and `Multithreading` are assigned concurrently!

## Peer Learning Days (PLDs)

This course has 2 PLDs
- Thursday, August 29
- Thursday, September 5

## Project Pacing Guide

---

### Week 1 (August 26 - August 30)

<table>
    <tbody>
        <tr>
            <th align="center">Projects Closing</th>
            <th align="center">Projects Opening (Monday morning)</th>
        </tr>
        <tr>
            <td>
                <ul>
                    <li>N/A</li>
                </ul>
            </td>
            <td>
                <ul>
                    <li><code>C - Strace</code></li>
                    <li><code>Multithreading</code></li>
                </ul>
            </td>
        </tr>
    </tbody>
</table>

#### Monday
- Projects opening today:
    - `C - Strace` (4 required tasks)
    - `Multithreading` (7 required tasks in intranet, but see note below)
        - `Task 2` and `Task 3` will not count against you if you don't do them (they are particularly time consuming and most of that time is spent on on Gaussian blur instead of multithreading)
        - So the number of tasks that are truly required is 5
- `C - Strace`
    - Review the `Concepts` and `Resources` pages (x86_64 assembly page is just provided for review of 64-bit registers)
    - Complete the quiz
    - Copy the helper header file from this repository https://github.com/hs-hq/0x0B-strace.c into your `strace` project directory
    - Look ahead at all 4 tasks to make a reusable design for your code
    - Complete `Task 0`

#### Tuesday
- `C - Strace`
    - Complete `Task 1`

#### Wednesday
- `C - Strace`
    - Complete `Task 2`

#### Thursday
- Optional PLD, 9-3
- `C - Strace`
    - Complete `Task 3`
- `Multithreading`
    - Review the `Concepts` and `Resources` pages
    - Look ahead at the required tasks (remember `Task 2` and `Task 3` will not count against your grade but feel free to complete them)

#### Friday
- `Multithreading`
    - Complete `Task 0`
    - Complete `Task 1`

---

### Week 2 (September 2 - September 6)
<table>
    <tbody>
        <tr>
            <th align="center">Projects Closing (Wednesday @ 11:59PM)</th>
            <th align="center">Project Opening (Friday morning)</th>
        </tr>
        <tr>
            <td>
                <ul>
                    <li><code>C - Strace</code></li>
                    <li><code>Multithreading</code></li>
                </ul>
            </td>
            <td>
                <ul>
                    <li><code>C - malloc</code> (next course)</li>
                </ul>
            </td>
        </tr>
    </tbody>
</table>

#### Monday
- `Multithreading`
    - Complete `Task 4`

#### Tuesday
- `Multithreading`
    - Complete `Task 5`

#### Wednesday
- `Multithreading`
    - Complete `Task 6`

#### Thursday
- _Course closes at 11:59PM!_
- _PLD, 9:00AM-3:00PM_
    - Go over any remaining questions on `C - Strace` and `Multithreading`
    - Look at possible implementation of `Task 2` and `Task 3` from `Multithreading` project
