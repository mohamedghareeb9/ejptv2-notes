# Linux Foundations for Host-Based Testing

**Source basis:** eJPTv2_Pr.pdf

## 1. Navigation and files
~~~bash
pwd
ls
ls -a
ls -l
ls -lah
cd /path
cd ..
cd /
cat file.txt
mkdir lab
nano notes.txt
cp source dest
mv source dest
rm file
rm -r directory
~~~

An absolute path starts at the filesystem root. A relative path is interpreted from the current working directory. Be careful with recursive deletion.

## 2. Output redirection and pipelines
~~~bash
echo "hello" > output.txt
echo "another line" >> output.txt
cat output.txt | grep "hello"
wc -l output.txt
~~~

A pipe sends one command's standard output to another command's standard input. The single greater-than operator overwrites or creates a file; the double greater-than operator appends.

## 3. Reading and searching text
| Command | Use |
|---|---|
| cat | Print file contents |
| less | Read long output and move backward/forward |
| more | Page through output |
| head | Show beginning of a file |
| tail | Show end of a file |
| tail -f | Follow new log entries |
| nl | Display line numbers |
| grep | Find matching lines |
| find | Search for files and directories |
| sed | Transform text streams |
| awk | Process structured text |

~~~bash
less /var/log/auth.log
head -n 20 file.txt
tail -n 20 file.txt
tail -f /var/log/auth.log
grep -i "failed" /var/log/auth.log
find /home -type f -name "*.txt"
find /home -type d -name "projects"
find /path -type f -exec grep -l "needle" {} \\;
~~~

## 4. Regular expressions
A regular expression describes a text pattern. The practical notes use it with grep, sed, and awk.

| Pattern | Meaning |
|---|---|
| . | Any single character |
| ^ | Start of line |
| $ | End of line |
| * | Zero or more of preceding item |
| + | One or more of preceding item (extended regex) |
| ? | Zero or one of preceding item (extended regex) |
| [abc] | One character from the set |
| [^0-9] | One character that is not a digit |
| (a|b) | Alternative/grouping in extended regex |
| backslash | Escape a special character |

~~~bash
grep -E "error|warning|failed" file.txt
grep -i "admin" file.txt
sed 's/old/new/g' file.txt
awk '{print $1}' file.txt
~~~

Regex dialects differ. A pattern supported by PCRE may not work unchanged in basic grep.

## 5. Permissions
Linux permissions are grouped into owner, group, and others. Each can have read, write, and execute permissions.

| Permission | Symbol | Numeric value |
|---|---|---:|
| Read | r | 4 |
| Write | w | 2 |
| Execute | x | 1 |

~~~bash
ls -lah
chmod 755 script.sh
chmod u+x script.sh
chmod g-w file.txt
chmod a+r file.txt
chmod -R 755 directory/
~~~

The mode 755 means owner has rwx and group/others have r-x. For a regular file, execute permission allows it to run as a program/script. For a directory, read allows listing entries and execute allows traversing/searching it. Recursive permission changes should be used carefully.

## 6. Processes and system information
~~~bash
ps aux
top
htop
kill <PID>
free -h
df -h
ip addr
~~~

ps aux is a process snapshot. top and htop provide a continuously updating view. A PID identifies a running process.

## 7. Help and package management
~~~bash
man nmap
whatis grep
apropos network
info coreutils
sudo apt install <package>
sudo snap install <package>
sudo dpkg -i <package.deb>
~~~

- man opens a command manual.
- whatis gives a short description.
- apropos searches manual descriptions by topic.
- info opens GNU documentation where available.
- APT installs repository packages and resolves dependencies.
- Snap installs Snap packages.
- dpkg installs a local Debian package; dependency repair may be needed separately.

## 8. Privilege context
The source notes introduce sudo su to open a root shell and exit to leave it. Prefer the least privilege needed. Running a whole session as root increases the impact of mistakes.

## 9. Self-check
1. Difference between an absolute and relative path?
2. What does the append redirection operator do compared with overwrite?
3. Which command follows a log as new lines are written?
4. What does chmod 755 mean?
5. Why does execute permission have a different meaning on a directory?
6. When would you use ps aux instead of top?
7. Difference between APT and dpkg?
