
## Pattern Creator
```
/usr/share/metasploit-framework/tools/exploit/pattern_create.rb -l 2700
```

## Get pattern location
```
/usr/share/metasploit-framework/tools/exploit/pattern_offset.rb -q 39694438
```
## Executable dlls using mona
```
!mona modules
```
### Find ASLR and DEP false dll which range don't have bad characters

## Search commands
```
jmp esp
```
## Search command sequence
```
push esp
retn
```

## Find opcode of given instruction
```
nasm_shell.rb
nasm> jmp esp
```
## search instructions using mona
```
!mona find -s "\xff\xa4" -m slm.dll
```
