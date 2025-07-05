
 End-to-End Project with Docker + Jenkins CI/CD Pipeline

```markdown
# 🐳 Flask + MySQL App with Jenkins CI/CD Pipeline

This project is a full end-to-end DevOps practice project where we:

1. Developed a simple **Flask + MySQL** app.
2. Containerized the app using **Docker** with a multi-stage build.
3. Automated the CI/CD process using **Jenkins**, building and pushing Docker images to **DockerHub**.

---

## 🧱 Step 1: Application Development

### ✅ Stack Used

- **Flask** – for the web app
- **MySQL** – for backend DB
- **Docker** – for containerizing the app

### ✅ Folder Structure

```

flask-mysql-app/
├── app.py                # Main Flask application
├── requirements.txt      # Python dependencies
├── Dockerfile            # Multistage build for Flask + MySQL
├── Jenkinsfile           # CI/CD script for Jenkins
└── README.md

````

---

## 🐳 Step 2: Dockerization

- Created a **multi-stage Dockerfile** to separate build and runtime.
- Tested image locally using:
  
```bash
docker build -t two-tier-flask-app .
docker run -p 5000:5000 two-tier-flask-app
````

---

## ⚙️ Step 3: Jenkins CI/CD Pipeline

### ✅ Jenkins Setup

* Installed Jenkins on an EC2 instance.
* Installed required plugins (Docker, GitHub, Pipeline, Credentials, etc.)
* Configured credentials for GitHub and DockerHub.

### ✅ Jenkinsfile (Declarative Pipeline)

```groovy
pipeline {
    agent any

    environment {
        IMAGE_NAME = 'nidhikumari1/two-tier-flask-app'
        TAG = 'latest'
    }

    stages {
        stage('Clone Repo') {
            steps {
                git url: 'https://github.com/Nidhi-kumarii/flask-mysql-app.git', branch: 'main'
            }
        }

        stage('Build Docker Image') {
            steps {
                script {
                    sh 'docker build -t $IMAGE_NAME:$TAG .'
                }
            }
        }

        stage('Login to Docker Hub') {
            steps {
                withCredentials([usernamePassword(credentialsId: 'dockerhub-creds', usernameVariable: 'USERNAME', passwordVariable: 'PASSWORD')]) {
                    sh 'echo $PASSWORD | docker login -u $USERNAME --password-stdin'
                }
            }
        }

        stage('Push Docker Image') {
            steps {
                sh 'docker push $IMAGE_NAME:$TAG'
            }
        }

        stage('Cleanup') {
            steps {
                sh 'docker rmi $IMAGE_NAME:$TAG || true'
            }
        }
    }
}
```

---

## 📦 DockerHub Repository

> Docker Image pushed to:
> 👉 [nidhikumari1/two-tier-flask-app](https://hub.docker.com/repository/docker/nidhikumari1/two-tier-flask-app)

---

## 📌 What's Next?

* [ ] Automated **deployment stage** using SSH into a remote EC2 agent.
* [ ] Connect Jenkins Master to Agent for deployment.
* [ ] Add **unit testing stage** before build 
* [ ] Use Docker Compose or Kubernetes for full production setup.

---

## 🙋‍♀️ Author

**Nidhi Kumari**
📍 DevOps | Cloud | Docker | CI/CD
🔗 GitHub: [Nidhi-kumarii](https://github.com/Nidhi-kumarii)
📦 DockerHub: [nidhikumari1](https://hub.docker.com/u/nidhikumari1)

---

```


```
