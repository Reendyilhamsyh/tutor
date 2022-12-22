Perintah Dasar Linux
Benar benar perintah awal
logout: Keluar dari shell login saat ini
-	passwd: mengganti password
# Ubah kata sandi Anda (Anda akan dimintai kata sandi saat ini terlebih dahulu)
$ passwd
-	sudo — Execute a command as a superuser
Saat Anda ingin melakukan sesuatu yang hanya dapat dilakukan oleh pengguna super, gunakan perintah ini. Misalnya, mengedit file sistem atau menjalankan perintah yang kuat.

Ini kadang-kadang agak sulit dipahami untuk pemula, jadi jika Anda ingin menyelami lebih dalam, lihat blog ini dari Red Hat..

# Edit the file `/etc/motd` (which only superusers have write access to)
$ sudo vi /etc/motdssh: membuat sebuah koneksi SSH connection (sebuah terminal) ke sebuah server
-	ssh — Create an SSH connection (a terminal) to a server
Saat Anda terhubung ke server lain, Anda biasanya menggunakan SSH untuk melakukannya.
Perintah ini membuat sesi baru dan kemudian meminta Anda untuk masuk.
# Opens an SSH connection to _example.com_ and tries to log in as user _dave_.
$ ssh dave@example.com
-	cd — Change the current directory (folder)
To move between different folders, use cd.

# Change directory to `mydocs`
$ cd mydocs

# Change to the parent directory (the directory above the current one)
$ cd ..

# Change to your user home directory (note it's just `cd` without any arguments!)
$ cd
-	ls — List files in a directory
Daftar file dan direktori. Anda dapat menambahkan opsi berbeda ke perintah, untuk mengubah keluaran atau mengurutkannya.yang merupakan adalah yang paling mirip dengan perintah dir di Windows.
# List files in the current directory (to show your current directory, type [pwd](#pwd))
$ ls

# List files (including hidden files) and also show their permissions and who owns them.
$ ls -al

# List files (including hidden), ordering by most recent at the bottom.
$ ls -alrt
-	mkdir — Make/create a new directory
Direktori berfungsi seperti folder. Gunakan perintah ini untuk membuat yang baru.
# Make a directory called `songs`
$ mkdir songs
-	pwd — Print current directory
 Ini menunjukkan direktori kerja Anda (juga disebut direktori saat ini).
-	cp — Copy files and directories
Perintah ini memungkinkan Anda membuat salinan file atau direktori dan isinya. Ini sangat berguna untuk membuat cadangan file saat Anda mengedit sesuatu yang penting dan Anda ingin menyimpan salinannya!

# Copy the contents of the file `money.txt` into a file `money.bak`
$ cp money.txt money.bak

# Copy the directory `songs` (and all of its contents) into `songs2`
$ cp -rp songs songs2
-	rm: Delete files and directories
Tidak ada recycle bin di Linux jadi ketika Anda menggunakan perintah rm, file Anda akan dihapus secara permanen! Untuk menghapus semua file dalam folder, Anda dapat menambahkan opsi -r (“rekursif”).

# Delete the file `myfile.txt`
$ rm myfile.txt

# Delete the directory `songs` and all files in it, without prompting! (warning, use this with caution!)
$ rm -rf songs

Sekarang kita sampai pada perintah yang sangat berguna! Ini adalah perintah yang akan Anda gunakan untuk memanipulasi file dan membuat yang baru. Sebagian besar hal di Linux dikonfigurasi menggunakan file, jadi ada baiknya mengetahui perintah ini. Saat Anda ingin mengedit file teks, Anda akan menggunakan editor teks. Tiga editor teks paling populer adalah vi, nano dan emacs.Personally, I started out with nano and then moved onto vi!

cat — Print the contents of a file
Saat Anda ingin melihat isi file, ini adalah perintah paling sederhana untuk digunakan!

Satu-satunya masalah adalah membuang seluruh file ke terminal Anda. Jadi jika ini adalah file besar dan Anda ingin menjelajahinya, gunakan perintah yang lebih sedikit.
# Print the contents of `songs.txt`
$ cat songs.txt

chmod — Change the permissions of a file or directory
Setiap file di Linux memiliki pengaturan izin untuk tiga grup berbeda: izin pengguna (pemilik), izin grup, dan izin lainnya.

Perintah ini membantu Anda mengatur izin untuk masing-masing dari ketiga grup tersebut.
# Grant all permissions on `myscript.sh` to the user, and execute-only to _group_ and _other_.
$ chmod 755 myscript.sh

# Allow the user to execute `myscript.sh`, and perform no other changes.
$ chmod u+x myscript.sh

chown — Change the owner and group of a file or directory
Selain izin, file di Linux dapat memiliki pemilik dan ditugaskan ke grup.

Perintah ini memungkinkan Anda mengubah pemilik atau grup file.
# Change the owner to _dave_ and the group to _staff_ on the file _accounts.txt_.
$ chown dave:staff accounts.txt

diff — Show the difference between two files
Terkadang Anda ingin melihat perubahan mana yang dibuat pada file, atau mencari tahu apakah dua file sama persis. Perintah ini membantu dengan itu!
# Print the differences between `nyc.txt` and `london.txt`
$ diff nyc.txt london.txt

file — Show the type of a file
Upaya untuk mendeteksi jenis file (misalnya gambar, mp3, program Java). Itu juga dapat mendeteksi beberapa file biner juga.

Ini berguna jika Anda ingin mengetahui untuk apa file digunakan, atau jika file telah disimpan tanpa ekstensi (misalnya seperti .mp3)

Biasanya dapat mendeteksi jenis file yang benar, meskipun nama file memiliki ekstensi yang salah.
# Show the file type of `cilla.mp3`
$ file cilla.mp3

less — Browse the contents of a file
Menampilkan konten file sebagai sekumpulan halaman di terminal Anda. Anda dapat menggunakan tombol panah atau PageUp/PageDown untuk menelusuri file.Sangat berguna untuk file besar!
# Show and scroll the file `songs.txt`. Press `q` to exit.
$ less songs.txt

