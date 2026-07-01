# Variable Initialization

<img src = "/images/ROM.png" width = 80%>

<img src = "/images/RAM.png" width = 80%>

<img src = "/images/StaticVariableWithInitialValue.png" width = 80%>

<img src = "/images/StaticVariableWithoutInitialValue.png" width = 80%>


## Question: Why aren't static variables with initial values simply stored in RAM from the beginning? Why must they be copied from ROM to RAM?

Because **RAM loses its contents when power is removed**, while ROM/Flash retains data.

When the program is built, the compiler/linker stores the initial values (i = 1, j = 10) in ROM/Flash. 

At startup, the runtime copies those values into RAM so the variables **can be modified during execution**.
