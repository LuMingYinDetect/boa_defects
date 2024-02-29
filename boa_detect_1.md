Affected Version:
boa 0.94.14rc21-5 7b13e12faf3ca5543b371987a89fe80cf31ff43c

Vulnerability Description:
The vulnerability is a memory leak bug located at line 233 of the file /boa/src/get.c. This vulnerability could potentially be exploited maliciously to cause resource exhaustion and denial of service attacks.

boa download address:
https://github.com/gpg/boa.git

Detailed Description of the Defect:

1.In the 186th line of the /boa/src/get.c file, a pointer named "port" is defined. In the 196th line, the function "strdup" allocates a dynamic memory area for this pointer. When the if statement in the 197th line returns false, it means that the memory area has been successfully allocated. When the if statement in the 230th line returns true, the program returns in the 233th line. During this process, the memory area pointed to by the variable "port" has not been freed, thus causing a memory leak defect, as shown in the following figure:

![image](https://github.com/LuMingYinDetect/boa_defects/blob/main/boa_1.png)
