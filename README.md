# FOSS — Arch Linux (GNU/Linux) — POSIX Compliant — Cheat Sheets

## Command Nomenclature

```
 #    # Comment line.
 >    # Command shell.
[ ]   # Element is optional.
{|}   # Set of possible elements to choose from.
 |    # "or" separator between multiple elements.
(,)   # Group of possible elements.
...   # Preceding element can be repeated multiple times.
< >   # User-defined element, variable or value.
~ ~   # Keystroke command.
```

### Examples

```
> <command> [-v]                     # The -v flag is optional.
> <command> [--flag=elmA|elmB]       # Choose elmA or elmB, or omit the flag entirely.
> <command> --flag={elmA|elmB}       # Specify either elmA or elmB.
> <command> -(elmA,elmB,elmC)        # Specify a combination of elmA, elmB, elmC.
                                     # e.g. > <command> -ac
> <command> <elm>...                 # Provide one or multiple of <elm>.
> <command> [<elm>...]               # Provide zero, one or multiple of <elm>.
```

## Text File Nomenclature

```
       [<file>]             # The <file> being referred to.
       | <text.1>           # Text line <text.1> inside <file>.
 <nr.1>| <text.2>           # Text line <text.2> inside <file> at line number <nr.1>.
<nr.2>?| <text.3>           # Text line <text.3> inside <file> near line number <nr.2>.
```

## Cheat Sheet Topics

* [Arch Linux — Cheat Sheet](ArchLinuxCheatSheet.md)
* [Build — Cheat Sheet ](BuildCheatSheet.md)
* [Git — Cheat Sheet](GitCheatSheet.md)
<!-- * Julia — Cheat Sheet -->
<!-- * Markdown — Cheat Sheet -->
<!-- * Python & Cython — Cheat Sheet -->
<!-- * Regular Expressions (RegEx — BRE, ERE, PCRE) — Cheat Sheet -->
<!-- * Shells & Shell Scripts — Cheat Sheet -->
<!-- * VIM — Cheat Sheet -->

## Files, Directories & Filesystem Commands

