Download Link: https://assignmentchef.com/product/solved-comp9044-lab-5
<br>
Before the lab you should re-read the relevant lecture slides and their accompanying examples.

Create a new directory for this lab called lab05, change to this directory, and fetch the provided code for this week by running these commands:

$ <strong>mkdir lab05</strong>

$ <strong>cd lab05</strong>

$ <strong>2041 fetch lab05</strong>

Or, if you’re not working on CSE, you can download the provided code as a <a href="https://cgi.cse.unsw.edu.au/~cs2041/20T2/lab/05/provided.zip">zip</a> <a href="https://cgi.cse.unsw.edu.au/~cs2041/20T2/lab/05/provided.zip">file</a> or a <a href="https://cgi.cse.unsw.edu.au/~cs2041/20T2/lab/05/provided.tar">tar</a> <a href="https://cgi.cse.unsw.edu.au/~cs2041/20T2/lab/05/provided.tar">file</a>.

Write a Shell program, backup.sh which takes 1 argument, the name of a file.

Your program should create a backup copy of this file.

If the file is named example.txt the backup should be called .example.txt.0 but you should not overwrite any previous backup copies.

So if .example.txt.0 exists, the backup copy should be called .example.txt.1 and if .example.txt.1 also exists it should be called .example.txt.2 and so on.

For example:

$ <strong>seq 1 3 &gt;n.txt</strong>

$ <strong>cat n.txt</strong>

1

2

3

$ <strong>backup.sh n.txt</strong>

Backup of ‘n.txt’ saved as ‘.n.txt.0’

$ <strong>cat .n.txt.0</strong>

1

2

3

$ <strong>backup.sh n.txt</strong>

Backup of ‘n.txt’ saved as ‘.n.txt.1’ $ <strong>backup.sh n.txt</strong>

Backup of ‘n.txt’ saved as ‘.n.txt.2’ $ <strong>backup.sh n.txt</strong>

Backup of ‘n.txt’ saved as ‘.n.txt.3’

$ <strong>ls .n.txt.*</strong>

.n.txt.0

.n.txt.1

.n.txt.2

Your answer must be Shell. You can not use other languages such as Perl, Python or C.

When you think your program is working, you can use autotest to run some simple automated tests:

$ <strong>2041 autotest shell_backup</strong>

When you are finished working on this exercise, you must submit your work by running give:

$ <strong>give cs2041 lab05_shell_backup backup.sh</strong>

before Tuesday 14 July 18 00 to obtain the marks for this lab exercise.

Rewrite your shell script from the last exercise as a Perl program, backup.pl which takes 1 argument, the name of a file.

Your program should create a backup copy of this file.

If the file is named example.txt the backup should be called .example.txt.0 but you should not overwrite any previous backup copies.

So if .example.txt.0 exists, the backup copy should be called .example.txt.1 and if .example.txt.1 also exists it should be called .example.txt.2 and so on.

For example:

$ <strong>seq 1 3 &gt;n.txt</strong>

$ <strong>cat n.txt</strong>

1

2

3

$ <strong>backup.pl n.txt</strong>

Backup of ‘n.txt’ saved as ‘.n.txt.0’

$ <strong>cat .n.txt.0</strong>

1

2

3

$ <strong>backup.pl n.txt</strong>

Backup of ‘n.txt’ saved as ‘.n.txt.1’ $ <strong>backup.pl n.txt</strong>

Backup of ‘n.txt’ saved as ‘.n.txt.2’ $ <strong>backup.pl n.txt</strong>

Backup of ‘n.txt’ saved as ‘.n.txt.3’

$ <strong>ls .n.txt.*</strong>

.n.txt.0

.n.txt.1

.n.txt.2

Your answer must be Perl only. You can not use other languages such as Shell, Python or C.

You may not run external programs, e.g. via system or backquotes. for example, you can’t run <sub>cp</sub>.

No error checking is necessary.

When you think your program is working, you can use autotest to run some simple automated tests:

