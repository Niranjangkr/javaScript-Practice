# javaScript-Practice
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
    function square (num) { // similarly it allocates memory to other variable and functions
        var ans = num * num; 
        return ans;
    }
    var square2 = square(n);
    var square4 = square(4)
    ```

- so  when the above code is run a global execution context is created below is the tabular representation of it:
    
    | Memory               | Code           |
    |----------------------|----------------|
    | n: undefined         | Row 1          |
    | square: {...}        | Row 2          |
    | square2: undefined   | Row 2          |
    | square4: undefined   | Row 2          |

- so this execution context is created in two phases:
    - the first phase is known as the **Creation Phase** Also known as the __Memory Creation Phase__
        - In these phase javascript will allocate memory to all the variables and functions 
        - That is as the js encounters the line of code it allocates memory to the variable or function which is there in the line of code 
        - for variable it stores special value called `undefined` (_undefined_ is a like a placeholder, you'll get to know more about it down)
        - for functions it stores the whole code of the function inside the memory space `{...}` the whole code is stored in the memory  


