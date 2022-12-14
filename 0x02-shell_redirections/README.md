0x02. Shell, I/O Redirections and filters

0. Hello World

Q--> Write a script that prints “Hello, World”, followed by a new line to the standard output.

A--> echo 'Hello, World'

1. Confused smiley

Q--> Write a script that displays a confused smiley "(Ôo)'.

A--> echo \"\(Ôo\)\'

Explanation: These 4 characters [ " ( ) ' ] must be escabed by \ (backslash) to prevent them from interpreted as a special character.

 2. Let's display a file
 
 Q--> Display the content of the /etc/passwd file.
 
 A--> cat /etc/passwd
 
 3. What about 2?
 
 Q--> Display the content of /etc/passwd and /etc/hosts

 A--> cat /etc/passwd /etc/hosts
 
 Explanation: We can display multiple files using cat by separating them by space.
 
 4. Last lines of a file
 
 Q--> Display the last 10 lines of /etc/passwd
 
 A--> tail -n 10 /etc/passwd
 
 Explanation: tail - is used to display the last lines of a file
              -n 10 - is an option which stand for 10 lines
            so (tail -n 10) will display the last 10 lines of a file
               /etc/passwd - is an argument which contains the file name

5. I'd prefer the first ones actually

Q--> Display the first 10 lines of /etc/passwd

A--> head -n 10 /etc/passwd

Explanation: head - is used to display the first lines of a file
             -n 10 - is an option which stand for 10 lines
           so (head -n 10) will display the first 10 lines of a file
             /etc/passwd - is an argument which contains the file name
             
6. Line #2

Q--> Write a script that displays the third line of the file iacta.
     The file iacta will be in the working directory
     
A--> head -n 3 iacta | tail -n 1

Explanation: Imagine we have these 6 lines in a file (iacta)
                 1.First
                 2.Second
                 3.Third
                 4.Fourth
                 5.Fifth
                 6.Sixth
             
             The command head -n 3 iacta will display the first 3 lines.which are:
                 1.First
                 2.Second
                 3.Third
              
              Then using a pipe character we can use this output to another input to get the desired output. In this case, tail -n 1.
              
              (tail -n 1) is a command that displays the last 1 line of a file. 
              So (head -n 3 iacta | tail -n 1) will display the last line of the first three lines of the file iacta:
                 3.Third
                 
7. It is a good file that cuts iron without making a noise

Q--> Write a shell script that creates a file named exactly \*\\'"Best School"\'\\*$\?\*\*\*\*\*:) containing the text Best School ending by a new line.


A--> echo "Best School" > '\*\\'\''"Best School"\'\''\\*$\?\*\*\*\*\*:)'

Explanation: we use (echo "Best School") to write "Best School" as a content in a file.
             Next we use ">" (The right arrow sign) to redirect the written content to the desired file. In this case, \*\\'"Best School"\'\\*$\?\*\*\*\*\*:).
             But, we can't simply redirect it by writing the file name.Because it contains special characters in it and they must not be interpreted.
             To do so, we use single quote and ignore all the special characters and we use backslash to ignore single quotes .Look at this comparision carefully: 
             
             
               \*\\         '      "    Best School  "\   '               \\*$\?\*\*\*\*\*:)
             ' \*\\  '     \'   '  "    Best School  "\   '\ '          '  \\*$\?\*\*\*\*\*:) '
             
8. Save current state of directory

Q--> Write a script that writes into the file ls_cwd_content the result of the command ls -la. If the file ls_cwd_content already exists, it should be overwritten. If the file ls_cwd_content does not exist, create it.

A--> ls -la > ls_cwd_content

Explanation: To redirect the output pf ls -la to ls_cwd_content, we simply use the right arrow sign (>).

9. Duplicate last line

Q--> Write a script that duplicates the last line of the file iacta

     The file iacta will be in the working directory
     
A--> tail -n -1 iacta >> iacta

Explanation: (tail -n -1 iacta) displays the last line of the file iacta
             >> - this sign used to append (In this case, repeat a line) at the end line of a file
             
10. No more javascrip

Q--> Write a script that deletes all the regular files (not the directories) with a .js extension that are present in the current directory and all its subfolders.

A--> find . -type f -name "*.js" -delete

Explanation: (find) - search for files 
              (.) - in the working directory
              (-type f) - tests regular files
              (-name "*.js*") - with the name .js
              (-delete) - is an action to delete files
              
11. Don't just count your directories, make your directories count

Q--> Write a script that counts the number of directories and sub-directories in the current directory.

    The current and parent directories should not be taken into account
Hidden directories should be counted

A--> find . -type d -not -path . | wc -l

Explanation: (find) - search for files
              (.) - in the working directory
              (-type d) - directory
              (-not -path .) - do not include the current working directory
              (|) - pipe
              (wc -l) - print the newline counts
              
12. What’s new

Q--> Create a script that displays the 10 newest files in the current directory.

     Requirements:
                  One file per line
                  Sorted from the newest to the oldest
 
 A--> ls -t . | head
 
 Explanation: (ls -t) - list files sort by newest first
              (.) - in the working directory
              (|) - pipeline
              (head) - displays the first 10 lines of a file (by default)
              
13. Being unique is better than being perfect

Q--> Create a script that takes a list of words as input and prints only words that appear exactly once.

           Input format: One line, one word
           Output format: One line, one word
           Words should be sorted
A--> sort | uniq -u

14. It must be in that file

Q--> Display lines containing the pattern “root” from the file /etc/passwd

A--> egrep "root" /etc/passwd

Explain: egrep = grep -e = search for extended regular expressions

15. Count that word

Q--> Display the number of lines that contain the pattern “bin” in the file /etc/passwd

A--> grep "bin" /etc/passwd | wc -l

16. What's next?

Q--> Display lines containing the pattern “root” and 3 lines after them in the file /etc/passwd.

A--> egrep -A 3 "root" /etc/passwd

Explanation: (-A) - is a grep context line control to print number lines of trailing context after matching.

17. I hate bins

Q--> Display all the lines in the file /etc/passwd that do not contain the pattern “bin”.

A--> cat /etc/passwd | grep -v "bin"

Explanation: (-v) - non-matching lines (Invert the sense of matching)

18. Letters only please

Q--> Display all lines of the file /etc/ssh/sshd_config starting with a letter.

A--> egrep ^[[:alpha:]] /etc/ssh/sshd_config

Explanation: (^(caret)) - indicates the beginning of the line.

19. A to Z

Q--> Replace all characters A and c from input to Z and e respectively.

A--> tr 'Ac' 'Ze'

Explanation: (tr) - translate or delete characters

20. Without C, you would live in hiago

Q--> Create a script that removes all letters c and C from input.

A--> tr -d cC

Explanation: (tr -d) - remove characters

21. esreveR

Q--> Write a script that reverse its input.

A--> rev

22. Write a script that displays all users and their home directories, sorted by users.

Q--> Write a script that displays all users and their home directories, sorted by users.

     Based on the the /etc/passwd file

A--> cut -d ':' -f 1,6 /etc/passwd | sort

Explanation: (cut) - print selected parts of lines 
             (-d) - delimeter (marks the beginning or end of a unit of data.) 
             (:) - separate values in paths
             (-f 1,6) - select only these fields (1 = login name, 6 = user home directory)
               
              
              








