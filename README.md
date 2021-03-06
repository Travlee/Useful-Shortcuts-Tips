# Useful Shortcuts & Tips

*Shortcuts for applications: VS Code, Bash shell, Git, and Vim*. Also some tips!

*By Travis Lee Presnell*



## Visual Studio Code

`Ctrl + W` - Closes active file

`Ctrl + B` - Toggle File Explorer

`Ctrl + PageUp/Down` - Cycle editors

`Ctrl + P` - Navigate to File

`Ctrl + Shift + O` - Navigate to Symbol

`F2` - Get Definition

`Shift + F2` - Get all References

`Ctrl + Tab` - File History

`Ctrl + I` - Select Line

`Ctrl + Shift + M` - Open Problems

`Ctrl + Shift + U` - Open Output

`Ctrl + Shift + L` - Select All Occurrences

`Ctrl + G` - Go to Line

`Ctrl + Page Down/Up` - Focus Next Editor Group

`Ctrl + tilde` - Terminal

`Ctrl + Shift + F` - Search all Files in Project

`Ctrl + K, F` - Closes working dir.

`Ctrl + K, Ctrl + O` - Open working dir.

`Alt + F12` - Peak definition.



## Windows Terminal

`Ctrl + Shift + W` - Close Tab/Pane

`Ctrl + T` - New Tab

`Shift + Alt + [-, +]` - New *pane* split horizontal and vertical, respectively 

`Alt + [Left, Right, Up, Down]` - Shift pane focus




## Linux

### Admin

`lastlog` - Shows a list of all accounts and their date of login.

`apt-cache search <string>` - With Debian systems, searches packages for pattern.

`apt-get update && apt-get upgrade` - Updates package-list THEN installs new packages.

`chown -[R recursive,] user:group <file>` - Changes ownership of directory/file.

`chgrp` - Changes group of directory/file.

`chmod [u,g,o,a] [+,-][r,w] <file>` - Changes permissions of directory/file.

`mount -[l=List, a=Reload]` - Mount points from fstab file.

`lsblk` - List all devices and partitions.

`w` - Shows logged in users and what they are doing.

`last` - History of recent account logs.

`ifconfig` - Network interfaces.

`ln -s <target> <destination>` - Makes a symbolic link.

`ps` - Shows processes on machine.

`ps -eH | less` - Shows process by all accounts into a hierarchy.

`top` - Realtime process info.

`a2ensite, a2dissite` - Apache enable/disable sites config.

`apache2ctl -S` - Apache Service status w/ Virtual Hosts.

`a2enmod <mod>, a2dismod <mod>` - Apache enable/disenable mods.

`mkdir /mnt/ram && mount -t tmpfs tmpfs /mnt/ram -o size=8192M` - Creates a super fast ram disk.

`mkdir -p folder/{sub1,sub2}/{sub1,sub2,sub3}` - Quickly create directory structure.

`ssh -L 8000:127.0.0.1:80root@remoteserver.org -N` - Creates a tunnel from remote service on port 80 to local port 8000.

`disown -a && exit` - Disconnects all processes from current terminal and exits, leaving all processes started by that terminal to remain running.

`export ENVVAR="value"` - Defines an environment variable for current shell-env.

`sed 's/\([0-9]\{1,3\}\.\)\{3,3\}[0-9]\{1,3\}/x.x.x.x/g' in.txt > out.txt` - Remove all IPs from a file.

`source ~/.bashrc ` OR `. ~/.bashrc` OR `exec bash` - Reloads bashrc file.

`crontab -l` - List running cronjobs.

`crontah -e` - Edit current user's cronjobs.

`find / 2>/dev/null | grep -i "pattern"` - Find files & hide stderr output.

`scp -[i identityfile, ] <target> <user@host:/tmp/destination>` - Secure copy to/from remote host.

`iptables -L` - Firewall rules.

### Other

`cat` - Outputs contents of files.

`cat >> file` - Cat in append mode.

`mkdir` - Makes a directory.

`echo <variable>` - Outputs to stout.

`ssh user@host` - SSH to user on host.

`grep -[P=Regex, F=ignore_special_charatcers, r=recursive, i=ignorecase, n=line_number, c=count, v=inverse] <pattern> <path>` - Searching input for patterns.

`rm -[r=recursive, f=force]` - Removes file.

`tail -[f=realtime, n=lines, v=verbose] <path>` - Outputs last *n* lines of a file.

`tail -f <name> | grep <search_term>` - Pipes the live file to grep.

`watch tail <file>` - Another way to watch a file in real time.

`lnav <file> <file2> ...` - Better way to watch log files for extended periods. REQUIRES LNAV PACKAGE!

