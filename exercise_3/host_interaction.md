# Host interaction

Rmember: look at `exercise_2/shellcode.md` for compilation instructions.

Exercises:
1. Look in `riscvm.cpp` and make a list of all the available syscalls and their numbers
    memcpy 			10006
    memset 			10007
    memmove			10008
    memcmp 			10009
    print_wstring	10100
    print_string	10101
    print_int		10102
    print_hex		10103
    print_tag_hex	10104
    resolve_import	10105
2. Implement the `print_string` syscall stub in `dbgprint.c`
3. In `import.c`, resolve the `puts` function (`module=0`) and print `Hello from RISC-V!` to the console using `host_call` (you will again need to implement the syscall stubs)
4. Bonus: create a new `secret.c` payload that opens and reads `secret.txt` using `resolve_import` and `host_call` (hard)
