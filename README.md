# computer_security_HW3-part1-

##Q1:
The assembly come contain GetmassageA and MessageBox API, it can be easyly find that two strings(No luck there, mate! Great work mate are related to MessageBoxA.<br>
![](https://github.com/lovethatcat/computer_security_HW3-part1-/raw/master/Images/01.PNG)<br>
from $6A 00 and $6A 30, those two lines are called from 0040124C and 00401245.<br>
![](https://github.com/lovethatcat/computer_security_HW3-part1-/raw/master/Images/02.png)<br>
the `cmp eax, ebx`will lead to the different address.if they are equal, the code will jump to the success box. And Je will check ZF mark, so only change the Z at `Je` commend in register window  to 1 will make the program always jump to the success box.<br>
![](https://github.com/lovethatcat/computer_security_HW3-part1-/raw/master/Images/03.PNG)<br>
Thus, it can be comfirm that if ZF==1, the program will always jump to `great work` massaage box, only change that two different registers to two indentical registers will make ZF always 1.<br>
The crackme_Y.exe is the program that change cmp eax,ebx to cmp eax,eax.<br>

##Q2:
To further understand this code, we can look at the function that generate eax and ebx. From Picture above, it can be found that eax is generate from CRACKME.0040137E, and ebx is generate from CRACKME.004013D8. Then we look inside those two blocks.<br>
For 0040137E,<br>
![](https://github.com/lovethatcat/computer_security_HW3-part1-/raw/master/Images/04.PNG)<br>
There is a call 004013d2, and ENTER it, it shows `sub AL, 20`, which means transfer the lower case of name to upper case. Here we can add a breadpoint to verify that at stack window. Then call 004013c2, which accumulate all ascii code of name. The most important line is call xor 5678,so the edi =edi xor 5678, then store in eax.

For 004013D8:
![](https://github.com/lovethatcat/computer_security_HW3-part1-/raw/master/Images/05.PNG)<br>
in this code, the password will xor 1234 and store in ebx. So, the logic is if the accumulation of the ascii code of upper case of name xor 5678== password xor 1234, the program will pass. So the password can be computed as password=accumulation of the ascii code of upper case of name xor 5678 Xor 1234.

<br>
My first name is Chen, the code is 17746
the given three name is :<br>
shifu:17745<br>
yujie:17866<br>
yiming:17793
