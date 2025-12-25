# Implementasi Load Balancing dengan Metode Round Robin (Docker & Nginx)

Proyek ini adalah demonstrasi sederhana penerapan teknik **Load Balancing** menggunakan **Nginx** sebagai reverse proxy dan **Docker** untuk menjalankan beberapa instance server. Proyek ini mendistribusikan trafik masuk secara bergantian ke dua server yang berbeda (`server1` dan `server2`) menggunakan algoritma **Round Robin**.

## 📂 Struktur Repositori

```text
├── server1/             # Folder untuk Server Aplikasi Pertama
├── server2/             # Folder untuk Server Aplikasi Kedua
├── nginx-lb.conf        # Konfigurasi Nginx untuk Load Balancing
├── docker-compose.yml   # Konfigurasi orkestrasi container Docker
└── .gitignore           # File pengecualian Git
🚀 Teknologi yang Digunakan
Docker & Docker Compose: Untuk menjalankan lingkungan server secara terisolasi.

Nginx: Bertindak sebagai Load Balancer dan Reverse Proxy.

HTML/Web Server: Konten statis yang disajikan oleh server backend.

🛠️ Cara Menjalankan Proyek
Pastikan Anda sudah menginstal Docker dan Docker Compose di komputer Anda.

Clone Repositori ini:

Bash

git clone [https://github.com/enjeliaa/project-Load-Balancing-metode-Round-Robin.git](https://github.com/enjeliaa/project-Load-Balancing-metode-Round-Robin.git)
cd project-Load-Balancing-metode-Round-Robin
Jalankan Container: Gunakan perintah berikut untuk membangun dan menjalankan semua server (Server 1, Server 2, dan Nginx Load Balancer):

Bash

docker-compose up -d --build
Cek Status Container: Pastikan ketiga container berjalan dengan baik:

Bash

docker-compose ps
🧪 Pengujian (Testing)
Untuk melihat Load Balancing bekerja dengan metode Round Robin:

Buka browser Anda dan akses: http://localhost (atau port yang didefinisikan di docker-compose.yml, biasanya port 80 atau 8080).

Lakukan Refresh (F5) halaman berkali-kali.

Anda akan melihat konten halaman berubah bergantian antara Server 1 dan Server 2.

Request 1 -> Masuk ke Server 1

Request 2 -> Masuk ke Server 2

Request 3 -> Masuk ke Server 1

dst...

Atau menggunakan terminal:

Bash

curl http://localhost
curl http://localhost

📚 Penjelasan Teknis
Apa itu Round Robin?
Metode Round Robin adalah algoritma load balancing yang paling sederhana. Nginx akan mendistribusikan permintaan klien ke daftar server backend secara berurutan. Jika server terakhir sudah menerima permintaan, Nginx akan kembali ke server pertama.

Konfigurasi Nginx (nginx-lb.conf)
Dalam file konfigurasi ini, blok upstream mendefinisikan grup server yang akan menerima trafik:

Nginx

upstream backend_servers {
    server server1:80;  # Nama service sesuai di docker-compose.yml
    server server2:80;
}

Dibuat oleh: Enjeliaa
