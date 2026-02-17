# OverTheWire Bandit Writeups (Level 0–20)
Author: Livinkumar J

This repository contains my learning notes and solutions for OverTheWire Bandit CTF (Level 0–20).

Skills Practiced:
- Linux commands
- File handling
- Permissions
- SSH
- Searching & filtering
- Encoding/decoding
- Networking basics

Note: Passwords are not shared for ethical reasons.

--------------------------------------------------

## Level 0 → Level 1

Goal: Login using SSH and read the readme file.

Commands Used:
ssh bandit0@bandit.labs.overthewire.org -p 2220  
ls  
cat readme  

Explanation:
- Connected to Bandit server using SSH
- Listed files using ls
- Opened readme file to get password

Screenshot:
![Level 0](lvel0.png)

--------------------------------------------------

## Level 1 → Level 2

Goal: Password stored in file named "-"

Commands Used:
ls  
cat ./-  

Explanation:
- "-" is treated as option
- Used ./ to read file safely

Screenshot:
![Level 1](lvel1.png)

--------------------------------------------------

## Level 2 → Level 3

Goal: File name contains spaces

Commands Used:
ls  
cat "spaces in this filename"  

Explanation:
- Used quotes to handle spaces

Screenshot:
![Level 2](lvel2.png)

--------------------------------------------------

## Level 3 → Level 4

Goal: Password inside hidden file

Commands Used:
ls -a  
cat .hidden  

Explanation:
- -a shows hidden files

Screenshot:
![Level 3](lvel3.png)

--------------------------------------------------

## Level 4 → Level 5

Goal: Find human-readable file

Commands Used:
ls  
file ./*  
cat ./-file07  

Explanation:
- Used file command to identify readable file

Screenshot:
![Level 4](lvel4.png)

--------------------------------------------------

## Level 5 → Level 6

Goal: Find file with:
- size 1033 bytes
- not executable
- human readable

Commands Used:
find . -type f -size 1033c ! -executable  
cat <filename>  

Explanation:
- Used find with conditions

Screenshot:
![Level 5](lvel5.png)

--------------------------------------------------

## Level 6 → Level 7

Goal: Find file owned by bandit7 & group bandit6

Commands Used:
find / -user bandit7 -group bandit6 -size 33c 2>/dev/null  
cat <file>  

Explanation:
- Searched entire system
- Ignored permission errors

Screenshot:
![Level 6](lvel6.png)

--------------------------------------------------

## Level 7 → Level 8

Goal: Password near word "millionth"

Commands Used:
grep millionth data.txt  

Explanation:
- Used grep to find keyword

Screenshot:
![Level 7](lvel7.png)

--------------------------------------------------

## Level 8 → Level 9

Goal: Find unique line

Commands Used:
sort data.txt | uniq -u  

Explanation:
- Sorted data
- Found unique value

Screenshot:
![Level 8](lvel8.png)

--------------------------------------------------

## Level 9 → Level 10

Goal: Password inside binary file

Commands Used:
strings data.txt | grep "="  

Explanation:
- Extracted readable text from binary

Screenshot:
![Level 9](lvel9.png)

--------------------------------------------------

## Level 10 → Level 11

Goal: Base64 encoded password

Commands Used:
base64 -d data.txt  

Explanation:
- Decoded Base64 content

Screenshot:
![Level 10](lvel10.png)

--------------------------------------------------

## Level 11 → Level 12

Goal: ROT13 encrypted text

Commands Used:
cat data.txt | tr 'A-Za-z' 'N-ZA-Mn-za-m'  

Explanation:
- Applied ROT13 decoding

Screenshot:
![Level 11](lvel11.png)

--------------------------------------------------

## Level 12 → Level 13

Goal: Multiple compressed layers

Commands Used:
xxd -r data.txt > file  
gzip -d  
bzip2 -d  
tar -xvf  

Explanation:
- Reversed hex dump
- Extracted compressed layers step by step

Screenshot:
![Level 12](lvel12.png)

--------------------------------------------------

## Level 13 → Level 14

Goal: Login using private SSH key

Commands Used:
ssh -i sshkey.private bandit14@localhost -p 2220  

Explanation:
- Used private key authentication

Screenshot:
![Level 13](lvel13.png)

--------------------------------------------------

## Level 14 → Level 15

Goal: Send password to port using netcat

Commands Used:
nc localhost 30000  

Explanation:
- Sent password to service running on port

Screenshot:
![Level 14](lvel14.png)

--------------------------------------------------

## Level 15 → Level 16

Goal: Connect using SSL

Commands Used:
openssl s_client -connect localhost:30001  

Explanation:
- Connected using encrypted SSL session

Screenshot:
![Level 15](lvel15.png)

--------------------------------------------------

## Level 16 → Level 17

Goal: Find correct port using nmap

Commands Used:
nmap -p 31000-32000 localhost  

Explanation:
- Scanned ports to find SSL service

Screenshot:
![Level 16](lvel16.png)

--------------------------------------------------

## Level 17 → Level 18

Goal: Compare two files

Commands Used:
diff passwords.old passwords.new  

Explanation:
- Found changed line using diff

Screenshot:
![Level 17](lvel17.png)

--------------------------------------------------

## Level 18 → Level 19

Goal: Bypass restricted shell

Commands Used:
ssh bandit18@bandit.labs.overthewire.org -p 2220 "cat readme"  

Explanation:
- Executed command during login

Screenshot:
![Level 18](lvel18.png)

--------------------------------------------------

## Level 19 → Level 20

Goal: Use setuid binary

Commands Used:
./bandit20-do cat /etc/bandit_pass/bandit20  

Explanation:
- Used special binary to read protected file

Screenshot:
![Level 19](lvel19.png)
