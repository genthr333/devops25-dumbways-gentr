Day 1 — Instalasi Ubuntu Server

**Ringkasan:** Instalasi Ubuntu Server di VirtualBox (RAM 2GB, 2 CPU, disk 20GB).

---

## Langkah 1 — Buat VM
**Deskripsi singkat:** Buat VM baru di VirtualBox.
  
**Screenshot:**  
<p align="center">
  <img src="step1.png" width="300" alt="Buat VM">
  <img src="step2.png" width="300" alt="Buat VM">
  <img src="step3.png" width="300" alt="Buat VM">
</p>
**Keterangan:** Masukan nama VM, lalu pastikan VM folder sama, dan pilih ISO image. setelah itu uncheck box unattended installation

---

## Langkah 2 — Atur RAM & CPU
**Deskripsi singkat:** Menyesuaikan resource VM.
  
**Screenshot:**  
<p align="center">
  <img src="step4.png" width="300" alt="Buat VM">
  <img src="step5.png" width="300" alt="Buat VM">
</p>
**Keterangan:** Tentukan resource VM minimal memory 2 GB dan Core yang digunakan 2, saya kemarin gagal diproses instalasi jika hanya menggunakan memory sebesar 1GB dan 1 core. lalu jika sudah klik next dan finish.

---

## Langkah 3 — Run Ubuntu
**Deskripsi singkat:** Run ubuntu untuk melanjutkan prosess instalasi.
  
**Screenshot:**  
<p align="center">
  <img src="step6.png" width="300" alt="Buat VM">
  <img src="step7.png" width="300" alt="Buat VM">
  <img src="step8.png" width="300" alt="Buat VM">
  <img src="step9.png" width="300" alt="Buat VM">
  <img src="step10.png" width="300" alt="Buat VM">
  <img src="step11.png" width="300" alt="Buat VM">
  <img src="step12.png" width="300" alt="Buat VM">
</p>
**Keterangan:** Klik Tombol Start pada menu Vitrualbox untuk run ubuntu, ketika sudah running tekan enter pada text try or install ubuntu server, tunggu beberapa saat lalu pilih Bahasa yang akan digunakan, jika muncul menu installer update available pilih yang continue without update, klik enter pada konfigurasi keyboard default, dan pilih ubuntu server pada menu type installation

---

## Langkah 4 — Konfigurasi IPv4
**Deskripsi singkat:** Menyesuaikan IP address yang ada di ubuntu dan di device kita.
  
**Screenshot:**  
<p align="center">
  <img src="step13.png" width="300" alt="Buat VM">
  <img src="step14.png" width="300" alt="Buat VM">
  <img src="step14b.png" width="300" alt="Buat VM">
</p>
**Keterangan:** Pilih IPv4 method yang manual, lalu masukan IP addres.Lihat IP config pada menu cmd dan gunakan IP address sesuai dengan yang ada di menu cmd, pastikan IP address tidaka sama. enter lalu tunggu beberapa saat kalua muncul pilihan continue without connection maka coba config ulang, jika muncul pilihan done maka ubuntu sudah bisa terhubung ke internet. lalu pada bagian proxy kita enter saja, dan bagian ubuntu mirror archive kita enter saja.

---

## Langkah 5 — Konfigurasi Storage
**Deskripsi singkat:** Menyesuaikan storage.
  
**Screenshot:**  
<p align="center">
  <img src="step15.png" width="300" alt="Buat VM">
  <img src="step15b.png" width="300" alt="Buat VM">
  <img src="step16.png" width="300" alt="Buat VM">
  <img src="step16b.png" width="300" alt="Buat VM">
  <img src="step17d.png" width="300" alt="Buat VM">
</p>
**Keterangan:** Pada menu storage configuration pilih custome storage layout lalu continue. Di sini kita akan membuat partisi sebesar 7GB untuk storage dengan format new extension. Lalu sisa free space kita manfaatkan sebagai memory candangan dengan format swap sebesar 3.1GB. lalu klik done dan continue

---

## Langkah 6 — Konfigurasi Storage
**Deskripsi singkat:** Menyesuaikan storage.
  
**Screenshot:**  
<p align="center">
  <img src="step15.png" width="300" alt="Buat VM">
  <img src="step15b.png" width="300" alt="Buat VM">
  <img src="step16.png" width="300" alt="Buat VM">
  <img src="step16b.png" width="300" alt="Buat VM">
  <img src="step17d.png" width="300" alt="Buat VM">
</p>
**Keterangan:** Pada menu storage configuration pilih custome storage layout lalu continue. Di sini kita akan membuat partisi sebesar 7GB untuk storage dengan format new extension. Lalu sisa free space kita manfaatkan sebagai memory candangan dengan format swap sebesar 3.1GB. lalu klik done dan continue.

---

## Langkah 7 — Melanjutkan instalasi 
**Deskripsi singkat:** Melanjutkan instalasi secara polos.
  
**Screenshot:**  
<p align="center">
  <img src="step17.png" width="300" alt="Buat VM">
  <img src="step17b.png" width="300" alt="Buat VM">
  <img src="step17c.png" width="300" alt="Buat VM">
  <img src="step18.png" width="300" alt="Buat VM">
  <img src="step18a.png" width="300" alt="Buat VM">
</p>
**Keterangan:** Pada menu upgrade UbuntuPro, SSH configuration, featured server snaps kita enter saja jecuali jika ingin langsung menginstall aplikasi maka pada menu server snaps bisa dipilih aplikasi yang mau diinstall. jika sudah maka kita sudah mengintsall ubuntu di virtualbox secara polos. tunggu proses instalasi.

---

## Langkah 8 — Login dan ping
**Deskripsi singkat:** melakukan login dan test ping.
  
**Screenshot:**  
<p align="center">
  <img src="step19a.png" width="300" alt="Buat VM">
  <img src="step19b.png" width="300" alt="Buat VM">
</p>
**Keterangan:** Jika sudah bisa ngetik atau muncul menu login maka kita bisa coba login dan jika sudah berhasil masuk kita bisa mencoba melakukan ping ke google.com atau ke 8.8.8.8

---