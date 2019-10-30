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
