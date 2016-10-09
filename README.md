# About Set
Esoteric **Set** programming language - Only one command, endless possibilities! Based off the [original specification](https://www.reddit.com/r/esolangs/comments/54b0b1/set_an_language_with_1_command/) by reddit user [qwertyu63](https://www.reddit.com/user/qwertyu63). Developed by [Matheus Avellar](https://github.com/MatheusAvellar)

# Variables
**Set** supports 52 assignable variables. Each variable is a single upper or lower case letter and stores a single unbounded integer.
All lower case variables are initialized to 0; all upper case variables are initialized to their ASCII representation (65-90).
There is also a special system variable indicated by a question mark (`?`), which contains the line of code currently being executed.

# Commands (`set A B`)
As previously estabilished, there is only 1 command in **Set**: `set A B`.
Each `set` command must be on its own line, and is case insensitive.
`set` takes two arguments, each separated by 1 space (`set█A█B`):

* `A` must be either a variable or an exclamation point.
* `B` must be either a variable, an exclamation point, a combiner or an integer.

On most occasions, the `set` command will set the variable on argument `A` to the value of argument `B`.

Example:
```
set k 10  > Assings 10 to the variable 'k'
set a A   > Assings ASCII value of 'A' (65) to the variable 'a'
```
<hr/>
## Exclamation point (`!`)
Exclamation points indicate input/output. When used as argument:

* `A`: Outputs the ASCII character matching argument `B` to the screen.
* `B`: Takes **one** ASCII character as input and sets argument `A` to the matching integer.

Example:
```set
> When used as argument "A"
set ! A
set ! B
> Outputs: AB


> When used as argument "B"
set a !  > Prompts the user for a one-character-long value input
         > and assigns it to the variable 'a'

set b !
> Received "B"
> 'b' now equals 66
```

<hr/>
## Question mark (`?`)
Question marks represent the line of code which is being executed. When used as argument:

* `A`: Works as a 'go to' function. Defines the value of `B` as the line of code to be executed next
* `B`: Acts as a regular variable. Assigns argument `A` the number of the current line of code

Example:
```set
set a ?  > Defines 'a' as 1
set ? 1  > Jumps to line 1, thus creating an infinite loop
set z 1  > This line will never be executed, as the code cannot reach it
```
<hr/>
## Combiners (`(N+M)`)
Combiners allow you to combine two numbers into one. There are two valid combiners; each used in the place of argument `B`:

* `(N+M)`: is equal to `N` plus `M`.
* `(N-M)`: is equal to `N` minus `M`.

`N` and `M` must be either a **variable** or a **single digit integer**.

Example:
```set
set b (A+1)  > Adds 1 to ASCII value of 'A' (65)
             > b becomes 66 (ASCII for 'B')
```

<hr/>
## Conditionals (`[X=Y]`)
By putting a conditional in front of a `set` command, you can make that command only run in some situations. There are two valid conditionals:

* `[X/Y]`: `X` must not equal `Y`.
* `[X=Y]`: `X` must equal `Y`.

If the condition is not met, the command is not run. X and Y must be either a variable or a single digit integer.

Example:
```set
set a 1
[a=0] set a 2  > If 'a' equals 0, then set 'a' to 2
[a/0] set a 3  > If 'a' is not equal to 0, then set 'a' to 3

> 'a' is 3
```

<hr/>
# Comments

Although not specified in the original concept of the **Set** language,
the `>` (greater than) character may be used to insert comments on the **Set** code.

Example:
```set
> Whole line comment. Starts with a '>' symbol. This line is completely ignored by the parser.
set a 10  > Inline comment. Starts after a 'set' command, which runs normally.

set b 20  > Convetionally, inline comments should always be separated of
          > the 'set' command by at least 2 spaces
```
