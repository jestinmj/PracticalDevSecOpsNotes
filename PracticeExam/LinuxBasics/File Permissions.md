You can provide executable permissions to a file using the chmod command
```
cat > myfile <<<EOL
ls
EOL
```

verify contents with `cat`
Verify permissions using `ls -l`
Verify permissions using `stat myfile`
Give executable permissions using chmod `chmod +x myfile`
run a file using `./myfile`

`sudo` command to run with root privileges

create a new user
`echo -e "pdevsecops\npdevsecops" | adduser --gecos "" john

usermod command to add user to sudo group
`usermod -aG sudo john`

become a user
`sudo su - john`


Now, try reading the content of a very sensitive file on Linux, i.e., /etc/shadow.


cat /etc/shadow

Command Output
cat: /etc/shadow: Permission denied
Permission denied. Even though we are logged in as John we still have to explicitly specify sudo before the actual command to try performing an operation as a privileged user.

So let’s try reading the content of /etc/shadow again, but this time with sudo prefix.
`echo pdevsecops | sudo -S cat /etc/shadow`
