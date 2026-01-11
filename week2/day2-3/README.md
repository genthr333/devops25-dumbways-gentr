## Day 2 CI/CD Jenkins


#1 install Jenkins dan Docker 


Langkah 1


Pada tahap pertama kita akan menginstall jenkins pada server yang terpisah dikarenakan jenkins berat.
untuk menginstall jenkins diperlukan menginstall java, menambahkan key rings repo, menambhakan repository jenkins dengan command seperti berikut.
sudo apt update, sudo apt install fontconfig, openjdk-17-jre untuk menginstall java(open jdk17)
sudo apt update, sudo apt install jenkins untuk menginstall jenkins
sudo wget -O (location key rings repo) https://pkg.jenkins.io/debian-stable/jenkins.io-2023.key untuk menambahkan keyrings
echo "deb [signed-by=/usr/share/keyrings/jenkins-keyring.asc] https://pkg.jenkins.io/debian-stable binary/" | sudo tee /etc/apt/sources.list.d/jenkins.list > /dev/null untuk menambahkan repository jenkins
dan jalankan sudo systemctl start jenkins untuk menjalankan jenkins. jenkins bisa diakses melalui ip dan port server.


Langkah 2


pada tahap kedua kita akan menginstall docker di app server denga command seperti berikut.
sudo apt-get update untuk update package index
sudo apt-get install ca-certificates curl gnupg untuk install dependesi awal
sudo install -m 0755 -d /etc/apt/keyrings curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /etc/apt/keyrings/docker.gpg untuk menambahkan gpg key
echo "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.gpg] https://download.docker.com/linux/ubuntu $(. /etc/os-release && echo "$VERSION_CODENAME") stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
sudo apt-get update, sudo apt-get install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin untuk install docker


#2 Setup docker files


langkah 1


<p align="center">
  <img src="8.png" width="48%" />
  <img src="3.png" width="48%" />
</p>


docker files backend ditambahakn pada dir backend dan docker files ditambahkan pada dir frontend. pada docker files frotnend kita tambhakan sequelize-cli untuk sequelize database.


Langkah 2


<p align="center"> <img src="7.png" width="700" alt="command"> </p>


edit file config.json pada dir backend sesuaikan username, pasword, dan database sesuai dengan database yang sudah diinstall. lalu pastikan host sesuai dengan ip dimana database terinstall


Langkah 3


<p align="center"> <img src="1.png" width="700" alt="command"> </p>


buat file docker-compose di luar dari dir frontend dan backend. masukan backend, frontend, dan database ke dalam service supaya run di atas docker. pastikan context seusai dengan location docker file dan pada database password dan nama data base disesuaikan sama. lalu pastikan semua bisa diakses telebih dahulu dan backend terhubung dengan database.


#3 setup jenkins file


Langkah 1


<p align="center">
  <img src="4.png" width="32%" />
  <img src="5.png" width="32%" />
  <img src="6.png" width="32%" />
</p>


buat jenkins file di dalam dir backend. lalu di dalam stages tambahkan stage db migrate.


Langkah 2


<p align="center">
  <img src="9.png" width="48%" />
  <img src="10.png" width="48%" />
</p>


buat jenkinsfile di dalam dir frontend


#4 setup reverse proxy


Langkah 1


buat domain untuk jenkins, frontend, dan backend menggunakan cloudflare.


Langkah 2


<p align="center">
  <img src="12.png" width="32%" />
  <img src="13.png" width="32%" />
  <img src="14.png" width="32%" />
</p>


buat file reverse proxy untuk jenkins, backend, dan frontend. lalu gunakan ssl, dan pada bagian location tambahkan proxy_set_header X-Forwarded-Proto https;


#5 configurasi jenkins


Langkah 1


<p align="center">
  <img src="15.png" width="48%" />
  <img src="19.png" width="48%" />
</p>


install beberapa plugins yangdi perlukan setelah register. masuk ke configuration backend, lalu pada menu triggers pilih github hok triggers, ambil webhook pada menu setting github.


Langkah 2


<p align="center">
  <img src="15.png" width="48%" />
  <img src="16.png" width="48%" />
</p>


tambahakan url repo github. lalu coba lakukan beberapa perubaha hingga tmapilan dashboard hasilnya seperti ini 


<p align="center"> <img src="20.png" width="700" alt="command"> </p>
