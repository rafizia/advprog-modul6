Nama: Muhammad Rafi Zia Ulhaq<br>
NPM: 2206814551<br>
Kelas: Pemrograman Lanjut B<br>

# Module 6

### Commit 1 Reflection
Method `handle_connection` adalah sebuah method untuk menangani koneksi TCP. Method ini menerima parameter stream yang merupakan objek TcpStream. Tujuan utama dari method `handle_connection` adalah untuk membaca data dari stream dengan menggunakan `BufReader`, mengolahnya, meresponsnya, serta menampilkan request HTTP yang diterima menggunakan `println!`.

### Commit 2 Reflection
Method `handle_connection` masih melakukan hal yang sama seperti sebelumnya, namun ditambah dengan mengirimkan sebuah response HTTP dengan cara membaca dan menampilkan konten dari file `hello.html` menggunakan `fs::read_to_string`. Panjang konten `(contents.len())` dihitung untuk dijadikan bagian dari header `response`. Response HTTP dikirimkan dengan menggunakan format yang sesuai dengan protokol HTTP, termasuk status line, header "Content-Length", dan konten dari file `hello.html`. Menggunakan `write_all()`, response yang telah diformat dikirimkan kembali kepada browser melalui `stream`.
![alt text](https://github.com/rafizia/advprog-modul6/blob/master/src/image/commit2.png?raw=true)

### Commit 3 Reflection
Kode tersebut memerlukan *refactoring* karena terdapat duplikasi pada blok if dan else, keduanya sama-sama membaca file dan menulis konten ke `stream`. Perbedaannya hanya pada `status_line` dan `filename`. Refactoring dilakukan dengan menarik perbedaan-perbedaan tersebut ke dalam baris if dan else terpisah dan memasukkan nilai `status_line` dan `filename` ke dalam sebuah variabel. Kemudian variabel tersebut dapat digunakan untuk membaca file dan menulis respons. Maka blok if dan else hanya mengembalikan nilai yang sesuai untuk `status_line` dan `filename` dalam sebuah tuple. Kemudian kita dapat menggunakan destrukturisasi untuk menetapkan dua nilai tersebut ke `status_line` dan `filename` menggunakan pattern pada `let` *statement*.
![alt text](https://github.com/rafizia/advprog-modul6/blob/master/src/image/commit3.png?raw=true)

### Commit 4 Reflection
Pada kode tersebut if statement kedua berfungsi untuk menerima request ke `/sleep`. Ketika request tersebut diterima, server akan sleep selama 10 detik sebelum merender halaman HTML yang berhasil. Cara ini dapat menjadi cara untuk menguji bagaimana server menangani delay atau untuk mensimulasikan kondisi jaringan yang lambat.

### Commit 5 Reflection
ThreadPool adalah kumpulan dari beberapa thread yang tersedia untuk mengeksekusi tugas-tugas secara paralel. Saat program menerima tugas baru, program akan menugaskan salah satu thread di threadpool untuk mengerjakan tugas tersebut. Thread yang tersisa tersedia untuk menangani tugas lain yang masuk saat thread pertama memproses suatu pekerjaan. Saat thread pertama selesai memproses tugasnya, thread tersebut dikembalikan ke kumpulan thread yang menganggur dan siap untuk menangani tugas baru. Hal ini dapat meningkatkan efisiensi dan kinerja aplikasi, sehingga dapat meningkatkan throughput dari server.