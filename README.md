# Tiktok Clone using Next3, Vue3, Laravel API
<p align="center"><a href="https://laravel.com" target="_blank"><img src="https://cdn.dribbble.com/users/1636225/screenshots/15155331/tiktok-clone-1600x1200.png" width="400" alt="Laravel Logo"></a></p>

Proyek ini adalah klon TikTok yang dikembangkan menggunakan Nuxt 3 untuk front-end dan Laravel API untuk back-end. Proyek ini memungkinkan pengguna untuk membuat, melihat, dan berinteraksi dengan video pendek seperti di platform TikTok. Proyek ini dibangun berdasarkan tutorial di YouTube dengan penyesuaian dan tambahan fitur untuk memperluas fungsionalitas.

## Fitur 
### Bawaan Tutorial

1. Beranda
2. Upload Video
3. Like & Comment
4. Profile User
5. Responsive
6. Search

### Tambahan/Modifikasi
1. Search Filter
2. Dark Mode
3. Popup Notification

## Installasi

1. Clone Repository
```bash
# Clone repository ini
https://github.com/ahzi8100/tiktok-clone.git
cd tiktok-clone
```
2. Install Dependensi
```bash
# Instal dependensi untuk Nuxt 3 (frontend)
npm install

# Instal dependensi untuk Laravel (backend)
composer install
```
3. Konfigurasi Database
- Buat file .env di root Laravel API, lalu tambahkan konfigurasi database dan token API.
- Untuk Nuxt 3, tambahkan file .env untuk URL API back-end.
4. Migrasi Database
```bash
php artisan migrate
```
5. Jalankan server
```bash
# Jalankan backend Laravel
php artisan serve

# Jalankan frontend Nuxt 3
npm run dev
```
## Teknologi yang Digunakan
1. Nuxt 3: Framework modern untuk pengembangan front-end.
2. Vue 3: Library JavaScript reaktif untuk antarmuka pengguna.
3. Tailwind CSS: Framework CSS untuk styling.
4. Laravel API: Framework PHP untuk pengembangan back-end.
5. Pinia: State management yang ringan untuk Vue.
6. Axios: Library untuk melakukan request HTTP ke API.
7. JavaScript: Bahasa pemrograman utama untuk pengembangan front-end.
## Hal yang dipelajari dari Projek ini
1. Pengembangan Front-End dengan Nuxt 3 dan Vue 3:
   - Membuat antarmuka pengguna yang dinamis dan reaktif.
   - Implementasi navigasi halaman dengan SSR (Server-Side Rendering) atau CSR (Client-Side Rendering).

2. State Management dengan Pinia:
   - Mengelola data global seperti autentikasi pengguna atau informasi video.

3. Integrasi API dengan Laravel:
   - Membuat API RESTful untuk operasi CRUD (Create, Read, Update, Delete).
   - Implementasi autentikasi berbasis token.

4. Menggunakan Axios untuk HTTP Requests:
   - Mengirim dan menerima data antara front-end dan back-end.

5. Styling dengan Tailwind CSS:
   - Membangun desain responsif dan modern dengan utilities Tailwind.

6. Deployment:
   - Memahami cara meng-host aplikasi front-end dan back-end secara live.

7. Pola Kerja Aplikasi Media Sosial:
   - Fitur seperti unggahan video, sistem komentar, dan suka.
   - Optimalisasi pengalaman pengguna dengan pemutaran video otomatis dan desain responsif.

8. Debugging dan Optimisasi Kode:
   - Mengatasi tantangan saat mengintegrasikan teknologi dan meningkatkan performa aplikasi.

9. Pengenalan Ekosistem Teknologi Fullstack:
    - Menggabungkan framework front-end dan back-end dalam satu proyek nyata. 

## Credit 
Proyek ini dikembangkan berdasarkan tutorial dari [John Weeks Dev](https://www.youtube.com/watch?v=CHSL0Btbj_o&list=PL3pX4NAc7vJvBhW5bcngX011BsaFpD-Yo&index=2) Big Thanks.
