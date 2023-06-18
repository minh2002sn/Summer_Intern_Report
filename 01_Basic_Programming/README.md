# **Report Basic C**
## **1. Compiling process and Cross-compiler**
### **1.1. Compiling process**
The compilation process in C involves 4 steps: pre-processing, compiling, assembling and linking.

#### ***1.1.1. Pre-processing step***

This step includes:
- Removal of comments.
- Expansion of macros.
- Expansion of the included files.
- Conditional compilation.

The pre-processing output is .i files.

**Example 1:**

Header file:

    #ifndef MAIN_H
    #define MAIN_H
    
    void func_1();
    void func_2();
    
    #endif
Source file:

    /* Include main.h file */
    #include "main.h"

    /* Macro */
    #define PI          3.14
    #define SQUARE(a)   a*a

    /* main function */
    int main()
    {
        float f = SQUARE(2)*PI;
    }
Typing below command in terminal to generate main.i file:

    gcc -E main.c -o main.i

main.i file's content:

    # 0 "main.c"
    # 0 "<built-in>"
    # 0 "<command-line>"
    # 1 "/usr/include/stdc-predef.h" 1 3 4
    # 0 "<command-line>" 2
    # 1 "main.c"

    # 1 "main.h" 1



    void func_1();
    void func_2();
    # 3 "main.c" 2






    int main()
    {
        float f = 2*2*3.14;
    }
#### ***1.1.2. Compiling step***

This step is to compile .i files to .s file in assembly-level instruction.

**Example 2: Using main.c and main.h file in example 1**

Typing below command to terminal to generate main.s file:

    gcc -S main.c -o main.s

Content of main.s file:

    	.file	"main.c"
        .text
        .globl	main
        .type	main, @function
    main:
    .LFB0:
        .cfi_startproc
        endbr64
        pushq	%rbp
        .cfi_def_cfa_offset 16
        .cfi_offset 6, -16
        movq	%rsp, %rbp
        .cfi_def_cfa_register 6
        movss	.LC0(%rip), %xmm0
        movss	%xmm0, -4(%rbp)
        movl	$0, %eax
        popq	%rbp
        .cfi_def_cfa 7, 8
        ret
        .cfi_endproc
    .LFE0:
        .size	main, .-main
        .section	.rodata
        .align 4
    .LC0:
        .long	1095300547
        .ident	"GCC: (Ubuntu 11.3.0-1ubuntu1~22.04.1) 11.3.0"
        .section	.note.GNU-stack,"",@progbits
        .section	.note.gnu.property,"a"
        .align 8
        .long	1f - 0f
        .long	4f - 1f
        .long	5
    0:
        .string	"GNU"
    1:
        .align 8
        .long	0xc0000002
        .long	3f - 2f
    2:
        .long	0x3
    3:
        .align 8
    4:

#### ***1.1.3. Assembling step***

This step is to compile .s files to .o files in machine-level instruction.

Number of .o files generated is number of .c files.

**Example 3: Using main.c and main.h file in example 1**

Typing below command to terminal to generate main.s file:

    gcc -c main.c -o main.o

Content of main.o file:

    ELF>@@
    ��UH����E��]���HAGCC: (Ubuntu 11.3.0-1ubuntu1~22.04.1) 11.3.0GNU�zRx�E�C
    S��main.cmain�������� .symtab.strtab.shstrtab.rela.text.data.bss.rodata.comment.note.GNU-stack.note.gnu.property.rela.eh_frame @@p&\,\1\90`.B�R� j�8e@�	�x	`
    �t

#### ***1.1.4. Linking step***

This step is to link all .o files and static library files to generate executable file.

### **1.2 Cross compiler**

A cross compiler is a compiler capable of creating executable code for a platform other than the one on which the compiler is running.

Cross compiler has 5 phases:

- Lexical Analysis.
- Syntactic Analysis.
- Intermediate Code Generating.
- Optimization.
- Code Generation.


## **3. Makefile**
### **3.1. Rule**

A Makefile is a file name Makefile or makefile, that include a set of rules. A rule's structure looks like:

![01_makefile_rule](./images/01_makefile_rule.png)

with:
- The targets are file names, separated by spaces. Typically, there is only one per rule.
- The actions are a series of steps typically used to make the target(s). These need to start with a tab character, not spaces.
- The dependencies are also file names, separated by spaces. These files need to exist before the commands for the target are run. If the dependencies file do not exist, the rules that has same target's name will run.

To run a rule, type in terminal the following command:

    make target_name

### **3.2. Variables**

A variable is a name defined in a makefile to represent a string of text, called the variable's value.



`var := 1`