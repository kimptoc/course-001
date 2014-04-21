$ ls
foo       hello.sh  hello.txt

$ ls foo/*.txt
foo/bar.txt  foo/baz.txt  foo/quux.txt

$ ls -l
total 16
drwxr-xr-x+ 7 kimptoc  staff  238  2 Apr 21:27 foo
-rwxr-xr-x+ 1 kimptoc  staff   39  2 Apr 21:27 hello.sh
-rw-r--r--+ 1 kimptoc  staff   13  2 Apr 21:27 hello.txt

$ ls -a
.         ..        .secret   foo       hello.sh  hello.txt

$ ls -a -l
total 24
drwxr-xr-x+ 6 kimptoc  staff  204  2 Apr 21:27 .
drwxr-xr-x+ 7 kimptoc  staff  238  6 Apr 19:59 ..
-rw-r--r--+ 1 kimptoc  staff    9  2 Apr 21:27 .secret
drwxr-xr-x+ 7 kimptoc  staff  238  2 Apr 21:27 foo
-rwxr-xr-x+ 1 kimptoc  staff   39  2 Apr 21:27 hello.sh
-rw-r--r--+ 1 kimptoc  staff   13  2 Apr 21:27 hello.txt

$ ls -l foo/*.txt
-rw-r--r--+ 1 kimptoc  staff   8  2 Apr 21:27 foo/bar.txt
-rw-r--r--+ 1 kimptoc  staff   8  2 Apr 21:27 foo/baz.txt
-rw-r--r--+ 1 kimptoc  staff  10  2 Apr 21:27 foo/quux.txt

$ ls missingdir
ls: missingdir: No such file or directory

$ ls -Z
ls: illegal option -- Z
usage: ls [-ABCFGHLOPRSTUWabcdefghiklmnopqrstuwx1] [file ...]