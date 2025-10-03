# Exercise 1: VM Obfuscation Basics

Change the working directory:

```sh
cd exercise_1
```

In this exercise we are going to explore the concept of VM obfuscation.

1. Build `minivm.cpp`:
   ```sh
   clang-20 -O3 -fno-slp-vectorize -std=c++17 minivm.cpp -o minivm
   ```
2. Run the VM (`./minivm 1 2 3 4`) and do the following exercises:
   - Extract the active VM bytecode (look at the source code).
        OR(REG(4), REG(0), REG(1)),
        XOR(REG(5), REG(2), REG(3)),
        ADD(REG(6), REG(4), REG(5)),
        RET(REG(6)),
   - How many registers does the VM have?
        It has 257, 256 registries and the instruction pointer.
   - Make a list of all the operations and what they do.
        ret
        add
        movimm
        cmp
        jcc
        xor
        or
        mul
   - What does the active VM bytecode do? Write it as C pseudocode.
        OR(REG(4), REG(0), REG(1)),
        XOR(REG(5), REG(2), REG(3)),
        ADD(REG(6), REG(4), REG(5)),
        RET(REG(6)),



        reg[4] = reg[0] or reg[1];
        reg[5] = reg[2] xor reg[3];
        reg[6] = reg[4] + reg[5];
        ret reg[6];

        // "checking" that the pseudocode matches the actual result of the program
        reg[4] = 1 or 2 = 3;
        reg[5] = 3 xor 4 = 7; // 0011 xor 0100
        reg[6] = 3 + 7 = 10;
        ret reg[6];


3. For this exercise you will write your own bytecode. Look at the commented-out example code to figure out how to do it.
   - Implement a function that adds the first two arguments together: `return a + b`
   - Implement a function that multiplies the first two arguments together: `return a * b`
   - Implement a function that implements: `return a - b`
   - Implement a function that implements: `return a == 42 ? 1337 : 0`

If you finish early, here are a few bonus exercises (not required):

1. Extend `minivm.cpp` so it becomes possible to implement `fib(n)` (iterative).
2. Implement the `fib(n)` function to verify your new opcodes.

Do these exercises for `minivm-tailcall.cpp` (make sure to recompile):

3. Analyze the `minivm` binary in you favorite disassembler/decompiler. Would it be difficult to write a disassembler for the VM bytecode if the opcodes were switched around?
4. Which C++ attribute is responsible for the `jmp reg` opcode at the end of the handler?