`locate <file>` - Searches index-db for files.

`sudo updatedb` - Updates index-db for `locate`.

`find <path> -[type f=file, d=dir] -[iname=ignore_case] -[time <days_since_accessed>]<pattern> -print` - Find Files.

`find / -size -5M -and -size +2M` - Finds files in root larger than 2MB and smaller than 5MB.

`find | grep -[i=ignorecase] <string>` - Find files *hacky*.

`find / -[name=filename, iname=filenameIGNORECASE] "*.s*"` - Finds all files in root that have an s in its extension.

`find . -path "*"` `find . -type d` - Finds all directories in pwd.

`sudo !!` - Run last used command as root.

`fc` - Opens last command ran in editor to make changes more easily, then runs once saved.

`yes | command` - Pipes yes input to command or script.

`> filename` - Empties a file without deleting it.

`export NEWENVVAR="new env variable"` - Creates a new environment variable

`curl [-I = headers,] <url>` - Curl

`history | grep <filter>` - Search bash history

### Terminal

`Shift + PageUp/Down` - Scroll lines in terminal.

`Ctrl + U` - Clears current line behind cursor.

`Ctrl + A` - Moves Cursor to Beginning of Line.

`Ctrl + E` - Moves to end of line.

`Ctrl + K`  - Clears Current Line in Front of Cursor.

`Ctrl + W` - Clears last word.

`Ctrl + X + E` - Opens an editor to type commands.

`Ctrl + R` - Live bash history search

### Important Files

`/etc/passwd` - User account information.

`/etc/shadow` - Secret user account information.

`/var/log/auth.log` - Authorization Log File.

`/var/log/apache/[access.log, error.log]` - Apache Logs.

`/etc/os-release` - Operating system information.

`/etc/environment` - Ubuntu environment file; update env vars.

### Misc

Add an alias to sudoers file -

```bash
sudo visudo
...
# Creates a user alias to be referenced later
User_Alias INSTALLERS = lee, zooey

# Gives all users in INSTALLERS access to apt-get with sudo
INSTALLERS	ALL=/usr/bin/apt-get
...
```

Bash script to test environment variables/directories/symbolic links

```bash
#!/bin/bash

# Test environment variable
if [ -z "$TEST_ENVVAR" ]; then
	echo "Environment variable doesn't exist!"
fi
# Inline
if [ -z "$TEST_ENVVAR" ]; then echo "Environment variable doesn't exist!"; fi

# Test if directory exists
if [ -d /path/to/dir ]; then echo "Found directory!"; fi

# Test for symbolic link
if [ -L /path/to/link ]; then echo "Found link!"; fi

# Test for file
if [ -e /path/to/file ]; then echo "Found file!"; fi

```

### Common Processes

```bash
	# List drives/partitions, then mount to see contents ##########
	
	# Show drives/partitions
	lslbk

	# Mount partition
	sudo mkdir /mnt/tmp && sudo mount /dev/sdX /mnt/tmp

	# See contents..
	ls -la /mnt/tmp
```



## Git

`git init` - Initializes git for the pwd; adds git files.

`git add [<file>, <file>, ...]` - Tracks new file(s).

`git rm --cached <file>` - Stops tracking file in repo, doesn't delete from filesystem.

`git status` - Shows state of current branch.

`git ls-files` - Show tracked files.

`git commit -[a=AllTracked, m=Message, ] --[ammend=Ammends previous commit, no-edit=Keeps commit message, reuse-message HEAD=Keeps commit msg from HEAD, ] <msg?>` - Makes a commit.

`git diff <file?>` - Shows changes.

`git log [--graph?]` - Shows log of commits.

`git log --all -- <filename>` - Searches through git history for file.

`git branch -[d=Delete, m=Rename] <branch> <newname>` - Shows branches.

`git checkout -[b=NewBranch] <branch>` - Changes current branch.

`git checkout -- <file>` - Resets a file to HEAD, ignoring local changes.

`git merge [--squash="Collaspe all commit in merging branch to single."] <branch>` - Merge branch into current.

`git mergetool` - See merge conflicts.

`git remote add origin <url>.git` - Adds remote origin to repo.

`git remote -v` - Shows your current remote origin/fetch urls.

`git reset [--hard=Ignores local changes, --soft=Keeps local changes]` - Resets all files to last commit.

`git push -u origin <branch>` - Sets the origin as the default for push calls, then pushes branch.

`git push origin --delete <branch>` - Deletes remote branch.

`git stash -[u=Untracked Files, ]` - Stash working dir.

`git stash list` - Lists all stash objects.

`git stash pop` - Pops the top-most stash entry to working dir and removes entry from stash list.

