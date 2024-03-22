Nama: Muhammad Rafi Zia Ulhaq<br>
NPM: 2206814551<br>
Kelas: Pemrograman Lanjut B<br>

# Module 6

### Commit 1 Reflection
Method `handle_connection` adalah sebuah method untuk menangani koneksi TCP. Method ini menerima parameter stream yang merupakan objek TcpStream. Tujuan utama dari method `handle_connection` adalah untuk membaca data dari stream dengan menggunakan `BufReader`, mengolahnya, meresponsnya, serta menampilkan request HTTP yang diterima menggunakan `println!`.

### Commit 2 Reflection
Method `handle_connection` masih melakukan hal yang sama seperti sebelumnya, namun ditambah dengan mengirimkan sebuah response HTTP dengan cara membaca dan menampilkan konten dari file `hello.html` menggunakan `fs::read_to_string`. Panjang konten `(contents.len())` dihitung untuk dijadikan bagian dari header `response`. Response HTTP dikirimkan dengan menggunakan format yang sesuai dengan protokol HTTP, termasuk status line, header "Content-Length", dan konten dari file `hello.html`. Menggunakan `write_all()`, response yang telah diformat dikirimkan kembali kepada browser melalui `stream`.
![alt text](https://github.com/rafizia/advprog-modul6/blob/master/src/image/commit2.png?raw=true)