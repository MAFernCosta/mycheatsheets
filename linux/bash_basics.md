# Bash basic commands

## File Commands
| Command                  | Description                               |
|:-------------------------|:------------------------------------------|
| `ls`                       | List the content of the current directory |
| `ls -R`                    | List subdirectories recursively           |
| `ls -a`                    | List all contents, including hidden files |
| `ls -l`                    | List contents with detailed information   |
| `pwd`                      | Show the current directory                |
| `cd folder1`               | Change working directory to folder1       |
| `cd`                       | Return to $HOME directory                 |
| `cd ..`                    | Go up one directory                       |
| `cd -`                     | Return to the previous directory          |
| `cp source destination`    | Copy source to destination                |
| `cp -r source destination` | Copy folder recursively                   |
| `mv source destination`    | Move or rename file                       |
| `rm file1`                 | Remove file                               |
| `rm -f file1`              | Force remove file without prompt          |
| `rm -r folder`             | Remove folder recursively                 |
| `mkdir foldername`         | Create a new folder                       |
| `rmdir foldername`         | Remove empty folder                       |
| `file file1`               | Show file type                            |
| `cat file1 file2`          | Concatenate files                         |
| `cat > file1`              | Redirect standard input to file           |
| `less file1`               | View and paginate file                    |
| `head file1`               | Show first 10 lines                       |
| `tail file1`               | Show last 10 lines                        |
| `chmod 777 file`           | Change file permission                    |
| `chown user:group file`    | Change file ownership                     |
| `ln -s source destination` | Create symbolic link                      |

## System commands

| Command                          | Description                 |
|:---------------------------------|:----------------------------|
| `uname -a   `                      | Show system and kernel info |
| `head -n1 /etc/issue   `           | Show distribution           |
| `mount    `                        | Show mounted filesystems    |
| `date   `                          | Show system date            |
| `uptime  `                         | Show system uptime          |
| `whoami  `                         | Show current username       |
| `w   `                             | Display who is online       |
| `man command`                      | Show manual for command     |
| `mount -o loop cdrom.iso /mnt/dir` | Mount ISO image             |
| `cat /proc/partitions   `          | Show all partitions         |
| `grep MemTotal /proc/meminfo `     | Show total RAM              |
| `grep model name /proc/cpuinfo `   | Show CPU info               |
| `lspci -tv `                       | Show PCI info               |
| `lsusb -tv `                       | Show USB info               |
| `!! `                              | Repeat last command         |
| `exit `                            | Logout current session      |

## File Searching Commands

| Command                | Description                                   |
|:-----------------------|:----------------------------------------------|
| `grep pattern files`     | Search for pattern in files                   |
| `grep -i`                | Case-insensitive search                       |
| `grep -r`                | Recursive search                              |
| `grep -v`                | Inverted search                               |
| `grep -o`                | Show only matched parts                       |
| `locate file1`           | Find file                                     |
| `whereis command`        | Find binary/source/manual                     |
| `which app`              | Locate a command                              |
| `look string file1`      | Find lines starting with string               |
| `find /dir/ -user name`  | Find files owned by user                      |
| `find /dir/ -mmin num`   | Find files modified less than num minutes ago |
| `find /dir/ -name name*` | Find files starting with name                 |

## File Encryption and Compression

| Command                          | Description              |
|:---------------------------------|:-------------------------|
| `gpg -c file `                     | Encrypt file             |
| `gpg file.gpg`                     | Decrypt file             |
| `tar -cf archive.tar foo bar `     | Create .tar archive      |
| `tar -xf archive.tar`              | Extract .tar archive     |
| `tar -czf archive.tar.gz foo bar`  | Create .tar.gz archive   |
| `tar -xzf archive.tar.gz`          | Extract .tar.gz archive  |
| `tar -cjf archive.tar.bz2 foo bar` | Create .tar.bz2 archive  |
| `tar -xjf archive.tar.bz2`         | Extract .tar.bz2 archive |
| `gzip file1`                       | Compress file            |
| `gzip -d file1.gz`                 | Decompress file          |

## Process Management

| Command      | Description                |
|:-------------|:---------------------------|
| `ps`           | Show snapshot of processes |
| `top`          | Show real-time processes   |
| `kill pid`     | Kill process by ID         |
| `pkill name`   | Kill process by name       |
| `killall name` | Kill all processes by name |

## SSH Commands

| Command                     | Description                |
|:----------------------------|:---------------------------|
| `ssh $USER@$HOST`             | Connect to host            |
| `ssh $USER@$HOST command`     | Run command remotely       |
| `ssh $USER@$HOST -p 1234`     | Connect via specific port  |
| `scp file1 $USER@$HOST:file1` | Copy file to remote host   |
| `scp $USER@$HOST:file1 file1` | Copy file from remote host |
| `scp -r foo $USER@$HOST:/bar` | Copy folder to remote host |

## Disk Space

| Command       | Description                    |
|:--------------|:-------------------------------|
| `df -h`         | Show free space on filesystems |
| `df -i`         | Show free inodes               |
| `du -h folder`  | Show folder usage              |
| `du -sh folder` | Show total size of folder      |

## Package Installation

| Command              | Description                |
|:---------------------|:---------------------------|
| `dpkg -i package.deb`  | Install .deb package       |
| `rpm -Uvh package.rpm` | Install .rpm package       |
| `fdisk -l`             | Show disk partitions       |
| `free`                 | Show memory and swap usage |

## Keyboard Shortcuts

| Shortcut         | Action                 |
|:-----------------|:-----------------------|
| Ctrl + Shift + C | Copy text              |
| Ctrl + Shift + V | Paste text             |
| Ctrl + Z         | Sleep program          |
| Ctrl + C         | Stop current command   |
| Ctrl + R         | Search command history |
| Ctrl + U         | Cut from start of line |
| Ctrl + K         | Cut to end of line     |
| Ctrl + A         | Go to start of line    |
| Ctrl + E         | Go to end of line      |