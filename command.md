# Command Line Basic
Fitur yang sangat _powerful_ pada linux adalah Terminal. Terminal menjalankan shell yaitu sebuah program yang membaca inputan kita (berupa perintah) yang nantinya akan dikirimkan ke Sistem Operasi untuk dijalankan. Program shell yang paling umum adalah bash (Bourne Again Shell), yaitu shell yang akan kita gunakan pada tutorial kali ini (hampir semua distro menggunakan bash secara default). 
Sebelum kita mulai belajar dasar command line, mari kita jalankan ritual semua programmer menggunakan keyword 'echo' untuk mengeprint sebuah string :
```sh
$ echo Hello World
```

### Navigasi
#### pwd 
pwd (Print Working Directory) digunakan untuk melihat pada directory mana kita saat ini berada menggunakan absolute path, yaitu path dari root sampai directory saat ini.
```sh 
$ pwd
/home/user/Desktop
$
```
#### cd 
cd (Change Directory) digunakan untuk berpindah dari directory satu ke directory lain. Ada beberapa shortcut yang dapat digunakan pada command cd : 
- '.' (current directory)
- '..' (parent directory)
- '~' (home directory)
- '-' (previous directory)
```sh
$ cd /home/user/Desktop
$ cd ./tugas # /home/user/Desktop/tugas
$ cd .. # /home/user/Desktop
$ cd ~ # /home/user
$ cd - # /home/user/Desktop
```

#### ls
ls digunakan untuk menampilkan isi dari sebuah directory, secara default adalah current directory. Ada beberapa flag yang kita berikan untuk menambah fungsionalitas tambahan : 
- '-a'  (menampilkan file dan folder tersembunyi)
- '-l' (menampilkan dalam format lebih detail)
```sh
$ ls
file1 file2 folder1
$ ls -a
. .. .hiddenfile file1 file2 folder1
$ ls -l
-rwxrwxrwx 1 user user      79 Mar 15 10:45  file1
-rwxrwxrwx 1 user user   16384 Feb 10  2021  file2
drwxrwxrwx 1 user user     512 Mar 22 20:40  folder1

```
### File Manipulation
#### touch
Digunakan untuk membuat sebuah file kosong.
```sh
$ touch file_baru
```
#### cp
Digunakan untuk men-copy sebuah file (untuk mencopy directory, harus ditambah flag -r).
```sh
$ cp ./thisfile.txt ./to_this_folder
$ cp -r ./thisfolder ./to_this_folder
```
#### mv
Digunakan untuk memindahkan file atau folder
```sh
$ mv ./thisfile.txt ./to_this_folder
```
Biasanya mv juga digunakan untuk merename suatu file atau folder.
```sh
$ mv ./oldname.txt ./newname.txt
```
#### rm
Digunakan untuk menghapus file.
```sh
$ rm thisfile.txt
```
#### mkdir
Digunakan untuk membuat folder atau direktori baru.
```sh
$ mkdir ./newdir
```
#### rmdir
Digunakan untuk menghapus folder atau direktori.
```sh
$ rmdir ./delete_this_dir
```
### Wildcard
Saat kita menggunakan command  misalnya cp, kita bisa men-copy beberapa file sekaligus menggunakan wildcard. Command lain yang juga bisa menggunakan wildcard misalnya rm dan mv. Command akan mengeksekusi sebanyak file atau folder yang memenuhi pattern wildcard. 
- '*' merepresentasikan lebih dari satu karakter
- '?' merepresentasikan satu karakter
- '[]' merepresentasikan karakter yang ada pada bracket
```sh
$ cp *.jpg ./pictures
```

### Redirection
