# JavaScript-Practice
This repo is to practice and understand js concepts 

## Intro

### Everything in javascript happens inside an execution context
    -this execution context is like a box or container in which whole javascript code is executed
    -In this box there is 2 components:
        1) Memory component - also know as Environment variable - this is where all the variables and functions are stored in key value pairs
        2) Code component -also known as Thread of Execution - this is where code is executed one line at a time.

### JavaScript is a synchronous single-threaded language
    -Singel threaded means javascript can execute one command at a time
    -and synchronous means it can execute one command at a time in a specific order

___

## How JavaScript Code is Executed(What actually happens when you run a js code)
- so when you actually run a js code a execution context is created for example:
    ``` js
    //see the table to understand how the memory is allocated 
    var n = 2 // as soon as it reads this line it allocates memory to n
    function square (num) { // similarly it allocates memory to other variable and functions // num is the parameter of the function
        var ans = num * num; 
        return ans;
    }
    var square2 = square(n); // n is the argument 
    var square4 = square(4);
    ```

- so  when the above code is run a global execution context is created below is the tabular representation of it:
    
    | Memory               | Code      |
    |----------------------|-----------|
    | n: undefined         |           |
    | square: {...}        |           |
    | square2: undefined   |           |
    | square4: undefined   |           |

- so this execution context is created in two phases:
    - the first phase is known as the **Creation Phase** Also known as the __Memory Creation Phase__
        - In these phase javascript will allocate memory to all the variables and functions 
        - That is as the js encounters the line of code it allocates memory to the variable or function which is there in the line of code 
        - for variable it stores special value called `undefined` (_undefined_ is a like a placeholder, you'll get to know more about it down)
        - for functions it stores the whole code of the function inside the memory space `{...}` the whole code is stored in the memory.
    - Phase Two is the **Code Execution Phase** 
        - so in this phase javascript once again runs through the whole javascript program line by line and executes the code. 
        - so this is when all the calculation of the program is done
        - Understanding what actually happens line by line:
            - so as the code runs again when it encounters the `var n = 2` again in the first line it actually stores the 2 in the placeholder n, so in place of `n: undefined` it will be `n: 2` in memory component of execution context.
            - Now at the 2 to 5 there is nothing to execute so then it moves to the 6th line
            - Now at this line that is `var square2 = square(n);` there something interesting happens:
            - Here the funtion is invoked that is the function is executed - whenever the you see something like this `square(n)` it means the function is being executed. 
            - So function is basically like a mini program and when this is invoked then all together a new **Exectuion Context** is created, for that mini program. below is the example:

                | Memory                            | Code                      |
                |-----------------------------------|---------------------------|
                | n: undefined                      |                           |
                | square: {...}                     |                           |
                | square2: undefined                |                           |
                | square4: undefined                |                           |
                |                                   | | Memory         | Code  ||
                |                                   | |----------------|-------||
                |                                   | | num: undefined |       ||
                |                                   | | ans: undefined |       ||

            - so here again a new execution context is created which has the same two component memory and code so again there will two phases involved i.e
                - 1) **Memory Creation** : In this we are the memory for the function code will be allocated
                    ```js
                    function square (num) { 
                        var ans = num * num; 
                        return ans;
                    }
                    ```
                - so num and ans will be allocated memory with undefined stored in them in the first phase 
                - 2) In phase two each line of the code will be executed:
                - so `num: undefined` this will updated to `num: 2` which is passed as a argument to num parameter  
                    | Memory         | Code  |
                    |----------------|-------|
                    | num: 2         |       |
                    | ans: undefined |       |





