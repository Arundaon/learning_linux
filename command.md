# Command Line Basic
Fitur yang sangat _powerful_ pada linux adalah Terminal. Terminal menjalankan shell yaitu sebuah program yang membaca inputan kita (berupa perintah) yang nantinya akan dikirimkan ke Sistem Operasi untuk dijalankan. Program shell yang paling umum adalah bash (Bourne Again Shell), yaitu shell yang akan kita gunakan pada tutorial kali ini (hampir semua distro menggunakan bash secara default). 
Sebelum kita mulai belajar dasar command line, mari kita jalankan ritual semua programmer menggunakan keyword 'echo' untuk mengeprint sebuah string :
```sh
$ echo Hello World
```

### Navigasi, Directory & File

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

#### cat
cat digunakan untuk membaca file dan menampilkannya ke layar. cat juga bisa mengkombinasikan beberapa file dan mengoutputkannya.
```sh
$ cat somefile
$ cat somefile1 somefile2
```

#### less
less digunakan untuk membaca file, khususnya yang panjang, sehingga bisa discroll.
```sh
$ less longtext.txt
```
Saat menggunakan less, ada key yang digunakan untuk menavigasinya : 
- 'q', quit less
- 'g', kembali ke awal file
- 'G', ke akhir file
- '/', untuk mencari teks pada file, contoh : '/daftar'
- 'h', untuk melihat command-command pada less (lebih lanjut)


### File & Directory Manipulation

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

### Command Sistem
#### history
command history digunakan untuk melihat command yang sebelumnya kita ketikkan. Kita bisa menggunakan tombol up arrow untuk men-cycle ke command sebelumnya.
Shortcut lain history adalah ctrl+R, yang mana adalah reverse command. Kita bisa mencari command yang kita gunakan sebelumnya dan mengeksekusinya langsung.

```sh
$ history
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

#### stdout
'>' adalah redirection operator untuk memilih kemana output pergi (secara default screen). Jadi misal kita menulis "echo Hello World" yang secara default muncul di screen, kita dapat mengoutputkanya ke file hello.txt misalnya. Saat file sudah ada, maka file akan di-overwrite, sedangkan jika file belum ada maka akan membuat file baru.
```sh
$ echo Hello stdout > hello.txt
```
Jika kita tidak ingin meng-overwrite file, melainkan meng-append nya, kita bisa menggunakan operator append '>>'.
```sh
$ echo Hello append > hello.txt
```
#### stdin
'<' adalah redirection operator untuk memilih dari mana input berasal (secara default keyboard). Jadi, misal kita menulis "cat hello.txt", kita bisa juga mendapatkan hasil yang sama saat menulis "cat < hello.txt".
```sh
$ cat < hello.txt
```
#### stderr
Saat kita ingin menggunakan stdout, tapi folder atau file tidak ada, maka akan mengoutputkan error. Secara default, error akan di-print ke screen, tapi kita bisa mengoutputkan error ke dalam file mirip dengan '2>'. 2 Pada stderr ini adalah suatu file descriptor, yaitu nomor yang digunakan untuk mendeskripsikan stream yang digunakan, 0 untuk stdin, 1 untuk stdout, dan 2 untuk stderr.
```sh
$ ls /fakedir 2> err.txt
```
Untuk menggunakan stdout dan stderr sekaligus kita bisa menggunakan operator '&>'. Artinya jika tidak error akan mengoutputkan kedalam file, jika error akan mengoutputkan error.
```sh
$ ls /maybe_exist &> maybe.txt
```

### Pipe & Tee

Pipe operator membolehkan kita untuk mengambil stdout dari command dan menggunakannya sebagai stdin dari command lain sekaligus. Misalnya kita ingin menampilkan command ls ke dalam less, kita bisa menggunakan operator pipe '|' untuk melakukannya.
```sh
$ ls -l | less
```
Apabila kita ingin melakukan write ke banyak file dan stdout, kita bisa menggunakan command 'tee'.
```sh
ls | tee out1.txt out2.txt
```



