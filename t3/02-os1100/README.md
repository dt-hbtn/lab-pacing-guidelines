# OS1100: Beginning Open-Source Operating System Computing (Summer 2024)
## Course Overview
__From the catalog...__
"Students will expand their basic knowledge of Shell and filesystem. They will learn how to manipulate environments and both redirect streams and setup a pipe."

__What it means...__
In this course, you will be learning more techniques for interprocess communication--including a shell interpreter with support for piping and redirects, and a Python script that manipulates data in the heap of another process running on the same system.

## Project Overview
- `C - Shell v2`
    - Opens _Friday, May 24_
    - Due _Wednesday, June 5 @ 11:59PM_ (open 13 calendar days)
    - Task overview (__Note the tasks below that I am not requiring for your grade__)
        - `hsh 1.0`
            - Handle the `PATH` environment variable (i.e., when given a command like `ls`, you will need to search the directories listed in `PATH` to find an executable with that name)
            - Implement the following built-in commands: `cd`, `exit`, and also `env`
                - Built-in commands are provided by the shell interpreter itself, they are not executables on the system like `ls`, `chmod`, `mkdir`, etc.
        - `hsh 1.1`
            - Add support for right stream redirection with the `>` operator (e.g., `command > outputfile.txt`)
                - Under the hood, this shell operator writes anything the command prints to `stdout` into the output file (creates and/or overwrites the file)
        - `hsh 1.2`
            - Add support for the double right stream redirection with the `>>` operator (e.g., `command >> outputfile.txt`)
                - Unlike the `>` operator, this operator should _append_ the contents of `stdout` to the output file.
        - `hsh 1.3`
            - Add support for left stream redirection with the `<` operator (e.g., `command < inputfile.txt`)
                - This operator should `open()` the input file and map its file descriptor so that `command` receives the files contents via `stdin`
        - `hsh 1.4` (__can skip__)
            - Add support for double left stream redirection (heredoc) with the `<<` operator (e.g., `command << delimiter`)
                - I will not count the points on this one, so you may treat it as an advanced task
        - `hsh 1.5`
            - Add support for piping between two commands with the `|` operator (e.g., `command1 | command2`)
                - Under the hood, this operator creates a one-way channel of communication with `pipe` (i.e., one process can write to the pipe and one can read from it)
                - You will have to map the file descriptor for `stdout` of `command1` to the write end of the pipe, and map the file descriptor for `stdin` of `command2` to the read end of the pipe.
        - `hsh 1.6` (__can skip__)
            - Add support for the command separator (`;`)
                - I will not count the points on this one, so you may treat it as an advanced task
        - `hsh 1.7` (__can skip__)
            - Add support for the logical-and operator (`&&`)
                - I will not count the points on this one, so you may treat it as an advanced task
        - `hsh 1.8` (__can skip__)
            - Add support for the logical-or operator (`||`)
                - I will not count the points on this one, so you may treat it as an advanced task
        - `README, man, AUTHORS`
            - Your "Simple Shell" project from T1 should have everything you need to refresh yourself on this
        - `Betty would be proud`
            - Runs `betty` checks on all of your C files
        - 

- `Python - /proc filesystem`
    - Opens _Friday, June 7_
    - Due _Wednesday, June 12_
    - In this project...
        - You will write a Python script that manipulates data in the heap of another running process.
        - Since everything is a file in Linux, you can actually access a process's memory via its corresponding `/proc/<pid>/mem` file in the filesystem.
        - Each process will also have a `/proc/<pid>/maps` file that shows you the address mapping for the different memory segments (in which you will search for `[heap]`)
        - Once you have accessed the target process's memory and navigated to the start address of its heap, you will implement find/replace for a particular string in the process's heap
        - You will also write a short blog post about the `/proc` filesystem on Linux. __Note: It is fine if you do not publish it publicly. You can just submit a GoogleDoc or whatever format you like.__

## Peer Learning Days (PLDs)

This course has 3 required PLDs
- Thursday, May 30
- Thursday, June 6
- Thursday, June 13

## Project Pacing Guide

---

### Week 0 (May 24)

<table>
    <tbody>
        <tr>
            <th align="center">Projects Closing</th>
            <th align="center">Projects Opening (Friday morning)</th>
        </tr>
        <tr>
            <td>
                <ul>
                    <li><code>C - ls</code> (from last course)</li>
                </ul>
            </td>
            <td>
                <ul>
                    <li><code>C - Shell v2</code></li>
                    <li><code>Python - /proc filesystem</code></li>
                </ul>
            </td>
        </tr>
    </tbody>
</table>

#### Friday
- `C - Shell v2`
    - Review the `Concepts` and `Resources` pages
    - Complete the quiz
    - Review the `Allowed Functions and System Calls` list and research examples of their usage.
        - Refresh yourself on these system calls from T1 (spawning a child process):
            - `fork` (`man 2 fork`)
            - `execve` (`man 2 execve`)
            - `wait`/`waitpid` (`man 2 wait`)
        - New system calls to focus on:
            - `dup`/`dup2` (`man 2 dup`)
            - `pipe` (`man 2 pipe`)
        - (There are many more in the list but those listed above are really important to understand)
    - Plan to start working with partner following Monday

---

### Week 1 (May 27 - May 31)
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

(Continuing to work on `C - Shell v2` this week)

