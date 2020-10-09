# BOF
buffer overflow stuff

## Mona CheatSheet
Setup your working directory 

`!mona config -set workingfolder c:\mona\%p`

<br>
<br>


Generate a byte array

`!mona bytearray -b "\x00"`

<br>

Run your fuzzer till a crash

compare your stuff
`!mona compare -f C:\mona\bytearray.bin -a ESP`

<br>

Add newly found bad chars to your list to be removed, and regenerate your badchars list
`!mona bytearray -b "\x00\x0a"`

<br>

Resend the new list of badchars, and then compare again 
`!mona compare -f C:\mona\bytearray.bin -a ESP`


https://tryhackme.com/room/bufferoverflowprep 

https://www.youtube.com/watch?v=1X2JGF_9JGM 
