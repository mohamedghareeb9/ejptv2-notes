# Linux Foundations for Host-Based Testing

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
find /path -type f -exec grep -l "needle" {} +
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
Use `sudo su` to open a root shell and `exit` to leave it. Prefer the least privilege needed. Running a whole session as root increases the impact of mistakes.

## 9. Self-check
1. Difference between an absolute and relative path?
2. What does the append redirection operator do compared with overwrite?
3. Which command follows a log as new lines are written?
4. What does chmod 755 mean?
5. Why does execute permission have a different meaning on a directory?
6. When would you use ps aux instead of top?
7. Difference between APT and dpkg?

## 10. Vim essentials
Vim is a modal text editor.

| Mode | Purpose |
|---|---|
| Normal | Navigate and issue editing commands |
| Insert | Type text |
| Visual | Select text |
| Command-line | Save, quit, and search |

Basic sequence:
1. Open a file with `vim filename.txt`.
2. Press `i` to enter Insert mode.
3. Press Esc to return to Normal mode.
4. Use `:w` to save, `:q` to quit, `:wq` to save and quit, or `:q!` to quit without saving.

Other commands from the notes: `dd` deletes a line, `yy` copies a line, `p` pastes, `u` undoes, `Ctrl+r` redoes, `/text` searches, `n` moves to the next match, `gg` goes to the top, and `G` goes to the bottom.

## 11. File timestamps and locating files

~~~bash
touch empty.txt
locate file.txt
locate -i file
sudo updatedb
find / -name file.txt
find . -iname "*.txt"
find . -type f
find . -type d
find . -size +10M
find . -mtime -1
find . -perm 777
~~~

Remember: `locate` is fast because it searches a database and may be stale; `find` searches the filesystem and is more current but can be slower. The locate database can be refreshed with updatedb.

The notes also demonstrate actions on matches:

~~~bash
find . -name "*.tmp" -delete
find . -name "*.sh" -exec chmod +x {} +
find /path -type f -exec grep -l "needle" {} +
~~~

Review the matched paths before using deletion or bulk modification options.

## 12. Archives and compression
Archiving combines files; compression reduces data size. Common formats include tar, tar.gz, tar.bz2, tar.xz, zip, gz, bz2, and xz.

~~~bash
tar -cvf archive.tar folder/
tar -xvf archive.tar
tar -czvf archive.tar.gz folder/
tar -xzvf archive.tar.gz
tar -cjvf archive.tar.bz2 folder/
tar -xjvf archive.tar.bz2
zip -r archive.zip folder/
unzip archive.zip
tar -tvf archive.tar.gz
unzip -l archive.zip
~~~

Tar flags: c=create, x=extract, v=verbose, f=archive filename, z=gzip, j=bzip2, and J=xz. Single-file compressors such as gzip, bzip2, and xz commonly replace the original file with the compressed version; check the command behavior before using it on important data.

## 13. Additional self-check
1. Why does Vim start in Normal mode?
2. What is the difference between locate and find?
3. What does touch do to an existing file?
4. What is the difference between archiving and compression?
5. What do the z, j, and J flags mean in tar?

## 14. Additional regular-expression patterns
The practical notes also list these advanced patterns, with support depending on the regex engine:

| Pattern | Meaning |
|---|---|
| \d / \D | Digit / non-digit in engines that support these classes |
| \w / \W | Word character / non-word character |
| \s / \S | Whitespace / non-whitespace |
| \b / \B | Word boundary / non-word boundary |
| (.)\1 | Backreference: repeat the character captured by group 1 |
| (?<=foo)bar | Lookbehind example: match bar when preceded by foo |
| foo(?=bar) | Lookahead example: match foo when followed by bar |
| (?:foo|bar) | Non-capturing group |

Examples using PCRE mode with grep:

~~~bash
grep -P "(?<=foo)bar" file.txt
grep -P "foo(?=bar)" file.txt
grep -P "(.)\1" file.txt
grep -E "error|warning|failed" file.txt
grep -o "\b[a-zA-Z]{4}\b" file.txt
~~~

Basic grep, extended grep, and PCRE are different regex dialects. Use the appropriate option and verify which engine is available on the system.