```
> pwd                        # Output current working directory.
> ls                         # List files and directories.
> ls -R                      # List files and directories recursively.
> ls -l                      # Long listing format.
> ls -a                      # List all, including hidden entries starting with "."
> ls -lh                     # Long listing format, with human-readable file sizes.
> ls -lah                    # Long listing format, output all with human-readable file sizes.
> ls <*.ext>...              # List files matching <*.ext> or matching multiple <*.ext> (globing).
> cd <dir>                   # Change directory to <dir>.
  # e.g. > cd /              # Change to root directory.
> cd ~                       # Change to home directory.
> cd -                       # Change to previous directory.
> cd ..                      # Change to parent directory.
> rm <file>...               # Remove <file> or multiple <file>.
> rm <*.ext>                 # Remove files matching <*.ext> (globing).
> shopt -s extglob;          # Use extended globing to remove all files in current directory except <file.1> and <file.2>.
  rm !(<file.1>|<file.2>)    # !(|) — Taken literally.
> rm -r <dir>                # Remove <dir> and sub-directories recursively (use with care).
> rm -rf <dir>               # Force remove directory <dir> and sub-directories recursively (use with care).
> mv <src> <dest>            # Move <src> file(s) or directory to <dest>.
> cp <src> <dest>            # Copy <src> file(s) or directory to <dest>.
> cp -R <src> <dest>         # Copy <src> file(s) or directory and sub-directories recursively to <dest>.
> cp -p <src> <dest>         # Copy <src> file(s) or directory to <dest>, preserving permissions and timestamps.
> mkdir <dir>...             # Make directory <dir> or multiple <dir>.
> mkdir -p <p.dir>/<dir>     # Make directory <dir> and parent directory <p.dir> or multiple as needed.
> rmdir <dir>...             # Remove directory <dir> or multiple <dir>, when empty.
> rmdir -p <p.dir>/<dir>     # Remove directory <dir> and parent directory <p.dir> or multiple, when empty.
> chown [<user>][:<group>] <file>...         # Change <file> or multiple <file> ownership to <user> and <group>.
> chwon -R [<user>][:<group>] <path>...      # Change recursively all files in <path> or multiple <path>.
> chmod (u,g,o)(=,+,-)(r,w,x) <file>...      # Change access rights on <file> or multiple <file>.
                                             # (u=user, g=group, o=others)(+=add, -=remove, ==define)(r=read, w=write, x=execute)  
  # e.g. > chmod ug+x <file>; chmod -w <file>
> chmod -R (u,g,o)(=,+,-)(r,w,x) <path>...   # Change access rights recursively in <path> or multiple <path>.
> chmod 000 <file>...         # Revoke all access rights on <file> or multiple <file>.
> chmod 777 <file>...         # Provide full access rights on <file> or multiple <file>.
> ln <src> <link>             # Create hard link of <src> at <link>, with <src> and <link> pointing to same inode in filesystem (disk).
                              # Only removing both <src> and <link> results in removing the inode in filesystem.
> ln -s <src> <link>          # Create symbolic link of <src> at <link>, with symbolic link lost (pointing nowhere) when inode is removed.
> touch <file>...             # Change <file> or multiple <file> timestamp(s), create empty <file> or multiple empty <file> if none existing.
> shred <file>...             # Overwrite <file> or multiple <file> repeatedly shredding and deleting content.
> whereis <file>...           # Find <file> or multiple <file> location in filesystem.
> dirname <file.path>         # Extract directory path from file location <file.path>.
> basename <file.path>        # Extract filename from full path <file.path>.
> df                          # Report disk space free.
> df -h                       # Report disk space free in human-readable sizes.
> df <file|path>...           # Report disk space free on which (multiple) <file> or (multiple) <path> reside(s).
> du                          # Estimate disk space usage of directories recursively from current directory.
> du -h                       # Estimate disk space usage of directories recursively from current directory in human-readable file sizes.
> du <file|path>...           # Estimate disk space usage of (multiple) <file> or (multiple) <path> containing files.
> lsof                        # List open files.
> lsof -p <pid>               # List open files for <pid> process.
> blkid <dev>...              # Report <dev> or multiple <dev> storage device(s) (block device(s)) attributes (e.g. UUID).
> lsblk                       # List tree of storage devices (block devices) with mount-points.
> lsblk <dev>...              # List tree of <dev> or multiple <dev> storage device(s) (block device(s)) with mount-point(s).
> sync                        # Synchronise cached writes to persistent storage.
> findmnt                     # List tree of mount-points.
> mount                       # List current mount-points in filesystem.
> mount <part.dev> <dest>     # Mount partition device <part.dev> at directory/mount-point to <dest> in filesystem.
> umount <part.dev>           # Unmount device <part.dev>.
> umount <dest>               # Unmount mount-point <dest> in filesystem.
> fdisk -l [<dev>]...         # List partition table(s), optionally for disk <dev> or multiple disk <dev>.
> fdisk <dev>                 # Manipulate disk partition table for disk <dev>.
> fsck.ext4 <part.dev>        # Check ext4 file system at partition <part.dev> (not currently mounted).
> fsck.btrfs <part.dev>       # Check btrfs file system at partition <part.dev> (not currently mounted).
> mkfs.ext4 <part.dev>        # Create ext4 file system at partition <part.dev> (not currently mounted).
> mkswap <part.dev>           # Create a swap file system at partition <part.dev> (not currently mounted).
> dd if=<in.file> of=<out.file> bs=<block.size>      # Raw copy <in.file> to <out.file> with <block.size> at a time (use kB, K, MB, M).
  # e.g. > dd if=file.iso of=/dev/sda1 bs=10MB
  # e.g. > dd if=file.iso of=/dev/sda1 bs=10MB status=progress
> sfdisk -d <disk.dev>  >  <part.table.file>         # Write disk partition table at <disk.dev> to description in <part.table.file>.
> sfdisk <disk.dev>  <  <part.table.file>            # Write disk partition table description in <part.table.file> to disk partition table at <disk.dev>.
> partprobe <disk.dev>                               # Inform Linux kernel of changes to partition table at <disk.dev>.
> swapon <part.dev|swap.file>                        # Enable swap partition <part.dev> or swap file <swap.file>.
> swapoff <part.dev|swap.file>                       # Disable swap partition <part.dev> or swap file <swap.file>.
```