locate — Find files with names matching a pattern
Mencari database file di disk, untuk menemukan file yang cocok dengan pola tertentu.Basis data hanya diperbarui sekali sehari, jadi ini lebih berguna untuk menemukan file sistem.Ini berbeda dengan yang mencari perintah.
# Find the location of any file called `httpd.conf`
$ locate httpd.conf

tail — Print the last few lines of a file
Sangat berguna jika Anda melihat file log, dan Anda ingin melihat baris terbaru di log.Anda juga dapat menambahkan -f untuk "mengikuti" file, yang berarti setiap baris baru juga akan dicetak ke layar.
# Print end of file and follow new lines in file `server.log`
$ tail -f server.log

touch — Create a new file or update an existing one
Perintah ini sering digunakan untuk melakukan salah satu dari dua hal: membuat file baru yang kosong, atau memperbarui "tanggal modifikasi" pada file yang sudah ada.Secara pribadi saya merasa paling berguna untuk membuat file kosong.
# Create an empty file called `newfile.txt`
$ touch newfile.txt

nano — An interactive file editor
Ini adalah editor file termudah untuk pemula, karena Anda dapat mengetik di mana saja, dan menggunakan tombol panah untuk bergerak.Sebagian besar perintah di nano dimulai dengan ^, yang merupakan tombol Ctrl. Untuk menyimpan file, lihat contoh di bawah ini!
# Edit the file `customers.txt` in _nano_
$ nano customers.txt

# Save a file and then exit.
$ Ctrl+O Ctrl+X

vim — An interactive file editor (Intermediate level)
vim berarti "vi ditingkatkan". Ini merupakan peningkatan dari editor "vi" asli.Segala sesuatu di vim dikontrol dengan perintah keyboard, yang membutuhkan waktu untuk dipelajari. Tapi begitu Anda mempelajarinya, Anda bisa menjadi sangat produktif! Jika Anda menginginkan editor yang lebih mudah, coba nano.
# Edit the file `customers.txt` in _vim_
$ vim customers.txt

📦 Install programs
Bagaimana Anda menginstal perangkat lunak di Linux?

Di Linux, Anda biasanya menginstal perangkat lunak dari repositori. Repositori pada dasarnya adalah tempat sentral yang menyimpan program dan biasanya dijalankan oleh distribusi Linux (misalnya Ubuntu atau Red Hat).

Program yang diinstall seperti ini, biasa disebut dengan package. Repositori berisi ribuan paket! Anda biasanya dapat menginstalnya dengan satu perintah. Anda tidak perlu dipusingkan dengan mengunduh file dari situs web, mengekstraknya, dan sebagainya.

Anda mungkin masih perlu menginstal program secara manual jika tidak ada di repositori, tetapi untuk itu Anda mungkin harus mengikuti petunjuk yang disertakan dengan program.

dnf: Install and manage packages in RHEL/Fedora

apt: Install and manage packages in Ubuntu

dnf — Install and manage packages in RHEL/Fedora
Ini adalah cara baru untuk menginstal perangkat lunak di Red Hat Enterprise Linux (RHEL) dan distro terkait, seperti Fedora dan CentOS.

Sebelumnya, di versi RHEL/Fedora linux yang lebih lama, pengelola paket disebut yum.
🔐 Note you’ll usually need to run this command with sudo.

# Search the online <i>repositories</i> for a package named `curl`
$ dnf search curl

# Install a package called `curl` from the online repositories
$ dnf install curl

# List all packages installed on your system
$ dnf list installed

# Upgrade all packages on your system to the latest compatible versions
$ dnf upgrade

apt — Install and manage packages in Ubuntu
Di Ubuntu, Anda menggunakan perintah ini untuk menginstal dan mengelola paket.

🔐 Note you’ll usually need to run this command with sudo.

# Install a package called `curl` from the online repositories
$ sudo apt install curl

# Uninstall the package called `curl` from your system
$ sudo apt remove curl

📯 Networking
Jaringan adalah salah satu hal tersulit untuk dipahami, karena ada begitu banyak lapisan dan protokol! Bagi kebanyakan dari kita, butuh waktu untuk memahami semuanya.Tetapi alat ini membuat segalanya sedikit lebih mudah, karena memungkinkan Anda membuat permintaan jaringan, mencari informasi, dan memanggil API.Perintah-perintah ini sangat berguna untuk menguji, atau mencari tahu mengapa ada sesuatu yang tidak berfungsi….
curl: Get a web page or API

dig: Look up DNS information

ip addr: Show your network configuration

ping: Check to see if a server is alive

curl — Get a web page or API
Ini adalah alat yang sangat ampuh untuk membuat permintaan HTTP (web). Anda dapat menggunakannya untuk menekan API, mengambil situs web, mengunduh file dari situs web, dan lainnya.
Another solid alternative to this command is wget, but I prefer curl.

# Fetch the Google home page and print the contents
$ curl www.google.com

# Fetch the Google home page and save the HTML to a file
$ curl -o index.html www.google.com

dig — Look up DNS information
DNS adalah cara Anda menerjemahkan nama domain menjadi alamat IP, dan banyak lagi.

Menggunakan dig bisa sangat berguna jika Anda ingin mengetahui hal-hal seperti alamat IP situs web, bagaimana email diproses (dengan data MX), dan banyak lagi.
# Show the IP addresses for domain _reddit.com_
$ dig +short A reddit.com

ip addr — Show your network configuration
Mencetak alamat IP Anda. Anda biasanya akan memiliki beberapa alamat IP di server Linux Anda, tergantung bagaimana konfigurasinya.
# Prints a list of all network interfaces, their IP addresses and config
$ ip addr

ping — Check to see if a server is alive
Sebuah "ping" adalah sesuatu yang spesifik dalam terminologi jaringan. Ini berarti mengirim paket kecil data ke server dan menunggu responsnya.

