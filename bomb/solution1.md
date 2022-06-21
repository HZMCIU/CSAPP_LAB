# phase 1

## prerequisite

1. `%rdi` save the first arguement, `%rsi` save the the second arguement.
2. return value is saved in `%rax`

```asm
0000000000400ee0 <phase_1>:
  400ee0:	48 83 ec 08          	sub    $0x8,%rsp
  400ee4:	be 00 24 40 00       	mov    $0x402400,%esi
  400ee9:	e8 4a 04 00 00       	callq  401338 <strings_not_equal>
  400eee:	85 c0                	test   %eax,%eax
  400ef0:	74 05                	je     400ef7 <phase_1+0x17>
  400ef2:	e8 43 05 00 00       	callq  40143a <explode_bomb>
  400ef7:	48 83 c4 08          	add    $0x8,%rsp
  400efb:	c3                   	retq   
```

## solve

1. `call ((int(*)()) strings_not_equal)("1", "1")`
  get result `$1=0`
  so in order to pass `explode_bomb`, string in `(%rdi)` should equal to string in `(%rsi)`
2. `x/s $rsi` 
  print the string stored in `(%rsi)`

## reference 

1. [10.5 Output Formats](https://sourceware.org/gdb/onlinedocs/gdb/Output-Formats.html)
2. [10.6 Examining Memory](https://sourceware.org/gdb/onlinedocs/gdb/Memory.html)
3. [Debugging IA32 Assembly Code with gdb (and ddd)](https://www.cs.swarthmore.edu/~newhall/cs31/resources/ia32_gdb.php)
4. [17.5 Calling Program Functions](https://sourceware.org/gdb/onlinedocs/gdb/Calling.html)