## File Content Commands

```
> cat <file>...                               # Output <file> or multiple <file> content.
> cat -n <file>...                            # Output <file> or multiple <file> content with line numbers.
> cat <file>... > <out.file>                  # Output <file> or multiple <file> content and write to <out.file>.
> cat <file>... >> <out.file>                 # Output <file> or multiple <file> content and append to <out.file>.
> cat > <out.file>                            # Take input from stdin (user) and write to <out.file> (~Ctrl+c~ or ~Ctrl+d~ to exit).
> cat <file>... | less                        # Output <file> or multiple <file> content, pipe to "less" (quit "less" with ~q~;
                                              # start search with ~/~<string|reg.exp>, next match ~n~, previous match ~N~).
> cat <file>... | tail                        # Output <file> or multiple <file> content, pipe to "tail" giving only tail of <file>.
> cat <file>... | head                        # Output <file> or multiple <file> content, pipe to "head" giving only head of <file>.
> cat <file> | sort | uniq | wc -l
  # Output <file>, pipe through "sort" sorting lines, then pipe through "uniq" finding unique lines,
  # then pipe through "wc -l" counting the number of unique lines. (e.g. use "sed", "cut", "join", "split").
> tac <file>...                               # Reverse output <file> or multiple <file> content.
> sort <file>...                              # Sort lines in <file> or multiple <file>.
> shuf <file>...                              # Randomly shuffle lines in <file> or multiple <file>.
> tail <file>...                              # Output tail of <file> or multiple <file>.
> tail -n <lines> <file>...                   # Output last <lines> of <file> or multiple <file>.
> tail -f <file>                              # Follow real-time updates to <file>.
> more <file>...                              # Browse content of <file> or multiple <file>.
> less <file>...                              # Browse content of <file> or multiple <file>.
> less -R <file>...                           # Browse content of <file> or multiple <file> in color.
> nl <file>...                                # Output <file> or multiple <file> numbering lines.
> cut -d<delimiter> -f<field.num> <file>...   # Cut from every line in <file> or multiple <file> the field numbered <field.num> using <delimiter>.
  # e.g. > cut -d: -f1  /etc/passwd           # Cut out usernames from "/etc/passwd".
  # e.g. > cut -dL -f1,3  /etc/passwd         # Cut out first en third field from "/etc/passwd".
> tr 'a-z' 'A-Z'  <  <file>                   # Translate lowercase to uppercase of content in <file> (stdin).
> hexdump <file>...                           # Output hexdump of <file> or multiple <file>.
> hexdump -C <file>...                        # Output hexdump with additional ACSII representation of <file> or multiple <file>.
> hexdump -C <file>... | less                 # Output hexdump with additional ASCII representation of <file> or multiple <file>, pipe to "less" (quit "less" with ~q~).
> sed -i "s/<reg.exp>/<replace>/" <file>...   # Match <reg.exp> once in <file> or multiple <file> and replace "in place" with <replace>.
> sed -i "s/<reg.exp>/<replace>/g" <file>...  # Match <reg.exp> repeatedly in every line in <file> and replace "in place" with <replace>.
> find <path> -name "<file>"                  # Search starting at <path> to locate <file> recursively.
> find <path> -name "*<.ext>"                 # Search starting at <path> to locate <.ext> (globing) recursively.
> find <path> -user <username>                # Search starting at <path> to locate files owned by <user.name>.
> find <path> -mtime -<days>                  # Search starting at <path> to locate files modified the last <days>.
  # e.g. > find ~ -mtime -7                   # Search home directory for files modified the last 7 days.
> grep -lir "<string|reg.exp>"                # Search files for matching <string|reg.exp> recursively.
> diff -u <file.old> <file.new>               # Output difference between <file.old> "---" and <file.new> "+++".
> diff -u <file.old> <file.new>  >  <file.patch>    # Write difference between <file.old> "---" and <file.new>. "+++" to patch file <file.patch>.
> patch <file> <file.patch>                         # Apply patch file <file.patch> to <file>.
```

