# DS1000: Low-Level Programming Applications (Summer 2024)
## Course Overview
__From the catalog...__
"This course is designed for students to be introduced to the basic elements of data structures including projects that focus on correctly using hash tables."

__What it means...__
In this course, you will build a hash table in C that supports features of a dictionary in php (i.e., key/value pairs stored in a hash table by key, but the k/v pairs can also be traversed in ascending/descending sorted order). You will also implement shell sort, counting sort, and merge sort for `int` arrays.

## Project Overview
- `Hash Tables Advanced`
    - Opens _Friday, May 24_
    - Due _Wednesday, June 5 @ 11:59PM_ (open 13 calendar days)
    - In this project...
        - Implement a hash table with string key/value pairs (`djb2` hash function)
        - The hash table will use linked lists to resolve hash collisions
        - Each struct/node will also be linked to its in-order predecessor and successor (the nodes with keys that come immediately before and immediately after when the keys are sorted lexicographically)
            - Think of the nodes that are stored in your hash table as belonging to two different linked lists: 1 singly-linked list for its hash bucket and 1 doubly-linked list that maintains the sorted order of keys
            - Each time you insert a new key into the hash table, you can traverse the sort-order linkage until you find an existing key that evaluates to greater (insert right before that one) or you reach the end and just place it there
- `Sorting Algorithms Advanced`
    - Opens _Friday, May 24_
    - Due _Wednesday, June 5 @ 11:59PM_ (open 13 calendar days)
    - In this project...
        - You will implement shell sort, counting sort, and merge sort.
        - You can find a lot of resources/videos for these sorting algorithms online. Feel free to share them.

Note: `Hash Tables Advanced` and `Sorting Algorithms Advanced` are assigned concurrently!

## Peer Learning Days (PLDs)

This course has 2 required PLDs
- Thursday, May 30
- Thursday, June 6

## Project Pacing Guide

---

### Week 0 (May 24)

<table>
    <tbody>
        <tr>
            <th align="center">Projects Closing</th>
            <th align="center">Projects Opening (Monday morning)</th>
        </tr>
        <tr>
            <td>
                <ul>
                    <li><code>C - malloc</code> (previous course)</li>
                </ul>
            </td>
            <td>
                <ul>
                    <li><code>Hash Tables Advanced</code></li>
                    <li><code>Sorting Algorithms Advanced</code></li>
                </ul>
            </td>
        </tr>
    </tbody>
</table>

#### Friday
- `Hash Tables Advanced`
    - Review the resource links in the project
    - Make sure you understand the purpose of the structs you are provided (`shash_node_t` and `shash_table_t`) and the purpose of all of their members (or collect whatever questions you may have about them).
    - Create your header file and include the given data structures.
    - Place this function in a file called `1-djb2.c` and put the prototype in your header file.
    ```c
    /**
    * hash_djb2 - hash a string for table lookup
    * @str: Input string
    *
    * Return: hash value
    */
    unsigned long int hash_djb2(const unsigned char *str)
    {
        unsigned long int hash;
        int c;

        hash = 5381;
        while ((c = *str++))
        {
            hash = ((hash << 5) + hash) + c; /* hash * 33 + c */
        }
        return (hash);
    }
    ```

---

### Week 1 (May 27 - May 31)
<table>
    <tbody>
        <tr>
            <th align="center">Projects Closing</th>
            <th align="center">Project Opening</th>
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

#### Monday
- `Hash Tables Advanced`
    - Implement the following functions:
        - `shash_table_create`
        - `shash_table_set`
            - Keep in mind that if the `key` already exists, then you just replace the `value` (like a Python dictionary)
            - If the `key` does not already exist, you will add it with the given value
            - The hash table will own heap-allocated copies of all `key`s and `value`s
        - `shash_table_get`

#### Tuesday
- `Hash Tables Advanced`
    - Implement the following functions:
        - `shash_table_print`
        - `shash_table_print_rev`
        - `shash_table_delete`
            - Keep in mind you've got to traverse all of the nodes, freeing their `key` and `value`, then free the node itself. You will then also have to free `shash_table_t::array` and then free the `shash_table_t` pointer itself.
            - (After the `malloc` project, you're probably thinking "wow that sure is using a LOT of memory")

#### Wednesday
- `Hash Tables Advanced`
    - Finish debugging and checking for memory errors

#### Thursday
- _PLD, 9:00AM-3:00PM_
    - We will look at other approaches to hash collisions and other data structures that are used for storing (sorted) key/value pairs

#### Friday
- `Sorting Algorithms Advanced`
    - Look over the resources
    - Create your header file with the function prototypes for the 3 sorting algorithms
    - Find some cool videos that visualize sorting algorithms (there are many)
    - I would first focus on implementing the algorithms correctly without worrying about the incremental output that the checker expects. Once you've implemented the sort correctly, it's not too difficult to modify your code to print incremental state (though it will force you to do the opposite of optimizing your implementation in a few places).
    - Start on `0. Shell sort - Knuth Sequence`

### Week 2 (June 3 - June 7)
<table>
    <tbody>
        <tr>
            <th align="center">Projects Closing (Wednesday @ 11:59PM)</th>
            <th align="center">Project Opening (Friday morning)</th>
        </tr>
        <tr>
            <td>
                <ul>
                    <li><code>Hash Tables Advanced</code></li>
                    <li><code>Sorting Algorithms Advanced</code></li>
                </ul>
            </td>
            <td>
                <ul>
                    <li><code>Sockets</code> (next course)</li>
                </ul>
            </td>
        </tr>
    </tbody>
</table>

#### Monday
- `Sorting Algorithms Advanced`
    - Complete `0. Shell sort - Knuth Sequence`
    - Implement `1. Counting sort`

#### Tuesday
- `Sorting Algorithms Advanced`
    - Implement `2. Merge sort`

#### Wednesday
- `Sorting Algorithms Advanced`
    - Finish refactoring to include the printing of incremental sort state in each algorithm.

#### Thursday
- _Course closes at 11:59PM_
- _PLD, 9:00AM-3:00PM_
    - If we have time, I would like to attempt a multithreaded implementation of Shell sort.