Anda kadang-kadang akan menggunakan ini jika Anda ingin melihat apakah server hidup dan menanggapi permintaan.
# Send a ping to _www.tutorialworks.com_ to see if it is responding
$ ping www.tutorialworks.com


⌚ Manage processes
Program yang berjalan di Linux biasanya disebut proses.Terkadang Anda akan mendapatkan program yang berhenti merespons, atau Anda perlu memecahkan masalahnya.Perintah-perintah ini membantu dengan itu. Anda dapat membuat daftar proses yang sedang berjalan, menghentikannya, dan banyak lagi.
kill: Terminate a program (process)

top: Show the top processes

ps: List running processes

Ctrl+Z: Suspend a process

fg: Resume a process

jobs: Lists all active jobs (processes)

kill — Terminate a program (process)
Saat Anda ingin mengakhiri proses di Linux, Anda mengirimkannya sinyal. Ada berbagai jenis sinyal, yang umum adalah “TERM” dan “KILL”.

“TERM” berarti menghentikan, seperti permintaan sopan untuk perintah berhenti. "KILL" sedikit lebih kuat - Anda dapat menggunakan ini saat program benar-benar perlu dihentikan sekarang.
# Terminate process number 12345
$ kill 12345

# Forcefully terminate (kill!) process number 12345
$ kill -9 12345

top — Show the top processes
Sedikit mirip dengan Task Manager di Windows, perintah ini menunjukkan kepada Anda semua program yang sedang berjalan, ID prosesnya dan berapa banyak sumber daya yang mereka gunakan, seperti memori dan CPU.

Kami juga memiliki artikel lengkap tentang perintah teratas jika Anda ingin mengetahui lebih lanjut!
ps — List running processes
Mencetak daftar proses saat ini, dengan ID mereka, dan perintah yang digunakan untuk memulai setiap proses.Cara yang bagus untuk mengetahui dengan tepat program mana yang sedang Anda jalankan!Perintah ini menghasilkan daftar proses, sehingga Anda dapat memfilter daftar menggunakan alat lain seperti grep.
# List all your processes
$ ps

# List all processes matching the string `java`
$ ps -ef | grep java

Ctrl+Z — Suspend a process
Ini bukan perintah, tapi ini pintasan keyboard yang bagus untuk diketahui.Ini akan menjeda program, jika sedang berjalan di latar depan, sehingga Anda dapat menjalankan sesuatu yang lain, atau melakukan tugas lain.Untuk melanjutkan proses lagi, gunakan perintah fg.
fg — Resume a process
Un-pauses or resumes a process which you’ve paused using Ctrl+Z.

jobs — Lists all active jobs (processes)
Daftar semua pekerjaan. Ini terutama digunakan ketika Anda menjeda/menangguhkan beberapa proses dan Anda ingin melihat daftarnya.
⚙️ Manajemen sistem
Saat Anda ingin mengetahui lebih lanjut tentang sistem Anda, Anda dapat menggunakan perintah ini.

cat /etc/redhat-release: Show Linux distribution name & version

date: Show the current date and time

df: Show free disk space

du: Show disk space usage

shutdown: Halt or reboot your machine

uname: Print system information

uptime: Show how long the system has been running

cat /etc/redhat-release — Show Linux distribution name & version
Show the current version of your Linux distribution.

You’ll notice that this is actually a file! This file is created when you install Linux. Here we’re just using cat to show the file’s contents.

# Show the Linux distribution name and version
$ cat /etc/redhat-release

date — Show the current date and time
Your server has a date and time set. It also has a time zone too. This will be used whenever the server writes files.

So it’s good to confirm that your server is set with the correct time and timezone.

df — Show free disk space
Want to find out how much disk space you have left? This command does it.

You can change the output in a few different ways to make it more human-readable (see the example below).

# Show free disk space with human-readable sizes
$ df -h

du — Show disk space usage
This is the opposite of the df command. It shows how much space your files and folders are taking up.

It can be handy to figure out where all your space is disappearing to!

# Show disk usage (in human-readable sizes) of all top-level directories
$ du -h -d 1 /

shutdown — Halt or reboot your machine
Getting ready to shut down your server? Use this command.

Be careful that nobody else is using the server at the same time. :-)

🔐 Note you’ll usually need to run this command with sudo.

# Reboot the system now
$ shutdown -r now

uname — Print system information
Shows information about the Linux kernel.

# Show all info about the Linux kernel, including version number.
$ uname -a

uptime — Show how long the system has been running
Use this to check whether your system has been running without problems, or whether it’s been restarted at some point recently.
Docker container
Untuk menampilkan semua Docker image yang ada di sistem Anda, gunakan command berikut:

sudo docker images
Kalau ingin menampilkan informasi tambahan, masukkan command berikut ke command line:

sudo docker images --help
Pada contoh ini, kami belum memiliki Docker Image satu pun, jadi kami akan melakukan pull image lebih dulu. Buka Docker Hub, yang berisi ratusan Docker Image.

Di sini kami akan mengambil image Ubuntu. Anda bisa mengklik setiap image untuk mengetahui detailnya masing-masing.
Anda bisa melakukan pull image dengan command berikut:

docker pull <image name>
Ganti <image name> dengan ratusan image yang bisa Anda temukan di Docker Hub seperti CentOS, MySQL, mariaDB, Python, dll.

Untuk mencantumkan hanya angka ID Image yang tersedia di dalam sistem, gunakan opsi -q.

sudo docker images -q
Kemudian, -f adalah filter flag. Kalau Anda ingin menampilkan semua image yang tidak berkaitan (dangling), yaitu yang ditag atau dirujuk oleh container lain, gunakan command berikut:

sudo docker images -f “dangling=false”
Setelah tahu cara pull dan menemukan image untuk membuat container Docker, mari mulai cara membuat Docker container.

Berikutnya, kami akan mencoba menjalankan image, yang berarti membuat container dari image tersebut. Kami akan mencoba menjalankan image Ubuntu tadi. Gunakan command berikut untuk membuat container Docker:

docker run <image_name>
Untuk menjalankan image Ubuntu, gunakan command berikut:

docker run ubuntu
Sekarang, container sudah dibuat, tapi belum berjalan.

Untuk mengaktifkan container, jalankan command berikut:

docker run --name MyContainer -it ubuntu bash
Dari kode di atas, -name MyContainer merupakan nama yang kita inginkan untuk proses yang sedang berjalan, sedangkan -it ubuntu bash akan menamai container yang dijalankan.

Buka jendela terminal lainnya, gunakan SSH untuk terhubung ke server, dan jalankan command ini:

sudo docker ps -a
Hasilnya, kita bisa melihat bahwa container yang diberi nama MyContainer sekarang sudah berjalan.

Untuk menghentikan container, jalankan command berikut:

sudo docker stop MyContainer
Kalau ingin melihat proses teratas container, gunakan command berikut:

docker top < container ID or Name>
Dengan nama yang tadi digunakan dalam contoh ini, kodenya akan menjadi seperti berikut:

sudo docker top MyContainer
Untuk melihat statistik container, misalnya penggunaan CPU, penggunaan memori, dan lainnya, ketik command:

docker stats
Terakhir, untuk melakukan kill Docker container, jalankan command berikut:

sudo docker kill MyContainer
Selesai! Anda sudah selesai mempelajari cara membuat Docker Container dan menggunakannya.

Kesimpulan
Docker merupakan tool yang sangat berguna bagi developer. Fungsinya untuk mengetes, meluncurkan (deploy), dan mengembangkan aplikasi tanpa masalah menjadi terobosan yang sangat membantu mempercepat alur kerja (workflow).

Di tutorial ini, Anda telah mempelajari cara membuat container Docker beserta sejumlah command yang diperlukan untuk menjalankan semua operasi terkait Docker container.

Berikut ini kumpulan query  SQL:

1. Create Database
Digunakan untuk membuat database baru.
Syntax dasar:
CREATE DATABASE database_nama
Contoh:
CREATE DATABASE databaru
2. Create Table
Digunakan untuk membuat tabel data baru dalam sebuah database.
Syntax dasar:
CREATE TABLE
(
Column_name1 table_nama data_type
Column_name2 table_nama data_type
Column_name3 table_nama data_type
)
Contoh:
CREATE TABLE tabeldata
( Id int, Nama varchar (255), Email varchar(50),
Kota varchar(255))
3. Select
Digunakan untuk memilih data dari table database.
Syntax dasar:
SELECT column_name(s)
FROM table_name
Atau
SELECT * FROM table_name
Contoh 1:
SELECT nama,email FROM tabeldata
Contoh 2:
SELECT * FROM tabeldata
4. Select Distinct
Digunakan untuk memilih data-data yang berbeda (menghilangkan duplikasi) dari sebuah table database.
Syntax dasar:
SELECT DISTINCT column_name(s)
FROM table_name
Contoh:
SELECT DISTINCT kota FROM tabeldata
5. Where
Digunakan untuk memfilter data pada perintah Select
Syntax dasar:
SELECT column name(s)
FROM table_name
WHERE column_name operator value
Contoh:
SELECT * FROM tabeldata WHERE kota=’Kediri’
6. Order By
Digunakan untuk mengurutkan data berdasarkan kolom (field) tertentu. Secara default, urutan tersusun secara ascending (urut kecil ke besar). Anda dapat mengubahnya menjadi descending (urut besar ke kecil) dengan menambahkan perintah DESC.
Syntax dasar:
SELECT column_name(s)
FROM table_name
ORDER BY column_name(s) ASC|DESC
Contoh 1:
SELECT * FROM tabeldata ORDER BY nama
Contoh 2:
SELECT * FROM tabeldata ORDER BY id DESC
7. Like
Digunakan bersama dengan perintah Where, untuk proses pencarian data dengan spesifikasi tertentu.
Syntax dasar:
SELECT column_name(s)
FROM table_name
WHERE column_name LIKE pattern
Contoh 1:
SELECT * FROM tabeldata WHERE nama LIKE ‘z%’
Keterangan :
Contoh di atas digunakan untuk pencarian berdasarkan kolom nama yang berhuruf depan “z”.
Contoh 2:
SELECT * FROM tabeldata WHERE nama LIKE ‘z%’
Keterangan :
Contoh di atas digunakan untuk pencarian berdasarkan kolom nama yang berhuruf belakang “z”.

8. In
Digunakan untuk pencarian data menggunakan lebih dari satu filter pada perintah Where.
Syntax dasar :
SELECT column_name(s)
FROM table_name
WHERE column_name IN (value1,value2, . . .)
Contoh:
SELECT * FROM tabeldata WHERE kota IN (‘kediri’,’malang’)
9. Between
Digunakan untuk menentukan jangkauan pencarian.
Syntax dasar:
SELECT column_name(s)
FROM table_name
WHERE column_name
BETWEEN value1 AND value2
Contoh :
SELECT * FROM tabeldata WHERE id BETWEEN 15 and 45
Keterangan :
Contoh di atas digunakan untuk mencari data yang memiliki nomor id antara 15 dan 45.