## Archiving Commands

```
> tar -czf <tarball> <file>...                # Compress <file> or multiple <file> into .tar.gz (tarball). Full paths of files will be archived.
> tar -czf <tarball> -C <root.dir> .          # Compress all files inside <root.dir> into .tar.gz (tarball).
                                              # Full paths will not be archived; the root directory of the archive will be <root.dir>.
> tar -xzf <tarball> -C <root.dir>            # Extract .tar.gz (tarball) to directory <root.dir>, instead of current directory.
> tar -cJf <tarball> <file>...                # Compress <file> or multiple <file> into .tar.xz (tarball). Full paths of files will be archived.
> tar -cJf <tarball> -C <root.dir> .          # Compress all files inside <root.dir> into .tar.xz (tarball).
                                              # Full paths will not be archived; the root directory of the archive will be <root.dir>.
> tar -xJf <tarball> -C <root.dir>            # Extract .tar.xz (tarball) to directory <root.dir>, instead of current directory.
> tar --zstd -cf <tarball> - C <root.dir> .   # Compress all files inside <root.dir> into .tar.zst (tarball).
                                              # Full paths will not be archived; the root directory of the archive will be <root.dir>.
> tar --zstd -xf <tarball> -C <root.dir>      # Extract .tar.zst (tarball) to directory <root.dir>, instead of current directory.
> gzip <file>...                              # Compress <file> or multiple <file> individually, replaced by .gz compressed files.
> gunzip <file>.gz...                         # Extract <file>.gz or multiple <file>.gz, replacing .gz compressed files by uncompressed files.
```

## Cipher & Hash Commands

```
> md5sum <file>...                                # Generate MD5 message digest hash(es) of <file> or multiple <file>.
> sha512sum <file>...                             # Generate SHA512 message digest hash(es) of <file> or multiple <file>.
> gpg -c --cipher-algo aes <plaintext>            # Create AES encrypted file <plaintext>.gpg.
> gpg --output <plaintext> --decrypt <file>.gpg   # Decrypt AES encrypted file <file>.gpg, creating <plaintext>.
```

## User Commands

```
> whoami                                                      # Give my user name.
> w                                                           # Show who is logged in and what they are doing.
> su <user.name>                                              # Switch to other user with <user.name>.
> sudo <command>                                              # Execute <command> with "root" privileges.
> useradd -m -g <prim.group> [-G <sec.group.1>,<sec.group.2>,...] -d <home-dir> <user.name>    # Add new user manually.
  # e.g. > useradd -m -g users -G wheel -d /home/<username> <user.name>
> userdel <user.name>                                         # Delete user with <user.name>.
> userdel -r <user.name>                                      # Delete user with <user.name>, removing home directory.
> usermod -g <prim.group> <user.name>                         # Force a new primary group <prim.group> for user with <user.name>.
> usermod -G <sec.group.1>,<sec.group.2>,... <user.name>      # New list of secondary group(s) <sec.group>... for user with <user.name>.
> usermod -a -G <sec.group.1>,<sec.group.2>,... <user.name>   # Additionally append secondary group(s) <sec.group>... to defined
                                                              # secondary groups for user with <user.name>.
> usermod -r -G <sec.group.1>,<sec.group.2>,... <user.name>   # Remove secondary groups <sec.group>... from defined secondary groups for user with <user.name>.
> passwd <user.name>                                          # Set new password for user with <user.name>.
> passwd -l <user.name>                                       # Lock user with <user.name>.
> passwd -u <user.name>                                       # Unlock user with <user.name>.
> id                                                          # Show user IDs.
> id <user.name>                                              # Show user IDs for user with <user.name>.
> groups                                                      # Show groups for current user.
> groups <user.name>                                          # Show groups for user with <user.name>.
> groupdel <group.name>                                       # Delete group with <group.name>.
> pwck                                                        # Check password file integrity.
> grpck                                                       # Check group file integrity.
```

