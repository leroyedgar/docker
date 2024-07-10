mkdir website-profil

cd website-profil

nano index.html
  <!DOCTYPE html>
  <html lang="en">
  <head>
      <meta charset="UTF-8">
      <meta name="viewport" content="width=device-width, initial-scale=1.0">
      <title>Profil</title>
  </head>
  <body>
      <h1>Profil</h1>
      <img src="foto.jpg" alt="Foto Profil" style="width:200px;">
  </body>
  </html>

nano Dockerfile
  FROM nginx:latest
  COPY . /usr/share/nginx/html
  EXPOSE 80

wget -O ~/website-profil/foto.jpg "https://drive.google.com/uc?export=download&id=1-i4m92WcoUtCnYNuVMUTrJ2oeY5KGL6T"

docker build -t website-profil .

cd ~

docker network create my-leroy-network

docker run -d --name website-profil --network my-leroy-network -p 8081:80 website-profil


mkdir website-Utama

cd website-utama

nano index.html
  <!DOCTYPE html>
  <html lang="en">
  <head>
      <meta charset="UTF-8">
      <title>Halaman Utama</title>
  </head>
  <body>
      <h1>Data Diri</h1>
      <p>Nama Lengkap: Leroy Edgar</p>
      <p>NIM: 215610068</p>
      <p>Program Studi: Sistem Informasi</p>
      <p>Hobi: Bermusik dan Bermain Game</p>
      <a href="https://16373497-0b2e-40a8-abd8-a9583a02935f-10-244-6-198-8081.papa.r.killercoda.com/">Profil</a>
  </body>
  </html>

nano Dockerfile
  FROM nginx:latest
  COPY . /usr/share/nginx/html
  EXPOSE 80

docker build -t website-utama .

docker run -d --name website-utama --network my-leroy-network -p 8080:80 website-utama










