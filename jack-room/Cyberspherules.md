Room: https://tryhackme.com/room/cyberspherules

- bypass the ext_denylist by uploading the reverseshell.php to the path using PHPpentester usually, generated from the revshell.com

Code: https://pastebin.com/V75YLbQj
- rename it to .phtml
- run nc 1st
- execute the browser
- we got user shell

check for sudo user
- id
- sudo su

root shell gained
