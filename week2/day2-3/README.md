## Day 2 CI/CD Jenkins


##1 Set up Docker, dan Jenkins 


Langkah 1


<p align="center"> <img src="1.png" width="700" alt="command"> </p>


Pada tahap pertama kita akan menginstall jenkins pada server yang terpisah dikarenakan jenkins berat.
untuk menginstall jenkins diperlukan menginstall java, menambahkan key rings repo, menambhakan repository jenkins dengan command seperti berikut.
sudo apt update, sudo apt install fontconfig, openjdk-17-jre untuk menginstall java(open jdk17)
sudo apt update, sudo apt install jenkins untuk menginstall jenkins
sudo wget -O (location key rings repo) https://pkg.jenkins.io/debian-stable/jenkins.io-2023.key untuk menambahkan keyrings
echo "deb [signed-by=/usr/share/keyrings/jenkins-keyring.asc] https://pkg.jenkins.io/debian-stable binary/" | sudo tee /etc/apt/sources.list.d/jenkins.list > /dev/null untuk menambahkan repository jenkins
dan jalankan sudo systemctl start jenkins untuk menjalankan jenkins

Langkah 2


pada tahap kedua kita akan menginstall docker di app server denga command seperti berikut.
sudo apt-get update untuk update package index
sudo apt-get install ca-certificates curl gnupg untuk install dependesi awal
sudo install -m 0755 -d /etc/apt/keyrings curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /etc/apt/keyrings/docker.gpg untuk menambahkan gpg key
echo "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.gpg] https://download.docker.com/linux/ubuntu $(. /etc/os-release && echo "$VERSION_CODENAME") stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
sudo apt-get update, sudo apt-get install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin untuk install docker


##2 Setup docker files pada frontend dan backend


<p align="center">
  <img src="8.png" width="48%" />
  <img src="3.png" width="48%" />
</p>





Langkah 4


<img width="1106" height="617" alt="step3" src="https://github.com/user-attachments/assets/0c1384bd-e6a5-447e-80f1-2e3224801dae" />





Langkah 5


<img width="1111" height="619" alt="step4" src="https://github.com/user-attachments/assets/545ae784-9cf3-40e0-b4ca-2a9553b25f17" />





Langkah 6


<img width="1114" height="621" alt="step5(1)" src="https://github.com/user-attachments/assets/7ff5ecfe-0b15-46e7-8f93-061034231609" />





Langkah 7


<img width="1117" height="624" alt="step6" src="https://github.com/user-attachments/assets/016e2b50-c30f-4409-9672-08ed7773bfd9" />




Langkah 8


<img width="2557" height="1439" alt="step7(1)" src="https://github.com/user-attachments/assets/4b1432e9-efca-415b-9d09-7d72fe4d7eec" />