`git stash apply` - Pops the top-most, keep changes in stash.

`git stash save "desc."` - Saves working dir with name/desc.

`git stash drop stash@{0}` - Drops stash at index 0.

`git show --pretty="" --name-only <commit hash>` - Shows new files in commit.



### Examples



**Merge Conflicts**

```bash
# Checkout ours/theirs to solve merge conflicts
git checkout [--ours, --theirs] filename.c
git add filename.c
git pull origin master
```



**Rebase Git-flow**

```bash
git checkout master && git pull # update master first
git checkout feature-branch		# get on feature branch to rebase
git rebase master 				# rebase feature to master
# git mergetool 				# solve merge issues, if any
git rebase --continue 			# continue rebase after fixing merge issues
# git rebase --abort 			# discard rebase if needed
git push -f						# force-push to remote feature branch
```



**Git Add Patch-mode**

```bash
git add -p 	# enter patch-mode to select hunks of a file to be commited
# y - stage this hunk
# n - do not stage this hunk
# q - quit; do not stage this hunk nor any of the remaining ones
# a - stage this hunk and all that follow
# d - do not this hunk or any that follow
# s - split current hunk into more
# ? - help
```




## VIM

### Insert Mode

`:e file` - Opens file inside Vi.

`:q!` - Quits without saving.

`:q` - Quits.

`:wq` - Writes and quits.

### Command Mode

`dd` - Deletes a whole line.

`v` - Starts copy.

`y` - Copies character under cursor.

`yy` - "Yanks" the whole line.

`12yy` - "Yanks" 12 lines.

`x` - Cuts character under cursor.

`p` - Pastes "yanked."

`i` - Insert mode.

`a` - Insert at end of current line.

`Esc` - Return to command mode.

`u` - Undo last change.

`Ctrl + R` - Redo

`/text` - Search for 'text' after the cursor.

`n` - Find next occurrence after searching.

`gg` - Takes you to the top of the code.

`=` - Fixes indents.

`G` - Fixes indents throughout the whole file.

`G$` - End of file.

`gg dG` - Deletes all lines in file

`:f` - Show file info?

### Config

`:noh` - Clear last search highlight.

`:set number` - Enables line numbers

### Buffer



## Windows 10

### File Explorer

`F2` - Renames directory/file.

`Ctrl + X` - Cuts to clipboard.

`Ctrl + C` - Copies to clipboard.

`Ctrl + V` - Paste clipboard.

`Ctrl + Shift + V` - Format paste.

`Ctrl + Z` - Undo.

`Ctrl + Y` - Redo.

`Alt + ArrowKeys` - Backwards & Forwards through history.

### Desktop

`Win + ArrowKeys` - Moves window to different monitor.

`Win + DownKey` - Minimizes everything.

`Win + D` - Hides everything and brings you to Desktop.

`Win + P` - Changes multi-display layout.

`Win + L` - Locks computer.

`Win + Shift + S` - Snipping Screenshot.

`Win + X` - Admin Panel.

`Ctrl + Shift + Esc` - Task Manager.

`Alt + Tab` - I mean... come on.

`Win + Tab` - More fancy alt-tab.

`Shift + F3` - Changes case in Word...

`Win + A` - Opens Action Center.

`Win + I` - Opens Settings.

`Win + M` - Minimizes all Windows.

`Win + Home` - Minimizes all but Current Window.

`Win + ,` - Quick Desktop Peak.

### Virtual Desktops

`Win + Ctrl + D` - New Desktop.

`Win + Ctrl + ArrowKeys` - Switch Between Desktops.

`Win + Ctrl + F4` - Closes Current Virtual Desktop.



## Blender

### Camera

`MB3` - Orbiting the view; rotating the view.

`Shift + MB3` - Pan view.

`NumPad .` - Snap view to selected object.

`NumPad 1` - Side-on view of selected object.

`NumPad 7` - Top-down view of selected object.

`~ + View Selected` - Snap view to selected object.

`Alt + MB3 Click Drag` - Snap to nearest view angle.

### General Keys

`G` - Grab

`S` - Scale

`R` - Rotate

`G/S/R + Z` - Locks to Z axis only.

`G/S/R + Y` - Locks to Y axis only.

`G/S/R + X` - Locks to X axis only.

`G/S/R + MB3` : Snaps to axis currently near.

`~` - Cursor menu

`X` - Delete selected object.

`Shift + A` - Add Menu at cursor.

`F3` - Search for things; shortcuts, info, etc...

`Tab` - Switch from edit/model mode.

`O` - Toggle Proportional Editing

`Alt + Z` - X-Ray mode; see through object...