$ <strong>2041 autotest perl_backup</strong>

When you are finished working on this exercise, you must submit your work by running give:

$ <strong>give cs2041 lab05_perl_backup backup.pl</strong>

before Tuesday 14 July 18 00 to obtain the marks for this lab exercise.

Write Shell scripts snapshot-save.sh &amp; snapshot-load.sh which saves &amp; restore backups of all the files in the current directory.

These scripts should be in Posix-compatible Shell, use:

#!/bin/dash

<h1>snapshot-save.sh</h1>

If snapshot-save.sh should save copies of all files in the current directory.

snapshot-save.sh should first create a directory named .snapshot.0 to store the backup copies of the files.

But if .snapshot.0 already exists, the backup directory should be called .snapshot.1 and if .snapshot.1 also exists it should be called .snapshot.2 and so on. snapshot-save.sh should ignore files with names starting with .

snapshot-save.sh should also ignore itself and snapshot-load.sh (not backup snapshot-save.sh and snapshot-load.sh). snapshot-load.sh <em>n</em>

If snapshot-load.sh is called with a first argument of <em>n</em> it should restore (copy back) the files from snapshot .snapshot.<em>n</em>.

Before doing this it should copy the current version of all files in a new .snapshot directory, (hint run snapshot-save.sh)

This is to make sure the user doesn’t accidentally lose some work when restoring files. It is always done even if the user wouldn’t lose work.

<h1>Examples</h1>

<table width="961">

 <tbody>

  <tr>

   <td width="961">$ <strong>ls .snapshot.*/*</strong> ls: cannot access .snapshot.*/*: No such file or directory$ <strong>echo hello &gt;a.txt</strong>$ <strong>snapshot-save.sh</strong>Creating snapshot 0$ <strong>ls .snapshot.*/*</strong>.snapshot.0/a.txt $ <strong>echo word &gt;a.txt</strong>$ <strong>snapshot-load.sh 0</strong> Creating snapshot 1Restoring snapshot 0$ <strong>ls .snapshot.*/*</strong>.snapshot.0/a.txt.snapshot.1/a.txt $ <strong>cat a.txt</strong> hello</td>

  </tr>

 </tbody>

</table>

and

$ <strong>echo hello0 &gt;a.txt</strong>

$ <strong>echo world0 &gt;b.txt </strong>$ <strong>snapshot-save.sh</strong>

Creating snapshot 0 $ <strong>echo hello1 &gt;a.txt</strong>

$ <strong>echo world1 &gt;b.txt </strong>$ <strong>snapshot-save.sh</strong>

Creating snapshot 1 $ <strong>echo hello2 &gt;a.txt</strong>

$ <strong>echo world2 &gt;b.txt</strong>