## General Commands & Keystrokes

```
> info                                             # GNU coreutils info.
> <command> --help                                 # Output help about command-line options for <command>.
> man <command>                                    # Manual page about <command>.
  # e.g. > man (sed, grep, tac, fdisk, man, mkfs.ext3, ssh, systemctl, journalctl, autoscan, autoconf, aclocal, automake, pacman, makepkg, &c.)
> man <section> <command>                          # Manual page about <command> under specific numbered <section>.
> clear                                            # Clear terminal screen.
> ~Ctrl+l~                                         # Clear terminal screen.
> ~Ctrl+d~                                         # End user input to running process (leave interactive shell).
> reset                                            # Reset terminal state.
                                                   # Historically certain commands could upset the terminal output; e.g. terminal characters (> cat <binary>).
> setfont <font.type> [-h<height>]                 # Set TTY <font.type>, with possible line <height>.
  # e.g. > setfont Lat2-Terminus16 -h15
> xrandr <...>                                     # Adjust size, orientation, reflection of X11 screens.
> xrandr --listproviders                           # Report on available X11 graphic drivers.
> mesg -n                                          # Disable wall messages.
> exit                                             # Exit shell.
> export <VAR>=<value>                             # Set shell variable <VAR> to <value>.
> unset <VAR>                                      # Unset shell variable <VAR>.
> set                                              # Report shell variables.
> alias <name>=<command>                           # Add alias <name> to refer to <command> — Bash Shell.
> unalias <name>                                   # Remove alias <name> — Bash Shell.
> alias                                            # Report shell aliases — Bash Shell.
> printenv                                         # Print all environment variables.
> echo "<string>"                                  # Output text <string>.
> echo $VAR                                        # Output $VAR shell variable content.
> printf "\e[<esc.code>;...m%s\e[0m" "<string>"    # Output ECMA-48 (ANSI) escape "\e[<esc.code>m" coded text <string>:
                                                   # 0=reset color and style.
                                                   # color: +30=normal fg., +40=normal bg., +90=bright fg., +100=bright bg. —
                                                   #        0=black, 1=red, 2=green, 3=yellow, 4=blue, 5=magenta, 6=cyan, 7=white.
                                                   # style: 1=bold, 2=dim, 3=italic, 4=underline, 5/6=blink, 7=inverse,
                                                   #        8=hidden, 9=strike-through.
  # e.g. > printf "\e[31;44;1;5mHello World\e0m"   # Output "Hello World" bold and blinking on a normal blue bg. with normal red fg.
> whereis <command>                                # Locate <command> and manual page for <command>.
> which <command>                                  # Give full path of <command>.
> date                                             # Give system date and time.
> watch -n <interval> "<command>"                  # Execute <command> repeatedly every <interval>.
  # e.g. > watch -n 1 "ps aux"                     # Execute "ps aux" every second.
> time <command>                                   # Measure execution time of <command>.
> vim [<file>]...                                  # Open Vim text editor, optional with <file> or multiple <file>.
> nano [<file>]...                                 # Open Nano text editor, optional with <file> or multiple <file>.
```

## Redirections & Piping

