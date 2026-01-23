Create a directory called ""my_folder"", navigate into it, and create a file named ""my_file.txt"" with some text. Then, create another file named ""another_file.txt"" with some text. Concatenate the content of ""another_file.txt"" to ""my_file.txt"" and display the updated content. Finally, list all files and directories in the current directory.
HEMAN@HEMANTH MINGW64 ~
$ mkdir my_folder

HEMAN@HEMANTH MINGW64 ~
$ cd my_folder

HEMAN@HEMANTH MINGW64 ~/my_folder
$ echo This is my file content > my_file.txt

HEMAN@HEMANTH MINGW64 ~/my_folder
$ cat my_file.txt
This is my file content

HEMAN@HEMANTH MINGW64 ~/my_folder
$ echo This is my file contents >another_file.txt

HEMAN@HEMANTH MINGW64 ~/my_folder
$ cat another_file.txt
This is my file contents

HEMAN@HEMANTH MINGW64 ~/my_folder
$ ls -lrth
total 2.0K
-rw-r--r-- 1 HEMAN 197609 24 Jan 23 17:56 my_file.txt
-rw-r--r-- 1 HEMAN 197609 25 Jan 23 17:58 another_file.txt

HEMAN@HEMANTH MINGW64 ~/my_folder
$ cat another_file.txt >> my_file.txt

HEMAN@HEMANTH MINGW64 ~/my_folder
$ cat my_file.txt
This is my file content
This is my file contents

HEMAN@HEMANTH MINGW64 ~/my_folder
$ cat another_file.txt
This is my file contents
_________________________________________________________________________________________________________________________________________________________________________________________
Create 20 files with .txt extensions and rename the first 5 files to .yml extension and Print the latest created top 5 files among the total no of files".
HEMAN@HEMANTH MINGW64 ~/my_folder
$ touch file{1..20}.txt

HEMAN@HEMANTH MINGW64 ~/my_folder
$ pwd
/c/Users/HEMAN/my_folder

HEMAN@HEMANTH MINGW64 ~/my_folder
$ l -lrth
bash: l: command not found

HEMAN@HEMANTH MINGW64 ~/my_folder
$ ls -lrth
total 2.0K
-rw-r--r-- 1 HEMAN 197609 25 Jan 23 17:58 another_file.txt
-rw-r--r-- 1 HEMAN 197609 49 Jan 23 18:02 my_file.txt
-rw-r--r-- 1 HEMAN 197609  0 Jan 23 19:37 file1.txt
-rw-r--r-- 1 HEMAN 197609  0 Jan 23 19:37 file2.txt
-rw-r--r-- 1 HEMAN 197609  0 Jan 23 19:37 file3.txt
-rw-r--r-- 1 HEMAN 197609  0 Jan 23 19:37 file4.txt
-rw-r--r-- 1 HEMAN 197609  0 Jan 23 19:37 file5.txt
-rw-r--r-- 1 HEMAN 197609  0 Jan 23 19:37 file6.txt
-rw-r--r-- 1 HEMAN 197609  0 Jan 23 19:37 file7.txt
-rw-r--r-- 1 HEMAN 197609  0 Jan 23 19:37 file8.txt
-rw-r--r-- 1 HEMAN 197609  0 Jan 23 19:37 file9.txt
-rw-r--r-- 1 HEMAN 197609  0 Jan 23 19:37 file10.txt
-rw-r--r-- 1 HEMAN 197609  0 Jan 23 19:37 file11.txt
-rw-r--r-- 1 HEMAN 197609  0 Jan 23 19:37 file12.txt
-rw-r--r-- 1 HEMAN 197609  0 Jan 23 19:37 file13.txt
-rw-r--r-- 1 HEMAN 197609  0 Jan 23 19:37 file14.txt
-rw-r--r-- 1 HEMAN 197609  0 Jan 23 19:37 file15.txt
-rw-r--r-- 1 HEMAN 197609  0 Jan 23 19:37 file16.txt
-rw-r--r-- 1 HEMAN 197609  0 Jan 23 19:37 file17.txt
-rw-r--r-- 1 HEMAN 197609  0 Jan 23 19:37 file18.txt
-rw-r--r-- 1 HEMAN 197609  0 Jan 23 19:37 file19.txt
-rw-r--r-- 1 HEMAN 197609  0 Jan 23 19:37 file20.txt

HEMAN@HEMANTH MINGW64 ~/my_folder
$ for i in {1..5}; do
  mv file$i.txt file$i.yml
done

HEMAN@HEMANTH MINGW64 ~/my_folder
$ ls -lt | head -5
total 2
-rw-r--r-- 1 HEMAN 197609  0 Jan 23 19:37 file20.txt
-rw-r--r-- 1 HEMAN 197609  0 Jan 23 19:37 file19.txt
-rw-r--r-- 1 HEMAN 197609  0 Jan 23 19:37 file18.txt
-rw-r--r-- 1 HEMAN 197609  0 Jan 23 19:37 file17.txt

HEMAN@HEMANTH MINGW64 ~/my_folder
$ ls -lt | head -6
total 2
-rw-r--r-- 1 HEMAN 197609  0 Jan 23 19:37 file20.txt
-rw-r--r-- 1 HEMAN 197609  0 Jan 23 19:37 file19.txt
-rw-r--r-- 1 HEMAN 197609  0 Jan 23 19:37 file18.txt
-rw-r--r-- 1 HEMAN 197609  0 Jan 23 19:37 file17.txt
-rw-r--r-- 1 HEMAN 197609  0 Jan 23 19:37 file16.txt

HEMAN@HEMANTH MINGW64 ~/my_folder
$