$ <strong>ls .snapshot.*/*</strong>

.snapshot.0/a.txt

.snapshot.0/b.txt

.snapshot.1/a.txt

.snapshot.1/b.txt

$ <strong>snapshot-load.sh 0</strong> Creating snapshot 2

Restoring snapshot 0 $ <strong>grep . ?.txt</strong>

a.txt:hello0

b.txt:world0

Your answer must be Posix-compatible Shell only. You can not use Bash ,Perl, Python or C.

Autotest and automarking will run your scripts with a current working directory different to the directory containing the script. The directory containing your submission will be in $PATH.

This means ./snapshot-save.sh run from snapshot-load.sh, but running snapshot-save.sh will succeed.

No error checking is necessary.

When you think your program is working, you can use autotest to run some simple automated tests:

$ <strong>2041 autotest shell_snapshot</strong>

When you are finished working on this exercise, you must submit your work by running give:

$ <strong>give cs2041 lab05_shell_snapshot snapshot-save.sh snapshot-load.sh</strong>

before Tuesday 14 July 18 00 to obtain the marks for this lab exercise.

Write a Perl program, snapshot.pl which saves or restores backups of all the files in the current directory.

snapshot.pl will be called with a first argument of either load or save. snapshot.pl save

If snapshot.pl is called with a first argument of save it should save copies of all files in the current directory. snapshot.pl should first create a directory named .snapshot.0 to store the backup copies of the files.

But if .snapshot.0 already exists, the backup directory should be called .snapshot.1 and if .snapshot.1 also exists it should be called .snapshot.2 and so on. snapshot.pl should ignore files with names starting with .

snapshot.pl should also ignore itself (not backup snapshot.pl). Hint: Perl’s glob and mkdir functions are useful. snapshot.pl load <em>n</em>

If snapshot.pl is called with a first argument of load and a second argument of <em>n</em> it should restore (copy back) the files from snapshot .snapshot.<em>n</em>.

Before doing this it should copy the current version of all files in a new .snapshot directory, in other words do the same as a save operation.

This is to make sure the user doesn’t accidentally lose some work when restoring files. It is always done even if the user wouldn’t lose work.

<h1>Examples</h1>

<table width="961">

 <tbody>

  <tr>

   <td width="961">$ <strong>ls .snapshot.*/*</strong> ls: cannot access .snapshot.*/*: No such file or directory$ <strong>echo hello &gt;a.txt</strong>$ <strong>snapshot.pl save</strong>Creating snapshot 0$ <strong>ls .snapshot.*/*</strong>.snapshot.0/a.txt $ <strong>echo word &gt;a.txt</strong>$ <strong>snapshot.pl load 0</strong> Creating snapshot 1Restoring snapshot 0$ <strong>ls .snapshot.*/*</strong>.snapshot.0/a.txt.snapshot.1/a.txt $ <strong>cat a.txt</strong> hello</td>

  </tr>

 </tbody>

</table>

and

$ <strong>echo hello0 &gt;a.txt</strong>

$ <strong>echo world0 &gt;b.txt </strong>$ <strong>snapshot.pl save</strong>

Creating snapshot 0 $ <strong>echo hello1 &gt;a.txt</strong>

$ <strong>echo world1 &gt;b.txt </strong>$ <strong>snapshot.pl save</strong>

Creating snapshot 1 $ <strong>echo hello2 &gt;a.txt</strong>

$ <strong>echo world2 &gt;b.txt</strong>

$ <strong>ls .snapshot.*/*</strong>

.snapshot.0/a.txt

.snapshot.0/b.txt

.snapshot.1/a.txt

.snapshot.1/b.txt

$ <strong>snapshot.pl load 0</strong> Creating snapshot 2

Restoring snapshot 0 $ <strong>grep . ?.txt</strong>

a.txt:hello0

b.txt:world0

Your answer must be Perl only. You can not use other languages such as Shell, Python or C.

You may not run external programs, e.g. via system or backquotes. for example, you can’t run <sub>cp</sub>.

No error checking is necessary.

When you think your program is working, you can use autotest to run some simple automated tests:

$ <strong>2041 autotest perl_snapshot</strong>

When you are finished working on this exercise, you must submit your work by running give:

$ <strong>give cs2041 lab05_perl_snapshot snapshot.pl</strong>

before Tuesday 14 July 18 00 to obtain the marks for this lab exercise.

Write a Perl program perl_print.pl which is given a single argument. It should output a Perl program which when run, prints this string. For example:

$ <strong>./perl_print.pl ‘Perl that prints Perl – yay’ |perl</strong> Perl that prints Perl – yay

You can assume the string contains only ASCII characters. You can not make other assumptions about the characters in the string.

When you think your program is working, you can use autotest to run some simple automated tests:

$ <strong>2041 autotest perl_print</strong>

When you are finished working on this exercise, you must submit your work by running give:

$ <strong>give cs2041 lab05_perl_print perl_print.pl</strong>

before Tuesday 14 July 18 00 to obtain the marks for this lab exercise.

When you are finished each exercises make sure you submit your work by running give.

You can run give multiple times. Only your last submission will be marked.

