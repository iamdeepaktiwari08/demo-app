Hanumat kripa 
🚀 DevOps CI/CD Pipeline with Jenkins, Docker & DockerHub

This project demonstrates a complete CI/CD pipeline using Jenkins, Docker, and DockerHub.
A static website is automatically built into a Docker image and pushed to DockerHub whenever new code is committed.

⸻

🙏 Project Credit (Fork Information)

This repository is forked from my teacher’s original project:
🔗 gauravubnare/demo-app

I extended it by adding a fully automated CI/CD pipeline using Jenkins & Docker.

⸻

📸 Jenkins Build Success


⸻

📸 Live Website Output


⸻

📸 DockerHub Repository (Image Pushed Successfully)


⸻

📌 Project Features
	•	Fully automated CI/CD pipeline
	•	Git → Jenkins → Docker build → DockerHub Push
	•	Nginx-based static site container
	•	Jenkins Freestyle Job
	•	Deployable anywhere using Docker

⸻

🛠️ Tech Stack

Component	Technology
Source Code	HTML, CSS, JS
CI Tool	Jenkins
Containerization	Docker
Registry	DockerHub
Hosting	AWS EC2 (Ubuntu)


⸻

📂 Project Structure

demo-app/
│
├── assets/
├── css/
├── js/
├── scss/
├── manual/
├── index.html
└── Dockerfile


⸻

🐳 Dockerfile

FROM nginx
COPY . /usr/share/nginx/html
EXPOSE 80


⸻

⚙️ Step-by-Step Setup Guide

⸻

✅ 1. Launch EC2 Server
	•	Ubuntu 22.04
	•	t2.micro
	•	Open ports 22, 80, 8080

⸻

✅ 2. Install Docker

sudo apt update
sudo apt install docker.io -y
sudo systemctl start docker
sudo systemctl enable docker

Give Jenkins permission:

sudo usermod -aG docker jenkins
sudo reboot


⸻

✅ 3. Install Jenkins

sudo apt update
sudo apt install openjdk-17-jdk -y
wget -q -O - https://pkg.jenkins.io/debian-stable/jenkins.io.key | sudo apt-key add -
sudo sh -c 'echo deb https://pkg.jenkins.io/debian-stable binary/ > /etc/apt/sources.list.d/jenkins.list'
sudo apt update
sudo apt install jenkins -y
sudo systemctl start jenkins

Open Jenkins:

http://<EC2-IP>:8080


⸻

✅ 4. Install Jenkins Plugins
	•	Docker
	•	Docker Pipeline
	•	Docker Build Step
	•	Git

⸻

✅ 5. Configure Docker Host in Jenkins

Manage Jenkins → Configure System → Docker

Set:

unix:///var/run/docker.sock

✔ Fixes error:
java.lang.NullPointerException: uri was not specified

⸻

✅ 6. Create Jenkins Freestyle Job

Add GitHub Repo (forked repo)

https://github.com/iamdeepaktiwari08/demo-app.git

Add Docker build step

docker build -t <dockerhub-username>/app-org-jenkins-cicd:v1 .

DockerHub Login

echo $DOCKER_PASSWORD | docker login -u $DOCKER_USERNAME --password-stdin

Push Image

docker push <dockerhub-username>/app-org-jenkins-cicd:v1


⸻

✅ 7. Verify Image on DockerHub

Your repo will show:


⸻

✅ 8. Deploy Anywhere

Run container:

docker run -d -p 80:80 <dockerhub-username>/app-org-jenkins-cicd:v1

Check website:


⸻

🎯 Outcome

By completing this project, you learn:
	•	CI/CD automation
	•	Jenkins job configuration
	•	Docker build & push workflow
	•	DockerHub integration
	•	Real DevOps pipeline experience

Perfect for Resume, Portfolio, Interviews, and DevOps practice.

⸻

🙌 Credits
	•	Original Project: gauravubnare/demo-app
	•	CI/CD Automation Added By: Deepak Tiwari

⸻

👨‍💻 Author

Deepak Tiwari
GitHub: https://github.com/iamdeepaktiwari08
DockerHub: https://hub.docker.com/u/deepaktiwariii

⸻
