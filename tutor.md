Setup Kopdes — Panduan gae (ServBay) 
#lanang kok windows + servby (ambrol_ambrol)


1. Instal ServBay (lek uwes gak usah install)


2. Nyalakan layanan yang dibutuhkan

Buka ServBay, nyalakan (toggle ON):

PHP — (gaeo seng  8.4) 
MariaDB
Redis
Nginx

Pastikan semua statusnya menjadi hijau/"Running".koyok lampu lalu lintas 

3. Aktifkan estensi php lek gak ngerti delok youtube su

 aktifkan semua ini:

pdo_mysql
mbstring
curl
fileinfo
xml
zip
intl
pcntl
redis

, ojok sampe beda ya bosss engko malah ruwet maneh ngae servbay lek pake docker seh sek aman ada abang wkwkkw

4. Cek Composer & Node.js

Biasanya sudah ada di ServBay (cek menu Packages/Tools). Kalau belum ada:

Komposer: getcomposer.org
Node.js (versi LTS): nodejs.org
5. Proyek kloning

Buka terminal (Command Prompt / PowerShell / Git Bash):

pesta
git clone https://github.com/madanyifkar56-tech/kopdes.git
cd kopdes
lek notfound dm boss berarti belum di undang
6. Instal dependensi
pesta
install sek sabar kambek ngopi (adu pitek sek )
composer install
npm install

Tunggu sampai selesai

7. Bikin file .envsendiri
pesta
copy .env.example .env
php artisan key:generate

(kalau pakai Git Bash, ganti copyjadi cp)

8. Edit.env

sesuaikan dengan servbay mu (lek raiso banting ae leptop e)

contoh :
DB_CONNECTION=mysql
DB_HOST=127.0.0.1
DB_PORT=3306
DB_DATABASE=kopdes
DB_USERNAME=root
DB_PASSWORD=

podokno su ben gak eror DB_USERNAME/ DB_PASSWORDkalau default ServBay kamu berbeda. Cek database ServBay terserahmu.

Kalau Redis nyala normal, biarkan default SESSION_DRIVER=redis, CACHE_STORE=redis, QUEUE_CONNECTION=redis, REDIS_HOST=127.0.0.1, REDIS_PORT=6379.

Kalau Redis bermasalah, ganti sek sementara ya boss

SESSION_DRIVER=file
CACHE_STORE=file
QUEUE_CONNECTION=sync
9. Buat basis data
lek iki tanya koko ; aku kurang paham biasane ngae php my admin soale aku pakai docker ya boss bukan servbay ruwet koyok boti
10. Migrasi database
pesta
php artisan migrate:fresh --seed

Kalau error koneksi database, banting aja leptop nya (cek mariadb /mysql tapi pk devit wajib maria db jadi  mariadb pokok kudu aktif)
11. Bangun aset & jalankan
pesta
npm run build
composer run dev
12. Buka browser
http://localhost:8000

sampe muncul laravel 
Kalau Ada Error
could not find driver	pdo_mysqlbelum aktif	Cek maneh  PHP di ServBay
Gagal konek database	.envsalah / MySQL belum menyala	Cek DB_HOST, DB_USERNAME, DB_PASSWORD, pastikan MySQL berjalan
Halaman kosong putih	Kesalahan tersembunyi	Set APP_DEBUG=truedi .envsementara buat lihat error-nya
Halaman tanpa CSS	Aset belum dibangun	Itunpm run build
Redis gagal	Redis belum aktif	Pakai file/ syncsementara  (tapi iki agak ruwet bosss) tanya koko koko raiso tanya ai
(lihat langkah 8) lek nga kenek banting ae leptop eee
