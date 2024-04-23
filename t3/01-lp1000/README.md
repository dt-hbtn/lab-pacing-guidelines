# LP1000: Foundations of Low-Level Programming (Summer 2024)
## Projects in this course
- `C - Makefiles` (10 days)
- `C - Static variables, getline` (10 days)
- `C - ls` (13 days)

`C - Makefiles` and `C - Static variables, getline` are assigned concurrently!


## Project Pacing Guide

---

### Week 1 (April 29 - May 3)

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
                    <li><code>C - Makefiles</code></li>
                    <li><code>C - Static variables, getline</code></li>
                </ul>
            </td>
        </tr>
    </tbody>
</table>

#### Monday
- Projects opening today:
    - `C - Makefiles` (5 required tasks)
    - `C - Static variables, getline` (3 required tasks)
- Create the following repositories if they don't already exist:
    - `atlas-low_level_programming`
    - `atlas-system_linux`
- `C - Makefiles`
    - Review the tutorial linked in the project: https://makefiletutorial.com/
    - Copy the necessary files from this repository https://github.com/hs-hq/0x1B.c into your `makefiles` project directory
    - Complete `Task 0`

#### Tuesday
- `C - Makefiles`
    - Complete `Task 1`
    - Complete `Task 2`

#### Wednesday
- `C - Makefiles`
    - Complete `Task 3`
    - Complete `Task 4` (last required task)

#### Thursday
- Optional PLD, 9-3
- `C - Makefiles`
    - Bring any remaining questions to the optional PLD (or slack instructor if you cannot attend)
- `C - Static variables, getline`
    - Review the resource pages
    - Complete the quiz
    - Begin `Task 0`
        - You will need to track the race state with a function-scope static variable, but the data structure you use to do this is up to you
        - Regardless what data structure you use to track the data, you will need to keep track of each car's `id` and _current lap_.
        - Notice that the example output is always sorted ascending by car `id`
            - Prefer using a _binary search tree_ (which you worked with a little in T1) to maintain the car data because it will keep your data sorted by `id`
            - With a BST you can just perform an [in-order traversal](https://www.geeksforgeeks.org/inorder-traversal-of-binary-tree/) and print each node's data

#### Friday
- `C - Static variables, getline`
    - Complete `Task 0`
    - Begin `Task 1`

---

### Week 2 (May 6 - May 10)
<table>
    <tbody>
        <tr>
            <th align="center">Project(s) Closing (Wednesday @ 11:59PM)</th>
            <th align="center">Project(s) Opening (Friday morning)</th>
        </tr>
        <tr>
            <td>
                <ul>
                    <li><code>C - Makefiles</code></li>
                    <li><code>C - Static variables, getline</code></li>
                </ul>
            </td>
            <td>
                <ul>
                    <li><code>C - ls</code></li>
                </ul>
            </td>
        </tr>
    </tbody>
</table>

#### Monday
- `C - Static variables, getline`
    - Complete `Task 1`
    - Begin `Task 2` (last required task)

#### Tuesday
- `C - Static variables, getline`
    - Continue working on `Task 2` (last required task)

#### Wednesday
- `C - Static variables, getline`
    - Complete `Task 2` (last required task)
- Projects due at 11:59PM!
    - `C - Makefiles`
    - `C - Static variables, getline`

#### Thursday
- _PLD, 9:00AM-3:00PM_
- Review any final questions from `C - Makefiles` and `C - Static variables, getline`
- Look ahead at techniques that can be used in `C - ls`
    - Use of `enum` types for option flags (and bitwise combinations)
    - Prefer a single function as the point of entry. It should accept arguments related to the supported options (which you can gradually implement with each new task).

#### Friday
- Project opening today:
    - `C - ls` (6 required tasks)
- `C - ls`
    - Work through the `Concepts` page
    - Come up with an entry-function prototype that will work for all the required tasks
    - Begin `Task 0` (i.e., `ls` with no options)
---

### Week 3 (May 13 - May 17)
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

(Continuing to work on `C - ls` this week)

#### Monday
- `C - ls`
    - Complete `Task 0`

#### Tuesday
- `C - ls`
    - Complete `Task 1`

#### Wednesday
- `C - ls`
    - Complete `Task 2`

#### Thursday
- `C - ls`
    - Complete `Task 3`

#### Friday
- `C - ls`
    - Complete `Task 4`

---

### Week 4 (May 20 - May 24)
<table>
    <tbody>
        <tr>
            <th align="center">Project Closing (Wednesday @ 11:59PM)</th>
            <th align="center">Project Opening (Friday morning)</th>
        </tr>
        <tr>
            <td>
                <ul>
                    <li><code>C - ls</code></li>
                </ul>
            </td>
            <td>
                <ul>
                    <li><code>C - Shell v2</code> (next course)</li>
                </ul>
            </td>
        </tr>
    </tbody>
</table>

#### Monday
- `C - ls`
    - Begin `Task 5` (last required task)

#### Tuesday
- `C - ls`
    - Continue `Task 5` (last required task)

#### Wednesday
- `C - ls`
    - Complete `Task 5` (last required task)
- Project due at 11:59PM!

#### Thursday
- _Course closes at 11:59PM!_
- _PLD, 9:00AM-3:00PM_
    - Look ahead at `C - Shell v2` (next course, opens Friday)
        - Pick partners
        - Piping and redirection examples