#### Monday
- `C - Shell v2`, Task `hsh 1.0`
    - Implement a function that finds the absolute path to an executable, given the application's name (e.g., `ls`) and the `PATH` environment variable. Here's the basic idea.
    ```c
    /**
     * resolve_command_path - Returns absolute path of `command` given the `PATH` environment variable
     * @buf: Buffer to write result path to (4095 + null terminator max on linux)
     * @pathenv: Value of `PATH` environment variable
     * @command: Command name
     *
     * Return: 1 if path to command found, 0 if not
     */
    char *resolve_command_path(char buf[4096], const char *pathenv, const char *command)
    {
        /* max path length on linux is 4095 plus null terminator */
        int command_found = 0;

        /* `PATH` environment variable will be a colon-delimited list of directories to find commands */
        /* search each directory in the list for an executable file whose name matches `command` argument */
        /* use the `buf` argument to join paths where needed */
        /* if the command is found, return 1 and `buf` should now contain the absolute path to the command */

        return (command_found);
    }
    ```

#### Tuesday
- `C - Shell v2`, Task `hsh 1.0`
    - Implement `cd` and `exit` built-in commands
    - Implement `env` command

#### Wednesday
- `C - Shell v2`
    - Implement `hsh 1.1` task (`>` output redirection)
    - Implement `hsh 1.2` task (`>>` output redirection)

#### Thursday
- _PLD, 9:00AM-3:00PM_
- `C - Shell v2`
    - We will be covering redirection and piping pretty extensively

#### Friday
- `C - Shell v2`
    - Implement `hsh 1.3` task (`<` input redirection)
    - Make a plan for implementing `hsh 1.5` task (`|` piping operation), at a high level you might have a function like this:
    ```c
    void pipe_commands(const char *cmd1_path,
                       char *const cmd1_argv[],
                       const char *cmd2_path,
                       char *const cmd2_argv[],
                       char *const envp[])
    {
        int pipefd[2];
        pid_t cmd1_pid, cmd2_pid;

        /* create the pipe with `pipe` syscall */

        /* `fork` for command1 */

        /**
         * inside command1's child process, `dup2` the write end of the `pipefd` array to `STDOUT_FILENO`
         * then `execve(cmd1_path, cmd1_argv, envp)`
         */

        /* `fork` for command2 */

        /**
         * inside command2's child process, `dup2` the read end of the `pipefd` array to `STDIN_FILENO`
         * then `execve(cmd2_path, cmd2_argv, envp)`
         */

         /**
          * back in parent process, close the pipefds
          * call `waitpid` for `cmd1_pid` and `cmd2_pid`
          */
    }
    ```

---

### Week 2 (June 3 - June 7)

<table>
    <tbody>
        <tr>
            <th align="center">Projects Closing</th>
            <th align="center">Projects Opening (Friday morning)</th>
        </tr>
        <tr>
            <td>
                <ul>
                    <li><code>C - Shell v2</code></li>
                </ul>
            </td>
            <td>
                <ul>
                    <li><code>Python - /proc filesystem</code></li>
                </ul>
            </td>
        </tr>
    </tbody>
</table>

#### Monday
- `C - Shell v2`
    - Complete implementation of `hsh 1.5` task (`|` pipe redirection)

#### Tuesday - Wednesday
- `C - Shell v2`
    - Complete `README`, `man` page, and `AUTHORS`
    - Final debugging/fine-tuning
    - _Project due Wednesday, June 5 @ 11:59pm!_

#### Thursday
- _PLD, 9:00AM-3:00PM_
- `Python - /proc filesystem`
    - We will look at how the `/proc` filesystem works on Linux

#### Friday
- `Python - /proc filesystem`
    - Review the resources regarding the `/proc` filesystem
    - Build your command-line interface for the script
        - Usage: `read_write_heap.py pid search_string replace_string`
            - `pid`: Target process ID (`int`)
            - `search_string`: The string you will search for in the target process's heap
            - `replace_string`: The string you will replace `search_string` with
    - Don't forget to make your script executable (`chmod u+x read_write_heap.py`) and include the python3 shebang on the first line (`#!/usr/bin/python3`)

### Week 3 (June 10 - June 14)

<table>
    <tbody>
        <tr>
            <th align="center">Projects Closing</th>
            <th align="center">Projects Opening (Friday morning)</th>
        </tr>
        <tr>
            <td>
                <ul>
                    <li><code>Python - /proc filesystem</code></li>
                </ul>
            </td>
            <td>
                <ul>
                    <li><code>C - ELF: readelf</code> (next course)</li>
                </ul>
            </td>
        </tr>
    </tbody>
</table>

#### Monday
- `Python - /proc filesystem`
    - Write a function that parses the heap address range from `/proc/pid/maps` and returns it. This will get you started.
    ```python
    def get_heap_address_range(pid):
        with open(f'/proc/{pid}/maps', 'r') as proc_maps:
            for line in proc_maps:
                if '[heap]' in line:
                    # the address range will be at the start of this line, parse them out
                    # you can convert hex strings to an `int` with `int(hex_string, 16)`
                    # ...
                    return (heap_start, heap_end) # `tuple` of 2 `int`s
        
        return (None, None) # no heap segment for the target process
    ```
    - Once you have the heap address range, you can open the `/proc/<pid>/mem` file and seek to the `heap_start` address
    - Search that address space for `search_string`. When you find it, overwrite those bytes with `replace_string`.
    - You might find the `ctypes` module helpful (built-in to Python), but whether you use it or not you will want to become familiar with Python's built-in `bytes` and `bytearray` classes.

#### Tuesday
- `Python - /proc filesystem`
    - Finish implementing the command-line application, debugging

#### Wednesday
- `Python - /proc filesystem`
    - Write your blog post and submit
    - _Project due @ 11:59PM!_

#### Thursday
- _Course closes @ 11:59PM!_
    - Today is the last day to get any additional points on `C - Shell v2` and `Python - /proc filesystem`
- _PLD, 9:00AM-3:00PM_
