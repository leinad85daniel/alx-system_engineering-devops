                ___---___ 0x01. Shell, Permissions___---___

Task-0
su betty: is a script that prints the effecitve username of the current user.

Task-1
whoami: is a script that prints the effective username of the current user.

Task-2
groups: is a script that prints all the groups the current user is part of.

Task-3
chown betty hello: is a script that changes the owner of the file hello to the user betty.

Task-4
touch hello: is a script that creates an empty file called hello.

Task-5
chmod u+x hello: is a script that adds execute permission to the owner of the file hello.

Task-6
chmod u+x,g+x,o+r hello: is a script that adds execute permissions to the owner and the group owner, and read permission to other users, to the file hello.

Task-7
chmod ugo+x hello: is a script that adds execution permission to the owner, the group owner and the other users, to the file hello.

Task-8
chmod 007 hello: is a script that sets the permission to the file as follows: 
        owner - no permission at whole
        Group - no permission at all
        Other users - all the permissions

Task-9
chmod 753 hello: is a script that sets the mode of the file hello to this:
        -rwxr-x-wx 1 julien jlien 23 sep 20 14:25 hello

Task-10
chmod --reference olleh hello: is a script that sets the mode of the file hello tha same as olleh's mode.

Task-11
chmod -R +111 */: is a script that adds execute permission to all subdirectories of the current directory for the owner, the group owner and other users. Regular files should not be changed.

Task-12
mkdir -m 751 my_dir: is a script that creates a directory called my_dir withh permissions 751 in the working directory.

Task-13
chgrp school hello: is a script that changes the group owner to school for the file hello.

Task-14
chown -R vincent:staff ./: is a script that changes the owner to vincent and the group owner to staff for all the files and directories in the working directory.

Task-15
chown -h vincent:staff _hello: is a script that changes the owner and the group owner of _hello to vincent and staff respectively:
      The file _hello is in the working directory
      The file _hello is a symbolic link

Task-16
chown --from=guillaume betty hello: is a script that changes the owner of the file hello to betty only if it is owned by user guillaume.

Task-17
telnet towel.blinkenlights.nl: is a script that will play StarWart Iv episode in the terminal.

                        ___---___THE END___---___
