![image](https://github.com/lemonpooh/THM-WRITE-UP/assets/59368650/b50315fe-6839-4f98-b00f-2165665eb5c5)
After getting non-interactive shell, we need to change it to interactive shell by inserting bellowing command on the victim shell.

step 1. **export TERM=xterm**

step 2. **python2 -c 'import pty;pty.spawn("/bin/bash")'**

step 3. **press CTRL + Z** 不一定需要