```
> <command>  >  <file>                         # Redirect stdout of <command> to <file>.
> <command>  >>  <file>                        # Redirect stdout of <command> and append to <file>.
< <command>  <  <file>                         # Redirect content <file> to stdin of <command>.
> <command.1>  |  <command.2>                  # Pipe stdout of <command.1> to stdin of <command.2>.
> <command>  2>  <file>                        # Redirect stderr to <file>.
> <command>  2>>  <file>                       # Redirect stderr and append to <file>.
> <command>  &>  <file>                        # Redirect both stdout and stderr to <file>.
> <command>  &>>  <file>                       # Redirect both stdout and stderr to append to <file>.
> <command>  2>&1  >  <file>                   # Redirect stderr to stdout, thus redirecting both streams of <command> to <file>.
> <command.1>  2>&1  |  <command.2>            # Redirect stderr to stdout, piping both streams of <command.1> to stdin of <command.2>.
> <command>  |  tee <file.1> <file.2>          # Redirect stdout of <command> to stdin of "tee", which redirects to both <file.1> and <file.2>.
> <command>  |  tee -a <file.1> <file.2>       # Redirect stdout of <command> to stdin of "tee",
                                               # which redirects and appends to both <file.1> and <file.2>.
> <command.1>  |  tee <file>  |  <command.2>   # Pipe stdout of <command.1> to stdin of <command.2>,
                                               # while also using "tee" to redirect stdout of <command.1> to <file>.
> <command>  &>  /dev/null                     # Redirect both stdout en stderr of <command> to "/dev/null" (i.e. redirection to a black-hole).
> <command>  <<  EOF                           # Take user input until "EOF" (end-of-file) is again written on a final single line,
                                               # redirect this user input to stdin of <command>.
                                               # EOF is often written out in shell scripts (heredoc) and can go by any other name as sweet (e.g. CONF, INPT, &c.)
> <command>  <<  EOF  >  <file>                # Redirect user input to stdin of <command>, redirect stdout of <command> to <file>.
                                               # e.g. > sort  <<  EOF  >  sorted.txt
 ```

## Process & Memory Commands

```
> ps aux                          # Output detailed information on running processes and PID information.
> ps -u <user.name>               # Output detailed information on running processes by <user.name> and PID information.
> ps aux | grep "<application>"   # Output detailed information on running processes and PID information, pipe through "grep" matching <application>.
> pidof <application>             # Get PIDs of processes matching <application>.
> kill -TERM <pid>                # Terminate application, with <pid> found in second column of "ps -aux" or through "pidof".
> kill -KILL <pid>                # Forcefully remove application with given <pid>.
> killall <application>           # Terminate all applications matching <application>.
  # e.g. > killall firefox
> killall -KILL <application>     # Forcefully remove all applications matching <application>.
> ~Ctrl+c~                        # Kill running process.
> ~Ctrl+z~                        # Break away from running process, forcing it to run in background.
> jobs                            # List running jobs in current shell.
> jobs -p                         # List PIDs of running jobs in current shell.
> fg <pid>|%<job id>              # Run job <pid>|%<job id> in foreground.
> bg <pid>|%<job id>              # Run job <pid>|%<job id> in background.
> <command> &                     # Start <command> in background.
> nice -n <priority> <command>    # Start <command> with given <priority>.
  # e.g. > nice -n 10 /usr/bin/bash
> renice <priority> <pid>         # Change <priority> of running <pid>.
> pstree                          # List process tree of system parent and child processes.
> pstree -A                       # List process tree of system parent and child processes, with ASCII character output.
> free [-h]                       # Show free and used memory, optionally in human-readable sizes.
> top                             # Show continuos process information (quit "top" with ~q~).
> cat /proc/cpuinfo               # Show detailed CPU information.
> cat /proc/meminfo               # Show detailed memory information.
```

## Kernel Commands

