# Ansible


## 1 install WSL, dan setup


### Langkah 1


<p alig"center"> <img src="1.PNG" widthn=="700" alt="command"> </p>


Untuk mengerjakan tugas ansible saya menggunakan wsl untuk melakukan setup ansible playbook dan menjalankan ansible. intsall WSL di pc kalian dengan command wsl --install lalu wsl.exe --install --no-distribution. kemudian jika sudah terinstall kita akan menginstall distro ubuntu dengan menjalankan wsl --install -d ubuntu-22.04(masukan versi yang tersedia).


<p align="center">
  <img src="2.PNG" width="48%" />
  <img src="3.png" width="48%" />
</p>


lalu tunggu proses instalasi distro selsai, dan setelah selesai kita bisa menjalankan wsl dengan command wsl di terminal.


### Langkah 2


lalu kita akan menambahkan modul venv agar ansible terisolasi(tidak mengganggu sistem). masuk kedalam home di wsl lalu jalankan sudo apt update dan sudo install python3-venv -y. jika proses instalasi sudah selesai kita akan lanjut membuat folder project untuk menjalankan ansible mkdir (nama dir), masuk kedalam directory dan jalankan python3 -m venv ansible-env. untuk masuk kedalam venv kita bisa menggunakan command ini source ansible-env/bin/activate dan untuk keluar dari venv kita bisa deactivate. ansible hanya bisa dijalankan di dalam venv.


<p alig"center"> <img src="4.png" widthn=="700" alt="command"> </p>


## 2 set up ansible


### langkah 1 


kita akan membuat file ansible.cfg, invetory, dan directory group_vars yang berisi file app.yaml dan gateway.yaml.


<p alig"center"> <img src="5.png" widthn=="700" alt="command"> </p>


file ansible.cfg akan memberitahu secara otomatis untuk menggunakan file yang bernama inventory sebagai daftar host target.


<p alig"center"> <img src="8.png" widthn=="700" alt="command"> </p>


pada file ini akan mendefinisikan target host untuk menjalankan playbook, di mana di bagi menjadi 3 yaitu app, gateway, dan monitoring. di sini saya hanya menggunakan 2 server jadi monitoring target ke app server.


<p align="center">
  <img src="6.PNG" width="48%" />
  <img src="7.png" width="48%" />
</p>


dir group_vars berfungsi untuk mencocokan nama file di dalam folder ini dengan nama group di inventory, untuk menentukan variable mana yang akan digunakan.


### langkah 2


<p alig"center"> <img src="9.png" widthn=="700" alt="command"> </p>


setelah selsai dengan setup kita akan melakukan test membuat playbook. playbook yang pertama berfungsi untuk pembuat user baru pada server yang kit target, dan kita akan memberikan akses ssh public key dari wsl lalu di salin ke dalam authorized_key milik user1 di server target.


## install docker


### langkah 1


<p align="center">
  <img src="10.png" width="48%" />
  <img src="11.png" width="48%" />
</p>


selanjutnya kita akan install docker. pada environment ini semua aplikasi akan running di atas docker. add docker repo untuk menambahkan repo resmi docker ke dalam sistem ubuntu menggunakan codename jammy. install docker engine menginstall paket docker (docker-ce, cli, containerd), enable & start docker untuk mengaktifkan service docker agar langsung running dadn otomatis nyala walaupun server direboot. add user to docker group memasukan user1 ke docker.


### langkah 2


kita akan coba menjalankan frontend di atas docker


<p align="center">
  <img src="12.png" width="48%" />
  <img src="13.png" width="48%" />
</p>


ansible akan menggunakan module git untuk clone rerpo dari githuhb ke folder tujuan yaitu app_dir. pada parameter force: yes ini agar memastikan jika ada perubahan lokal yang konflik, code dari remote tetap diutamakan. build docker image menggunakan modul community.docker.docker_image untuk melakukan proses build berdasarkan dockerfile, hasilnya di tulis dalam variable image_name. restart_policy: alwawys untuk membuat container nyala ketika server di reboot.


## install node exporter dan prometheus


### langkah 1


<p alig"center"> <img src="14.png" widthn=="700" alt="command"> </p>


node exporter berfungsi sebagai jembatan yang mengubah data  hardware seperti cpu, ram, disk, network menjadi format metrik yang bisa di baca oleh prometheus. image prom/node-exporter ini akan menggunakan imager resmi dari ekosistem prometheus. lalu untuk check metricnya bisa curl http://103.103.23.200:9100/metrics | head -n 20


### langkah 2


<p align="center">
  <img src="15.png" width="48%" />
  <img src="16.png" width="48%" />
</p>


kedua playbook ini (atau gabungan task ini) bertujuan untuk mendefinisikan bagaimana Prometheus berjalan dan target mana saja yang harus dipantau.
volumes /opt/prometheus:/etc/prometheus ini adalah Bind Mount. Ansible memetakan folder di host /opt/prometheus ke dalam container /etc/prometheus. supaya file konfigurasi yang kita buat di server tetap tersimpan meskipun container dihapus atau direstart.
Command --config.file akan memberitahu prometheus untuk membaca aturan monitoring dari file konfigurasi yang telah kita petakan di dalam volume.
scrape_interval: 15s: Prometheus akan mengambil data metrik dari server setiap 15 detik sekali.
scrape_configs: Bagian ini mendefinisikan target monitoring.


<p alig"center"> <img src="14.png" widthn=="700" alt="command"> </p>


pastikan status target up.


## install grafana


### langkah 1


<p alig"center"> <img src="14.png" widthn=="700" alt="command"> </p>


sama seperti instalasi sebelumnya ansible akan menarik image docker grafana/grafana, lalu run di port 3001.


<p alig"center"> <img src="14.png" widthn=="700" alt="command"> </p>


login menggunakan admin.


<p alig"center"> <img src="14.png" widthn=="700" alt="command"> </p>


connect data source dari prometheus ke dalam grafana dengan memilih prometheus.


<p alig"center"> <img src="14.png" widthn=="700" alt="command"> </p>


lalu buat dashboard di dalam grafana untuk monitoring, bisa juga import template.
