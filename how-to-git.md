#How To Git
---
### Git Config
1. Menginformasikan nama dengan parameter global <br>
` git config --global user.name "<nama>" ` <br>
Perintah tersebut digunakan untuk memberikan informasi nama kolaborator ke git-client (ganti parameter <nama> dengan nama kolaborator). Nama kolaborator tersebut nantinya akan disimpan pada global config dan git client akan menyimpan informasi tersebut sebagai default config. User tidak perlu menjalankan perintah ini setiap akan menjalankan operasi git. Untuk mengganti nama kolaborator, user hanya tinggal menjalankan ulang perintah ini dengan nama kolaborator yang baru.

1. Menginformasikan email dengan parameter global <br>
` git config --global user.email "<email>" ` <br>
Perintah tersebut sama dengan perintah sebelumnya, dalam hal ini ganti <email> dengan email kolaborator.

1. Melihat informasi konfigurasi git yang sudah diterapkan <br>
` git config --list ` <br>
Perintah tersebut digunakan untuk melihat konfigurasi yang sudah diterapkan. Perlu diketahui bahwa konfigurasi Git dapat disimpan pada 3 lokasi (system, home directory, local repository). Konfigurasi yang diletakkan secara spesifik pada local repository (tanpa `--global`/`--system`) akan mendapat prioritas lebih besar. Konfigurasi yang tersimpan pada home directory (dengan parameter `--global`) akan diterapkan apabila tidak ditemukan konfigurasi pada local repository. Konfigurasi pada system akan digunakan apabila tidak ditemukan konfigurasi pada local repo maupun user home directory. Perbedaan `--global` dengan `--system` adalah penggunaan konfigurasi pada `--system` bisa lintas user.

### Menggunakan Git
1. Mendeklarasikan local git repository <br>
` git init ` <br>
Perintah tersebut digunakan untuk membuat working directory menjadi local repository untuk git. Umumnya akan dibuat folder `.git/` dan akan terdapat konfigurasi git di local repository. 

1. Menyalin dari remote repository <br>
` git clone https://github.com/<username>/<repository>.git ` <br>
Perintah tersebut digunakan untuk menyalin remote repository ke working directory. Pada working directory akan dibuat folder baru yang berisi seluruh file yang ada di remote repository. Ubah `<username>` menjadi username yang akan digunakan dan `<repository>` menjadi nama repo yang akan disalin.

1. Menambahkan file-file ke stagging <br>
` git add * ` <br>
Perintah tersebut digunakan untuk menambahkan semua file di working directory ke stage. Seluruh file akan di-index sesuai dengan hirarki file. Pada tahap inilah kita memastikan bahwa kode yang sudah diperbaharui siap dipindahkan ke HEAD. Parameter `*` dapat diubah menjadi nama file atau nama folder agar lebih spesifik ke dokumen tertentu saja. 

1. Melakukan komit ke HEAD <br>
` git commit -m "<komentar>" ` <br>
Komit ke HEAD digunakan untuk menandai bahwa file yang sudah berada di tahap stagging siap di-push ke remote repository. Perintah komit juga akan memberikan komentar pada proses editing terakhir sekaligus untuk memberikan log pada git tentang adanya perubahan terbaru.


1. Mengatur remote repository <br>
` git remote add origin <server> ` <br>
Perintah tersebut digunakan untuk memberitahu git-client tentang informasi remote repository tujuan yang akan di-update. Remote repository tersebut bisa saja sama dengan remote repository yang digunakan saat proses clone (salin) repo. Gunakan perintah di atas dengan mengganti parameter `<server>` dengan alamat remote repository seperti yang digunakan pada proses clone/salin.

1. Membuat cabang (branch) baru <br>
` git checkout -b <branch> ` <br>
Branch pada Git memiliki fungsi utama memisahkan source code yang sudah stable release dengan source code yang masih dikembangkan. Dalam hal ini Git memudahkan programmer dalam mengembangkan metode ataupun fitur baru yang bisa saja dalam proses pengembangannya menyimpan baris perintah yang bertentangan dengan baris perintah yang sudah ada. Pertentangan tersebut dapat menyebabkan aplikasi yang sudah stable justru malah crash. Dengan memanfaatkan branch, pengembangan aplikasi bisa terus berjalan dan source code yang stable tidak akan terpengaruh.
Perintah `checkout` akan membuat cabang baru dengan nama <branch> (dapat diganti dengan nama lain) kemudian sekaligus mengaktifkan branch. Ketika sudah berada pada branch baru, seluruh operasi git akan disimpan dalam branch tersebut.

1. Kembali ke master branch <br>
` git checkout master ` <br>
Branch master dapat dikatakan sebagai master-flow dimana source code stable tersimpan. Umumnya yang berada di branch ini bukanlah aplikasi yang masih dikembangkan melainkan aplikasi yang sudah release dan sudah digunakan.

1. Menggabungkan perubahan dari cabang lain <br>
` git merge <branch> ` <br>
Perintah tersebut digunakan untuk menggabungkan <branch> (diisi dengan nama branch) dengan branch aktif saat ini. Kita bisa saja menggabungkan 2 branch atau bisa langsung menggabungkan ke master. Proses `merge` tersebut akan secara otomatis menggabungkan 2 branch yang bisa juga justru mengakibatkan konflik. Untuk mencegah konflik, kita bisa menggunakan perintah `git diff <cabang_asal> <cabang_tujuan>` lalu melakukan `git add` secara spesifik pada file yang mengalami perubahan.

1. Memeriksa perubahan yang sudah dilakukan <br>
` git status ` <br>
Perintah tersebut digunakan untuk memeriksa adakah file yang sudah dimodifikasi. Apabila ada file yang dimodifikasi, apakah file tersebut sudah berada di stagging area. Tersedia juga petunjuk untuk melakukan operasi add/reset stagging/HEAD. Dengan perintah ini, kita dapat memastikan bahwa perubahan yang dilakukan memang sesuai dengan yang direncanakan, tidak ada perubahan lain yang tidak diharapkan.

1. Mengirimkan perubahan ke remote repository <br>
` git push origin <nama_cabang> ` <br>
Perintah tersebut digunakan untuk menyelaraskan local repository dengan remote repository. Umumnya kita menggunakan `master` sebagai pengganti `<nama cabang>`, namun setelah mempertimbangkan bahwa push ke master bisa menyebabkan konflik, kita dapat menentukan branch baru. Branch baru dapat diakses oleh pihak lain _hanya_ ketika branch tersebut sudah di-push ke remote repository.


