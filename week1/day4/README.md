## Day 4 Version control system


## 1. Penjelasan git


Git adalah version control system alat untuk mengatur dan mengamankan workflow development, biar setiap perubahan:

  tercatat

  bisa dicek versi sebelumnya

  bisa dikembangkan paralel

  bisa di-merge tanpa ribet


## 2. Repo Dumbways-25


Langkah 1


<img width="1110" height="626" alt="step1" src="https://github.com/user-attachments/assets/96f6135d-6198-4deb-8c9c-1049e280cb52" />


Buat folder Dumbways-batch-25


Langkah 2


<img width="1112" height="624" alt="step2" src="https://github.com/user-attachments/assets/539957a0-5bb7-4c52-bf11-99cc0d96c372" />


Buat 3 file dengan isi README.md atau apapun yang penting tidak kosong


Langkah 3


<img width="1113" height="623" alt="step3" src="https://github.com/user-attachments/assets/cd6c5316-705d-489a-b3b0-f6c49866afee" />


jalankan git add . untuk add 3 file yang baru dibuat lalu check dengan melihat di git status


Langkah 4


<img width="1111" height="623" alt="step4" src="https://github.com/user-attachments/assets/ec9f1549-6619-4bfa-a721-3f570b77deee" />


Jalankan git commit -m "(deskripsi)"


Langkah 5


<img width="1111" height="620" alt="step5" src="https://github.com/user-attachments/assets/a7f0a6e5-e432-43b0-8a35-d299e535c4c6" />


Lalu jalankan command git remote sesuaikan dengan repository. pastikan publickey bisa diakses jika tidak jalankan eval "$(ssh-agent -s)" lalu test menggunakan ssh -T git@github.com



langkah 6


<img width="1113" height="193" alt="step6" src="https://github.com/user-attachments/assets/b636ba25-a45d-4a70-8fe7-59c80f978b69" />


Disini saya bisa mengakses dan melihat branch yang ada di repo


Langkah 7


<img width="1111" height="400" alt="step7" src="https://github.com/user-attachments/assets/8c4bc93e-7c9b-478e-8d97-7b828e94e101" />


dan disini saya mencoba melakukan fetch,pull, dan berganti branch


Langkah 8


<img width="1104" height="177" alt="step8" src="https://github.com/user-attachments/assets/40c9deef-af10-41e3-97c2-bcbffc321655" />


Modif isi file menggunakan nano atau semacamnya lalu add dan commit setelah itu bisa menjalankan command git diff HEAD~1 HEAD akan mencari perubahan text pada ubuntu
