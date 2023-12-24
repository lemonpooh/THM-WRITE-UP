![image](https://github.com/lemonpooh/THM-WRITE-UP/assets/59368650/0a9839c8-259d-43c0-961d-4da5227ac800)

After getting non-interactive shell, we need to change it to interactive shell by inserting bellowing command on the victim shell.

step 1. **export TERM=xterm**

step 2. **python2 -c 'import pty;pty.spawn("/bin/bash")'**

step 3. **press CTRL + Z** 不一定需要

