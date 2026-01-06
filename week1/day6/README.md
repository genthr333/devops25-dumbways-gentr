## Day 6 Web Server & Load balancing


##1. Diagram Web serever menggunakan reverse proxy


<img width="391" height="641" alt="diagram1" src="https://github.com/user-attachments/assets/b3a789bf-d62d-49e8-8686-91809f63c01c" />


Struktur ini menggunakan Nginx sebagai reverse proxy dan Aplikasi berjalan di dua IP yang berbeda. 
Arsitektur ini membuat semua request dari client diarahkan dulu ke Nginx sebelum diteruskan ke aplikasi dan Nginx akan mendistribusikan traffic ke dua server tersebut (load balancing).


##2. Deploy wayshub dengan reverse proxy dan menggunakan domain sesuai nama


Langkah 1


<img width="1118" height="618" alt="step0" src="https://github.com/user-attachments/assets/59b7c5dd-9f4b-4362-aeba-14f1cb98910f" />


Pastikan web server wayshub sudah dirun terlebih dahulu. Lalu akses ubuntu dengan tab baru di terminal.


Langkah 2


<img width="920" height="610" alt="step1" src="https://github.com/user-attachments/assets/1c9d857b-f041-44b0-a60c-97cfe1fde553" />


Cari file hosts yang berada di C\Windows\System32\drivers\etc. Jika sudah ketemu tambahkan ip address ubuntu kita dan nama domain yang akan kita gunakan.


Langkah 3


<img width="1112" height="606" alt="step2" src="https://github.com/user-attachments/assets/1040d42d-4b96-49a6-9352-f522e1ea37a3" />


Pastikan package sudah up to date. Lalu install nginx, jika sudah makan jalankan command sudo systemctl status nginx, pastikan active(running).


Langkah 4


<img width="1106" height="617" alt="step3" src="https://github.com/user-attachments/assets/0c1384bd-e6a5-447e-80f1-2e3224801dae" />


Allow port 80


Langkah 5


<img width="1111" height="619" alt="step4" src="https://github.com/user-attachments/assets/545ae784-9cf3-40e0-b4ca-2a9553b25f17" />


Masuk kedalam folder /etc/nginx. lalu masuk kedalam folder sites-enabled


Langkah 6


<img width="1114" height="621" alt="step5(1)" src="https://github.com/user-attachments/assets/7ff5ecfe-0b15-46e7-8f93-061034231609" />


Buat file percobaan, dan masukan snippet code pastikan server name sesuai dan masukan dua ip address


Langkah 7


<img width="1117" height="624" alt="step6" src="https://github.com/user-attachments/assets/016e2b50-c30f-4409-9672-08ed7773bfd9" />


masukan command sudo nginx -t, di situ akan diperlihatkan apa bila ada eorror dalam penulisan syntax atau tidak. Jika ok restart nginx atau reload.


Langkah 8


<img width="2557" height="1439" alt="step7(1)" src="https://github.com/user-attachments/assets/4b1432e9-efca-415b-9d09-7d72fe4d7eec" />


Jalankan nginx dengan command sudo systemctl status nginx, dan akses web melalui webserver