`Shift + D` - Duplicate Selection.

`P` - Selection to separate object.

`Ctrl + L` - Select all of connected vertices.

`N` - Bring up another property window.

`A` - Select entire mesh.

`Alt + A` - Deselect.

`Alt + LeftClick` - Select row of vertices.

`Ctrl + I` - Invert selection.

`H` - Hide selection.

`Alt + H` - Reveal Hidden.

`E` - Extrude; pulls a new face out of the mesh.

`J` - Join vertices.

### Tips

- To make a donut less perfect, goto **Edit Mode**, turn on proportional edit, click a point and then hit G. Now scroll down to narrow the area affected.

- To see smooth objects: in **Object Mode** right click object, with it selected, and click **shade smooth**.

- To smooth mesh: in **Property Window** goto wrench, click **Add Modifier**, then **Subdivision Surface**.

- Select part of an object, hit **Shift + D** to duplicate it, hit **ESC** or **right-click** to cancel movement. Then hit **P** and **Selection** to make it a separate object.

- Add a **Solidify** modifier to icing, increased outset to 1.0 and decreased thickness. Move this modifier above Sub Surface for smooth thickness.

- Add vertices to mesh: Select mesh, **right click** then **Subdivide**. Doubles vertices in mesh.

- Turn on snapping to face when moving things: top of the window click **Snap**, then **Face** and **Project Individual Elements**.

## Gimp2

`[ ]` - Increase/decrease size of brush.

#### Paths Tool

`Ctrl + Click` - Adds a new node.

`Ctrl + Drag` - Realign node?

`Shift + Ctrl + Click` - Delete node.

## Chrome

`Ctrl + W` - Closes Tab.

`Ctrl + T` - New Tab.

`Ctrl + Shift + T` - Reopens last tab.

`Ctrl + Tab` - Cycles tabs.

`Ctrl + Page Up/Down` - Cycles tab.

`Ctrl + L` - Focuses search box.

`Alt + ArrowKeys` - History: back & forward.


## MySQL

`DROP TABLE [IF EXISTS] <name>;`

`DROP VIEW [IF EXISTS] <name>;`

`mysql -u username -p database_name < database_name.sql`

`CREATE VIEW <v_name> AS ...`

`SHOW FULL TABLES;`

`SHOW CREATE VIEW <view>;`

`... WHERE <field> LIKE 'string%';`

`DELETE FROM <table> WHERE <condition...>;`

`INSERT INTO <table> (<column>...) VALUES (<value>...);`

`SELECT * FROM <table> WHERE <condition>;`


## Docker
`docker info`

`docker ps -a`

`docker-machine start`

`docker-machine env default`

`docker container ls`

`docker container`

`docker container stop`

`docker container prune`

`docker system prune`

`docker create -v /var/lib/mysql --name mysqldata mysql:5.7` - Creates a data volume with the mysql image

`docker run --name dev-container -volumes-from mysqldata -e MYSQL_ROOT_PASSWORD=root -p 3307:3306 base-image:latest`

`docker run -it --rm --name container-name --volumes-from mysqldatadb -e MYSQL_ROOT_PASSWORD=root -p 3306:3306 -p 80:80 base-image:latest`

`docker run --rm -it -p 80:80 -p 3306:3306 dev-image:latest`

`docker run -it --rm -v $(pwd):/var/www/html base-image:latest`

`docker build -t base-image:latest .` - Finds a dockerfile in the localdir and builds the image and tags it with base-image:latest

`docker build -t image_name:tag --build-arg arg_name=arg_value .` - Builds an image with build-time environment variables

`docker images`

`docker volume ls`

`docker run -e "env_var_name=value" <image>` - Runs a container with supplied environment variable

`docker exec -it <container-name> /bin/bash` - Attack to running container; run bash

`docker stats` - Container resource usage information


## PHP

`php -S localhost:8080` - Built-in PHP dev web-server

`php -S localhost:8080 -c /etc/php/7.2/apache2/php.ini ` - Built-in PHP web-server with specific ini file.

```php
// PHP Class Auto-loader
spl_autoload_register(function ($class) {
	include "path" . $class . ".class.php";
});
```

```php
// PHP Convert Errors to Exceptions
set_error_handler(function($errorNumber, $errorMessage, $errorFile, $errorLine) {
    throw new \ErrorException($errorMessage, 0, $errorNumber, $errorFile, $errorLine);
});
```

```php
// PHP Register Shut-down Function - Handle Errors
register_shutdown_function(function() {
    $errorData = error_get_last();
    if (is_array($errorData)) {
        ob_end_clean();
        echo 'Error occured! - ' . $errorData['message'];
    }
});
```