10.  Insert Into
Digunakan untuk menambahkan data baru di tabel database.
Syntax dasar :
INSERT INTO table_name
VALUES (value1,value2,value3, . . .)
Atau
INSERT INTO table_name (column1,column2,column3, . . .)
VALUES (value1,value2,value3, . . .)
Contoh 1:
INSERT INTO tabeldata VALUES (1,’redaksi’,’redaksi@kuliahkomputer.com’,’Kediri’)
Contoh 2:
INSERT INTO tabeldata (id,nama,email,kota) VALUES (1,’redaksi’,’redaksi@kuliahkomputer.com’,’Kediri’)
11.  Update
Digunakan untuk mengubah/memperbarui data di tabel database.
Syntax dasar:
UPDATE table_name
SET column1=value,column2=value, . . .
WHERE some_column=some_value
Contoh :
UPDATE tabeldata SET email=’redaksi@kuliahkomputer.com’, kota=’Kediri’
WHERE id =1
12.  Delete
Digunakan untuk menghapus data di table database. Tambahkan perintah Where untuk memfilter data-data tertentu yang akan dihapus. Jika tanpa perintah Where, maka seluruh data dalam tabel akan terhapus.
Syntax dasar :
DELETE FROM table_name
WHERE some_column=some_value
Contoh:
DELETE FROM tabeldata WHERE id=1
13.  Inner Join
Digunakan untuk menghasilkan baris data dengan cara menggabungkan 2 buah tabel atau lebih menggunakan pasangan data yang match pada masing-masing tabel. Perintah ini sama dengan perintah join yang sering digunakan.
Syntax dasar :
SELECT column_name(s)
FROM table_name1
INNER JOIN table_name2
ON table_name1.column_name=table_name2
column-name
contoh :
SELECT tabeldata.nama,tabeldata.email,order.no_order
FROM tabeldata
INNER JOIN order
ON tabeldata.id=order.id
ORDER BY tabeldata.nama
14.  Left Join
Digunakan untuk menghasilkan baris data dari tabel kiri (nama tabel pertama) yang tidak ada pasangan datanya pada tabel kanan (nama tabel kedua).
Syntax dasar :
SELECT column_name(s)
FROM table_name1
LEFT JOIN table_name2
ON table_name1.column_name=table_name2.
column_name
contoh :
SELECT tabeldata.nama,tabeldata.email,order.no_order
FROM tabeldata
LEFT JOIN order
ON tabeldata.id=order.id
ORDER BY tabeldata.nama
15.  Right Join
Digunakan untuk menghasilkan baris data dari tabel kanan (nama tabel kedua) yang tidak ada pasangan datanya pada tabel kiri (nama tabel pertama).
Syntax dasar :
SELECT column_name(s)
FROM table_name1
RIGHT JOIN table_name2
ON table_name1.column_name=table_name2
column_name
contoh :
SELECT tabeldata.nama,tabeldata.emailmorder.no_order
FROM tabeldata
RIGHT JOIN order
ON tabeldata.id=order.i
ORDER BY tabeldata.nama
16.  Full Join
Digunakan untuk menghasilkan baris data jika ada data yang sama pada salah satu tabel.
Syntax dasar :
SELECT column_name(s)
FROM table_name1
FULL JOIN table_name2
ON table_name1.column_name=table_name2
column_name
Contoh :
SELECT tabeldata.nama,tabeldata.email,order.no_order
FROM tabeldata
FULL JOIN order
ON tabeldata.id=order.id
ORDER BY tabeldata.nama
17.  Union
Digunakan untuk menggabungkan hasil dari 2 atau lebih perintah Select.
Syntax dasar :
SELECT column_name(s)FROM table_name1
UNION column_name(s) FROM table_name2
Atau
SELECT column_name(s) FROM table_name1
UNION ALL
SELECT column_name(s) FROM table_name2
Contoh :
SELECT nama FROM mhs_kampus1
UNION
SELECT nama FROM mhs_kampus2
18.  Alter Table
Digunakan untuk menambah, menghapus, atau mengubah kolom (field) pada tabel yang sudah ada.
Syntax untuk menambah kolom :
ALTAR TABLE table_name
ADD column_name datatyoe
Contoh :
ALTER TABLE Persons
ADD DateOfBirth date
Syntax untuk menghapus kolom :
ALTER TABLE table_name
DROP COLUMN column_name
Contoh :
ALTER TABLE Persons
DROP COLUMN DateOfBirth
Syntax untuk mengubah kolom :
ALTER TABLE table_name
ALTER TABLE clumn_name datatype
Contoh :
ALTER TABLE Persons
ALTER COLUMN DateOfBirth year
19.  Now ()
Digunakan untuk mendapatkan informasi waktu (tanggal dan jam saat ini.)
Syntax dasar :
Now()
Contoh :
SELECT NOW()
20.  Curdate
Digunakan unutk mendapatkan informasi tanggal saat ini.
Syntax dasar :
Curdate()
Contoh :
SELECT CURDATE()