```
> uname                                   # Report general system information.
> uname -a                                # Report all system information.
> uname -r                                # Report kernel release.
> uptime                                  # Report how long system has been running.
> dmesg                                   # List kernel messages.
> dmesg | tail                            # List kernel messages, pipe through "tail" to only show latest kernel messages.
> lsusb                                   # List USB devices.
> lspci                                   # List PCI devices (on x86 architecture).
> lscpu                                   # List CPU architecture.
> strace <executable>                     # Trace system calls and signals occurring during execution of <executable>.
> strace -c <executable>                  # Trace and count system calls and signal occurring during execution of <executable>.
> lsmod                                   # List loaded Linux kernel modules.
                                          # (When a module being listed is not used, it does mean the module is loaded into the Linux kernel.)
> modprobe <module.name>                  # Load Linux kernel module (preferred over > insmod <module.file>).
                                          # Linux kernel modules are located "/lib/modules/$(uname -r)/").
                                          # During boot udev loads Linux kernel modules based on detected hardware (modalias) or
                                          # modules are statically loaded in "/etc/modules-load.d/" or
                                          # blacklisted in "/etc/modprobe.d/".
                                          # Check "dmesg" to determine problems (e.g. tainted kernel).
> modprobe -r <module.name>               # Remove Linux kernel module (preferred over > rmmod <module.file>).
> depmod -a                               # Scan for all Linux kernel modules in "/lib/modules/$(uname -r)/"; information stored for use with "modprobe".
> modinfo <module.name|module.file>       # Show information about Linux kernel module.
```

## systemd Commands

```
> systemctl daemon-reload                 # Reload systemd to apply changes made in service files "/etc/systemd/".
> systemctl enable <service>              # Enable systemd <service> for every boot.
> systemctl disable <service>             # Disable systemd <service> for every boot.
> systemctl mask <service>                # Mask systemd <service> which cannot otherwise be disabled.
> systemctl unmask <service>              # Unmask systemd <service> which cannot otherwise be disabled.
> systemctl start <service>               # Start systemd <service>.
> systemctl stop <service>                # Stop systemd <service>.
> systemctl status                        # Show tree view of systemd status.
> systemctl status "<service>*"           # Get status of systemd services with service-name starting with <service> (globing).
> systemctl --user start <service>        # Start systemd user <service>.
> systemctl --user stop <service>         # Stop systemd user <service>.
> systemctl list-unit-files [--state=enabled] ["<service>*"]    # List unit files, possibly those enabled [--state=enabled] and
                                                                # possibly service-name(s) starting with <service> (globing).
> systemctl poweroff [--no-wall]          # System shutdown, optionally without pesky wall message [--no-wall].
> systemctl reboot [--no-wall]            # System reboot, optionally without pesky wall message [--no-wall].
> journalctl                              # Show full systemd journal.
> journalctl -b                           # Show systemd journal since last boot.
> journalctl -b -1                        # Show systemd journal of previous boot.
> journalctl -b -p <level>                # Show systemd journal since last boot, with entries of chosen severity <level> as well as entries of higher-severity.
                                          # Choose <level> to be number or name (prev. Syslog severity levels):
                                          # 0-emerg, 1-alert, 2-crit, 3-err, 4-warning, 5-notice, 6-info, 7-debug.
> journalctl -b -p <level.1>..<level.2>   # Show systemd journal since last boot, with entries of severity between <level.1> and <level.2>; both can be of same value.
> journalctl -n <lines>                   # Show systemd journal limited to <lines> number of lines.
> loginctl                                # Control the systemd login manager, showing sessions.
> loginctl user-status [<user.name>...]   # Show tree view of one or more logged in users.
> loginctl session-status                 # Show tree view of one or more sessions.
> systemd-inhibit <command>               # Run <command> while sleep, shutdown, hibernation is not going to be triggered.
> systemd-inhibit --list                  # Show which process(es) inhibit(s) sleep, shutdown, hibernation.
> systemd-analyze critical-chain          # Show boot-sequence critical chain.
> systemd-analyze blame                   # Show time it took for services to initialise.
> varlinkctl                              # Introspect and monitor systemd Varlink communication (Point-to-point UNIX-socket IPC, passing human-readable JSON data).
> busctl                                  # Introspect and monitor systemd D-Bus communication (Publish-subscribe system-bus broker daemon IPC, passing binary data).

# coredumpctl Related Commands
> coredumpctl list [<executable|pid>]              # List all core dumps, with possible path to specific <executable> or running process <pid>.
> coredumpctl info [<pid>]                         # Show detailed information on core dump, possibly matching <pid>.
> coredumpctl dump <pid> --output=<dump.file>      # Write core dump to <dump.file>, possibly matching <pid>.
> coredumpctl debug <pid>                          # Invoke gdb debugger on core dump, possibly matching <pid>.
> gdb <executable> <dump.file>                     # Invoke gdb debugger on <executable> with core dump <dump.file>.
                                                   # Use gdb commands: "bt" (backtrace), "bt full", "list" (surrounding source-code), &c.

# Generate debug symbols — Arch Linux
[/etc/makepkg.conf]                                # Have "debug" option included (not "!debug"), to generate debug symbols
| OPTIONS=(... debug ...)                          # during "makepkg -rs" package compilation;
                                                   # "debugedit" package should be installed and useful to have "$DEBUGINFOD_URLS" defined.
                                                   # Debug symbols are compiled as a separate debug package to be installed with software package.
> objdump --syms <executable>                      # Check and show debug symbol table inside <executable>.
```

