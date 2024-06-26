# How does a C program work

This is the first program written in C. Run this program requires to invoke the  gcc compiler which, in turn, will
produce the **a.out** file.  
The latter is a binary file derived from the conversion of the firstprog.c in machine code (0s and 1s) performend by the gcc compiler. Now you can run the a.out file to execute the program.

__prompt commands:__
```
    gcc program_name.c
    ./a.out
```

Using `objdumb` tool, you can check out the content of the binary file **a.out**.  
Running the following command, you'll obtain the first 20 rows of the binary file after the regular expression _main_:

```
    objdump -D a.out | grep -A20 main.:
```  
After running this command, based on your machine, you will have something similar to the underlying lines in your prompt window:  
``` 
    1149:	f3 0f 1e fa          	endbr64
    114d:	55                   	push   %rbpgdb
    114e:	48 89 e5             	mov    %rsp,%rbp
    1151:	48 83 ec 10          	sub    $0x10,%rsp
    1155:	c7 45 fc 00 00 00 00 	movl   $0x0,-0x4(%rbp)
    115c:	eb 13                	jmp    1171 <main+0x28>
    115e:	48 8d 05 a3 0e 00 00 	lea    0xea3(%rip),%rax        # 2008 <_IO_stdin_used+0x8>
    1165:	48 89 c7             	mov    %rax,%rdi
    1168:	e8 e3 fe ff ff       	call   1050 <puts@plt>
    116d:	83 45 fc 01          	addl   $0x1,-0x4(%rbp)
    1171:	83 7d fc 09          	cmpl   $0x9,-0x4(%rbp)
    1175:	7e e7                	jle    115e <main+0x15>
    1177:	b8 00 00 00 00       	mov    $0x0,%eax
    117c:	c9                   	leave
    117d:	c3                   	ret
``` 
The first column stand for the addresses memory of each instruction converted in hexadecimal notation. 
The central column represent the instruction in hexadecimal form. Eventually, on the far right end side, 
there are the instructions expressed in assemply.