Don’t submit any exercises you haven’t attempted.

If you are working at home, you may find it more convenient to upload your work via <a href="https://cgi.cse.unsw.edu.au/~give/Student/give.php">g</a><a href="https://cgi.cse.unsw.edu.au/~give/Student/give.php">ive</a><a href="https://cgi.cse.unsw.edu.au/~give/Student/give.php">‘</a><a href="https://cgi.cse.unsw.edu.au/~give/Student/give.php">s</a> <a href="https://cgi.cse.unsw.edu.au/~give/Student/give.php">web</a> <a href="https://cgi.cse.unsw.edu.au/~give/Student/give.php">interface</a><a href="https://cgi.cse.unsw.edu.au/~give/Student/give.php">.</a>

Remember you have until Tuesday 14 July 18 00 to submit your work.

You cannot obtain marks by e-mailing your code to tutors or lecturers.

You check the files you have submitted <a href="https://cgi.cse.unsw.edu.au/~cs2041/20T2/student/">here</a>.

Automarking will be run by the lecturer several days after the submission deadline, using test cases different to those autotest runs for you. (Hint: do your own testing as well as running autotest.)

<a href="https://cgi.cse.unsw.edu.au/~give/Student/sturec.php">After</a> <a href="https://cgi.cse.unsw.edu.au/~give/Student/sturec.php">automarking</a> <a href="https://cgi.cse.unsw.edu.au/~give/Student/sturec.php">is</a> <a href="https://cgi.cse.unsw.edu.au/~give/Student/sturec.php">run</a> <a href="https://cgi.cse.unsw.edu.au/~give/Student/sturec.php">by</a> <a href="https://cgi.cse.unsw.edu.au/~give/Student/sturec.php">the</a> <a href="https://cgi.cse.unsw.edu.au/~give/Student/sturec.php">lecturer</a> <a href="https://cgi.cse.unsw.edu.au/~give/Student/sturec.php">you</a> <a href="https://cgi.cse.unsw.edu.au/~give/Student/sturec.php">can</a> <a href="https://cgi.cse.unsw.edu.au/~give/Student/sturec.php">view</a> <a href="https://cgi.cse.unsw.edu.au/~give/Student/sturec.php">y</a><a href="https://cgi.cse.unsw.edu.au/~give/Student/sturec.php">our</a> <a href="https://cgi.cse.unsw.edu.au/~give/Student/sturec.php">results</a> <a href="https://cgi.cse.unsw.edu.au/~give/Student/sturec.php">here</a><a href="https://cgi.cse.unsw.edu.au/~give/Student/sturec.php">.</a> <a href="https://cgi.cse.unsw.edu.au/~give/Student/sturec.php">The</a> <a href="https://cgi.cse.unsw.edu.au/~give/Student/sturec.php">resulting</a> <a href="https://cgi.cse.unsw.edu.au/~give/Student/sturec.php">mark</a> <a href="https://cgi.cse.unsw.edu.au/~give/Student/sturec.php">will</a> <a href="https://cgi.cse.unsw.edu.au/~give/Student/sturec.php">also</a> <a href="https://cgi.cse.unsw.edu.au/~give/Student/sturec.php">be</a> <a href="https://cgi.cse.unsw.edu.au/~give/Student/sturec.php">available</a> <a href="https://cgi.cse.unsw.edu.au/~give/Student/sturec.php">via</a> <a href="https://cgi.cse.unsw.edu.au/~give/Student/sturec.php">g</a><a href="https://cgi.cse.unsw.edu.au/~give/Student/sturec.php">ive</a><a href="https://cgi.cse.unsw.edu.au/~give/Student/sturec.php">‘</a><a href="https://cgi.cse.unsw.edu.au/~give/Student/sturec.php">s</a> <a href="https://cgi.cse.unsw.edu.au/~give/Student/sturec.php">web interface</a><a href="https://cgi.cse.unsw.edu.au/~give/Student/sturec.php">.</a>