## Networking Commands

```
> ip addr                                   # Network information.
> ip route                                  # Show routing table.
> ip link                                   # Show network interfaces.
> ip link set dev <interface> up            # Bring network device <interface> up.
> ip link set dev <interface> down          # Bring network device <interface> down.
> ip addr add <ip-address>>/<netmask> [broadcast <b.ip-address>] dev <interface>    # Set manual IP addresses.
  # e.g. > ip addr add 192.168.1.1/24 broadcast 192.168.1.255 dev wpl3s0
> ss | less                                 # Dump all TCP/IP and UNIX-socket statistics, pipe through "less" to read all.
> rfkill list                               # List soft and hard blocks on wireless devices.
> ping <domain|ip-address>                  # Ping network at <domain> or <ip-address>.
> traceroute <domain|ip-address>            # Report the route packets trace to <domain> or <ip-address>.
> nslookup <domain|ip-address>              # DNS lookup of <domain> or reverse lookup of <ip-address>.
> nslookup -type=mx <domain>                # MX (mail exchange) DNS lookup of <domain>.
> curl <url>                                # Get response from server at <url>.
  # e.g. > curl -s 6.ipquail.com/ip         # Get silently the current outward facing IPv6 address through server response at "6.ipquail.com/ip".
> wget <url>...                             # Download files from internet at <url> or multiple <url>.
> ssh-keygen -t rsa -b 4096 -C "user_email@host.domain"   # Generate SSH public/private RSA-keys (optionally no passphrase).
> ssh-keygen -t rsa -b 4096 -C "user@host"                # Generate SSH public/private RSA-keys (optionally no passphrase).
> ssh-copy-id -i <key.pub> <user>@<host>                  # Securely copy SSH public-key <key.pub> to <user> at <host>, authorising future logins.
> ssh <user>@<host>                                       # Remote secure shell SSH login for <user> at <host>.
> scp [<user>@<s.host>:]<s.file|s.path> [<user>@<d.host>:]<d.file|d.path>
  # Secure copy <s.file|s.path> from [<user>@<s.host>] to <d.file|d.path> at [<user>@<d.host>].
> scp -r -p [<user>@<s.host>:]<s.file|s.path> [<user>@<d.host>:]<d.file|d.path>
  # Secure copy <s.file|s.path> from [<user>@<s.host>] to <d.file|d.path> at [<user>@<d.host>] recursively,
  # preserving file attributes (e.g. date/time).
> i2cdetect -y -r 1    # Detect connected I2C-chips on e.g. Raspberry PI or BeagleBone.
```

[![FOSS Cheat Sheet — License](https://img.shields.io/badge/LICENSE-CC0--1.0-blue?style=for-the-badge&logo=creativecommons&logoColor=white)](LICENSE.md)