21.  Curtime()
Digunakan untuk mendapatkan informasi jam saat ini.
Syntax dasar :
Curtime()
Contoh :
SELECT CURTIME()
22.  Extract()
Digunakan untuk mendapatkan informasi bagian-bagian dari data waktu tertentu, seperti tahun, bulan, hari, jam, menit, dan detik tertentu.
Syntax dasar :
Extract(unit FROM date)
Keterangan :
Parameter unit dapat berupa :
• MICROSECOND
• SECOND
• MINUTE
• HOUR
• DAY
• WEEK
• MONTH
• QUARTER
• YEAR
• SECOND_MICROSECOND
• MINUTE_SECOND
• HOUR_MICROSECOND
• HOUR_SECOND
• HOUR_MINUTE
• DAY_MICROSECOND
• DAY_SECOND
• DAY_MINUTE
• DAY_HOUR
• YEAR_MONTH
Contoh :
SELECT EXTRAXT (YEAR FROM tglorder( AS Th_Order, EXTRACT (MONTH FROM tglorder) AS Bulan_Order,EXTRACT (FAY FROM tglorder AS Hari_Order,
FROM order
23.  Date_Add() dan Date_Sub()
Fungsi Date_Add() digunakan unutk menambahkan interval waktu tertentu pada sebuah tanggal, sedangkan fungsi Date_Sub() digunakan untuk pengurangan sebuah tanggal dengan interval tertentu.
Syntax dasar :
DATE_ADD (date,INTERVAL expr type)
DATE_SUB (date,INTERVAL expr type)
Keterangan :
Tipe data parameter INTERVAL dapat berupa :
• MICROSECOND
• SECOND
• MINUTE
• HOUR
• DAY
• WEEK
• MONTH
• QUARTER
• YEAR
• SECOND_MICROSECOND
• MINUTE_MICROSECOND
• MINUTE_SECOND
• HOUR_MICROSEDOND
• HOUR_SECOND
• HOUR_MINUTE
• DAY_MICROSECOND
• DAY_SECOND
• DAY_MINUTE
• DAY_HOUR
• YEAR_MONTH
Contoh 1:
SELECT id,DATE_ADD (tglorder,INTERVAL 30 DAY)
AS Waktu_pembayaran
FROM order
Contoh 2:
SELECT id,DATE_SUB(tglorder,INTERVAL 5 DAY)
AS Pengurangan_Waktu
FROM order
24.  DateDiff()
Digunakan untuk mendapatkan informasi waktu di antara 2 buah tanggal.
Syntax dasar :
DATEIFF(date1,date2)
Contoh :
SELECT DATEIFF(‘2010-06-30’,’2010-06-29’)
AS Selisih_waktu
25.  Date_Format()
Digunakan untuk menampilkan informasi jam dan tanggal dengan format tertentu.
Syntax dasar :
DATE_FORMAT(date,format)
Keterangan :
Parameter format dapat berupa :
• %a, nama hari yang disingkat
• %b, nama bulan yang disingkat
• %c, bulan (numerik)
• %D hari dalam sebulan dengan format English
• %d, hari dalam sebulan (numerik 00-31)
• %e, hari dalam sebulan (numerik 0-31)
• %f, micro detik
• %H, jam (00-23)
• %h, jam (01-12)
• %I, jam (01-12)
• %i, menit (00-59)
• %j, hari dalam setahun (001-366)
• %k, jam (0-23)
• %l, jam (1-12)
• %M, nama bulan
• %m, bulan (numerik 00-12)
• %p, AM atau PM
• %r, waktu jam dalam format 12 jam (hh:mm:ss AM or PM)
• %S, detik (00-59)
• %s, detik (00-59)
• %T, waktu jam dalam format 24 jam (hh:mm:ss)
• %U, minggu (00-53) dimana Sunday sebagai hari pertama dalam seminggu
• %u, minggu (00-53) dimana Monday sebagai hari pertama dalam seminggu
• %W, nama hari kerja
• %w, hari dalam seminggu (0=Sunday, 6=Saturday)
• %X, tahun dalam seminggu dimana Sunday sebagai hari pertama dalam seminggu (4 digits) digunakan dengan %V
• %x, tahun dalam seminggu di mana Monday sebagai hari pertama dalam seminggu (4 digits) digunakan dengan %v
• %Y, tahun 4 digit
• %y, tahun 2 digit
Contoh :
DATA_FORMAT (NOW(),’%b %d %Y %h : %i %p’)
DATE_FORMAT (NOW(),’%m-%d-%Y’)
DATE_FORMAT (NOW(),’%d %b %Y’)
DATE_FORMAT (NOW(),’%d %b %Y %T : %f’)
26.  Drop Table
Digunakan untuk menghapus tabel beserta seluruh datanya.
Syntax dasar :
DROP TABLE table_name
Contoh :
DROP TABLE mhs
27.  Drop Database()
Digunakan untuk menghapus database.
Syntax dasar :
DROP DATABASE database_name
28.  AVG()
Digunakan untuk menghitung nilai-rata-rata dari suatu data.
Syntax dasar :
SELECT  AVG (column_name) FROM table_name
Contoh :
SELECT AVG(harga) AS Harga_rata2FROM order
29.  Count()
Digunakan untuk menghitung jumlah (cacah) suatu data.
Syntax dasar :
SELECT COUNT (column_name) FROM table_name
Contoh :
SELECT COUNT(id) AS Jumlah_tamu FROM tabeldata
30.  Max()
Digunakan untuk mendapatkan nilai terbesar dari data-data yang ada.
Syntax dasar :
SELECT MAX (column_name) FROM table_name
Contoh :
SELECT MAX(harga) AS Harga_termahal FROM order
31.  Min()
Digunakan untuk mendapatkan nilai terkecil dari data-data yang ada.
Syntax dasar :
SELECT MIN (column_name) FROM table_name
Contoh:
SELECT MIN(harga) AS Harga_termurah FROM order
32.  Sum()
Digunakan untuk mendapatkan nilai total penjumlahan dari data-data yang ada.
Syntax dasar :
SELECT SUM (column_name) FROM table_name
Contoh :
SELECT SUM(harga) AS Harga_total FROM order
33.  Group By()
Digunakan untuk mengelompokkan data dengan kriteria tertentu.
Syntax dasar :
SELECT column_name,aggregate_function(column_name)
FROM table_name
WHERE column_name operator value
GROUP BY column_name
Contoh :
SELECT nama_customer,SUM(harga) FROM order GROUP BY nama_customer
34.  Having()
Digunakan untuk memfilter data dengan fungsi tertentu.
Syntax dasar :
SELECT column_name,aggregate_function(column_name)
FROM table_name
WHERE column_name operator value
GROUP BY column_name
HAVING aggregate_function(column_name) operator value
Contoh :
SELECT nama_customer,SUM(harga) FROM order
WHERE nama_customer=’Rico’ OR nama_customer=’Bastian’
GROUP BY nama_customer
HAVING SUM (harga)>125000
35.  Ucase()
Digunakan untuk mengubah huruf pada data tertentu menjadi huruf besar.
Syntax dasar :
SELECT UCASE (column_name) FROM table_name
Contoh :
SELECT UCASE(nama) as Nama FROM tabeldata
36.  Lcase()
Digunakan untuk mengubah huruf pada data tertentu menjadi huruf kecil.
Syntax dasar :
SELECT LCASE (column_name) FROM table_name
Contoh :
SELECT LCASE(nama) as Nama FROM tabeldata
37.  Mid()
Digunakan untuk mengambil beberapa karakter dari field teks.
Syntax dasar:
SELECT MID(column_name,start[,length]) FROM table_name
Contoh:
SELECT MID (kota,1,4) as singkatan_kota FROM tabeldata
38.  Len()
Digunakan unutk mendapatkan informasi jumlah karakter dari field teks.
Syntax dasar:
SELECT LEN (column_name) FROM table_name
Contoh:
SELECT LEN(nama) as panjang_nama FROM tabeldata
39.  Round()
Digunakan untuk pembuatan bilangan pecahan.
Syntax dasar:
SELECT ROUND (column_name,decimals)
FROM table_name
Contoh:
SELECT no_mhs, ROUND (nilai,0) as nilai_bulat FROM tabeldata
Microservices adalah suatu framework Architecture yang dipakai sebagai model dalam pembuatan aplikasi cloud yang modern. Di dalam microservices setiap aplikasi di bangun sebagai sekumpulan service dan setiap layanan berjalan dalam processnya sendiri. Masing-masing dari aplikasi tersebut saling berkomunikasi melalu API (Application Programing Interface).
Microservices digunakan secara bersamaan dengan Docker Container. Container adalah perantara yang sangat tepat untuk mendeploy Microservices. Container dapat diluncurkan dalam hitungan detik, sehingga dapat diterapkan kembali dengan cepat setelah kegagalan atau migrasi, dan dapat di scale-up dengan cepat untuk memenuhi permintaan.

Container bahkan lebih efisien daripada VM, memungkinkan kode (dan code library yang diperlukan) untuk diterapkan pada sistem Linux apa pun (atau OS apa pun yang mendukung kontainer Docker).  

Karena Container adalah bawaan Linux, perangkat keras komoditas dapat diterapkan ke berbagai microservices di datacenter, private cloud, atau multicloud hybrid.

MVC
MVC atau Model View Controller adalah sebuah pola desain arsitektur dalam sistem pengembangan website yang terdiri dari tiga bagian, yaitu: 
Model, bagian yang mengelola dan berhubungan langsung dengan database;
View, bagian yang akan menyajikan tampilan informasi kepada pengguna;
Controller, bagian yang menghubungkan model dan view dalam setiap proses request dari user. 
Dengan konsep MVC ini, website seakan memiliki bagian yang terpisah dan bisa dikembangkan masing-masing. Maka, proses pembuatan website bisa dilakukan lebih cepat karena developer akan lebih fokus pada pengerjaan salah satu bagian saja. 
Karena dianggap efektif, konsep MVC banyak diterapkan di berbagai framework. Sebagai contoh, di framework PHP terbaik seperti Laravel, CodeIgniter, Symfony, Yii, dan Zend sudah menggunakan konsep ini.
Oke, setelah mempelajari apa itu MVC, sekarang saatnya memahami bagaimana alur kerja dari MVC. Mari lihat bagan berikut ini:
 
Bagan MVC 
Bagian view akan merequest informasi untuk bisa ditampilkan kepada pengguna.
Request tersebut kemudian diambil oleh controller dan diserahkan bagian model untuk diproses; 
Model akan mengolah dan mencari data informasi tersebut di dalam database;
Model memberikan kembali pada controller untuk ditampilkan hasilnya di view; 
Controller mengambil hasil olahan yang dilakukan di bagian model dan menatanya di  bagian view.
Contoh Penggunaan Konsep MVC
Rasanya kurang afdol jika pembahasan konsep MVC ini tidak disertai dengan contoh, ya? Nah, ini dia contoh pembuatan form data user di website dengan menggunakan CodeIgniter: 

Download CodeIgniter dan ekstrak file tersebut ke web server Anda. 
Buat folder model terlebih dulu supaya data pengguna bisa masuk ke database. Lalu, tambahkan kode berikut: 
<?php
class M_user extends CI_Model
{
        public function insert_data($table, $data)
        {
        return $this->db->insert($table, $data);
        }
}
Selanjutnya, untuk controller buat folder baru lagi dengan nama yang berbeda dari folder model. Lalu tambahkan kode berikut: 
<?php
class User extends CI_Controller 
{
    public function add()
    {
        $this->load->view('user_add');
    }
}
Kemudian untuk tampilan (view) formnya, buat lagi folder baru dan isikan kode berikut: 
<!DOCTYPE html>
<html>
    <head>
        <title>Membuat Form Tambah User</title>
    </head>
    <body>
        <center>
            <h2>Form Tambah Data User</h2>
            <form method="post" action="<?= base_url('user/save'); ?>">
                <table border="1">
                    <tr>
                        <td>Email</td>
                        <td><input type="text" name="email"></td>
                    </tr>
                    <tr>
                        <td>Password</td>
                        <td><input type="password" name="password"></td>
                    </tr>
                    <tr>
                        <td>Nama</td>
                        <td><input type="text" name="nama"></td>
                    </tr>
                    <tr>
                        <td colspan="2"><input type="submit" name="kirim" value="Masukkan Data"></td>
                    </tr>
                </table>
            </form>
        </center>
    </body>
</html>
MVP
Sampel ini berdiri di atas prinsip Arsitektur Bersih.

Ini didasarkan pada sampel MVP, menambahkan lapisan domain antara lapisan presentasi dan repositori, membagi aplikasi menjadi tiga lapisan:
 
MVP: Pola Model View Presenter dari sampel dasar.
Domain: Menyimpan semua logika bisnis. Lapisan domain dimulai dengan kelas bernama kasus penggunaan atau interaksi yang digunakan oleh penyaji aplikasi. Kasus penggunaan ini mewakili semua kemungkinan tindakan yang dapat dilakukan pengembang dari lapisan presentasi.
Repositori: Pola repositori dari sampel dasar.
Konsep kunci
Perbedaan besar dengan sampel MVP dasar adalah penggunaan lapisan Domain dan kasus penggunaan. Memindahkan lapisan domain dari penyaji akan membantu menghindari pengulangan kode pada penyaji (mis. Filter tugas).

Kasus penggunaan menentukan operasi yang dibutuhkan aplikasi. Ini meningkatkan keterbacaan karena nama kelas membuat tujuannya jelas (lihat tugas/domain/usecase/).

Kasus penggunaan bagus untuk penggunaan kembali operasi melalui kode domain kami. CompleteTask adalah contoh yang bagus untuk ini karena digunakan dari TaskDetailPresenter dan TasksPresenter.

Eksekusi kasus penggunaan ini dilakukan di utas latar menggunakan pola perintah. Lapisan domain dipisahkan sepenuhnya dari Android SDK atau pustaka pihak ketiga lainnya.

Masalah/catatan
Kasus penggunaan lari dari utas utama, yang merupakan solusi bagus untuk aplikasi Android. Ini dilakukan sesegera mungkin untuk menghindari pemblokiran utas UI. Kami memutuskan untuk menggunakan pola perintah dan menjalankan setiap kasus penggunaan dengan kumpulan utas, tetapi kami dapat menerapkan hal yang sama dengan RxJava atau Promises.

Kami menggunakan repositori asinkron, tetapi tidak perlu melakukan ini lagi karena kasus penggunaan dijalankan dari utas utama. Ini disimpan untuk menjaga sampel semirip mungkin dengan yang asli.

Kami merekomendasikan penggunaan model yang berbeda untuk lapisan Tampilan, domain, dan API, tetapi dalam kasus ini semua model tidak dapat diubah sehingga tidak perlu menduplikasinya. Jika model Tampilan berisi bidang terkait Android, kami akan menggunakan dua model, satu untuk domain dan lainnya untuk Tampilan dan kelas mapper yang mengonversi keduanya.

Callback memiliki metode onError yang dalam aplikasi sebenarnya harus berisi informasi tentang masalah tersebut.

Testabilitas
Dengan pendekatan ini, semua kode domain diuji dengan pengujian unit. Ini dapat diperluas dengan pengujian integrasi, yang mencakup dari Kasus Penggunaan hingga batas tampilan dan repositori.

Ketergantungan
Selain dukungan dan pengujian perpustakaan, tidak ada
GITHUB Command
https://docs.github.com/en/get-started/using-git/about-git
Basic Git commands
Untuk menggunakan Git, pengembang menggunakan perintah khusus untuk menyalin, membuat, mengubah, dan menggabungkan kode. Perintah-perintah ini dapat dijalankan langsung dari baris perintah atau dengan menggunakan aplikasi seperti GitHub Desktop. Berikut adalah beberapa perintah umum untuk menggunakan Git:
git init menginisialisasi repositori Git baru dan mulai melacak direktori yang ada. Itu menambahkan subfolder tersembunyi di dalam direktori yang ada yang menampung struktur data internal yang diperlukan untuk kontrol versi.
git clone membuat salinan lokal dari proyek yang sudah ada dari jarak jauh. Klon mencakup semua file, riwayat, dan cabang proyek.
git add stages a change. Git melacak perubahan ke basis kode pengembang, tetapi penting untuk melakukan stage dan mengambil snapshot dari perubahan untuk memasukkannya ke dalam riwayat proyek. Perintah ini melakukan pementasan, bagian pertama dari proses dua langkah tersebut. Setiap perubahan yang dipentaskan akan menjadi bagian dari snapshot berikutnya dan bagian dari sejarah proyek. Pementasan dan komitmen secara terpisah memberi pengembang kendali penuh atas riwayat proyek mereka tanpa mengubah cara mereka membuat kode dan bekerja.
git commit menyimpan snapshot ke riwayat proyek dan menyelesaikan proses pelacakan perubahan. Singkatnya, komit berfungsi seperti mengambil foto. Apa pun yang telah dipentaskan dengan git add akan menjadi bagian dari snapshot dengan git commit.

git status shows the status of changes as untracked, modified, or staged.

git branch shows the branches being worked on locally.

git merge menggabungkan garis-garis pembangunan bersama-sama. Perintah ini biasanya digunakan untuk menggabungkan perubahan yang dilakukan pada dua cabang yang berbeda. Misalnya, pengembang akan menggabungkan ketika mereka ingin menggabungkan perubahan dari cabang fitur ke dalam cabang utama untuk diterapkan.
git pull memperbarui jalur pengembangan lokal dengan pembaruan dari mitra jarak jauhnya. Pengembang menggunakan perintah ini jika rekan satu tim telah melakukan komitmen ke cabang di jarak jauh, dan mereka ingin mencerminkan perubahan tersebut di lingkungan lokal mereka.

git push updates the remote repository with any commits made locally to a branch.
Example: Contribute to an existing repository
# download a repository on GitHub to our machine
# Replace `owner/repo` with the owner and name of the repository to clone
git clone https://github.com/owner/repo.git

# change into the `repo` directory
cd repo

# create a new branch to store any new changes
git branch my-branch

# switch to that branch (line of development)
git checkout my-branch

# make changes, for example, edit `file1.md` and `file2.md` using the text editor

# stage the changed files
git add file1.md file2.md

# take a snapshot of the staging area (anything that's been added)
git commit -m "my snapshot"

# push changes to github
git push --set-upstream origin my-branch

Example: Mulai repositori baru dan publikasikan ke GitHub
Pertama, Anda perlu membuat repositori baru di GitHub. Untuk informasi lebih lanjut, lihat "Halo Dunia." Jangan menginisialisasi repositori dengan file README, .gitignore, atau Lisensi. Repositori kosong ini akan menunggu kode Anda.
# create a new directory, and initialize it with git-specific functions
git init my-repo

# change into the `my-repo` directory
cd my-repo

# create the first file in the project
touch README.md

# git isn't aware of the file, stage it
git add README.md

# take a snapshot of the staging area
git commit -m "add README to initial commit"

# provide the path for the repository you created on github
git remote add origin https://github.com/YOUR-USERNAME/YOUR-REPOSITORY-NAME.git

# push changes to github
git push --set-upstream origin main
Example: contribute to an existing branch on GitHub
This example assumes that you already have a project called repo on the machine and that a new branch has been pushed to GitHub since the last time changes were made locally.

# change into the `repo` directory
cd repo

# update all remote tracking branches, and the currently checked out branch
git pull

# change into the existing branch called `feature-a`
git checkout feature-a

# make changes, for example, edit `file1.md` using the text editor

# stage the changed file
git add file1.md

# take a snapshot of the staging area
git commit -m "edit file1"

# push changes to github
git push

