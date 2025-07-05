# Flask MySQL Docker App

A two-tier web application built using **Flask** (Python) and **MySQL**, containerized with **Docker**, and orchestrated using **Docker Compose**. Designed to demonstrate DevOps fundamentals like containerization, orchestration, and deployment.

## 🚀 Tech Stack

- Python (Flask)
- MySQL
- Docker
- Docker Compose
- AWS EC2 (for deployment)
- HTML (Jinja templates)




## 📁 Project Structure

```
flask-mysql-app/
├── app.py  
├── Dockerfile  
├── docker-compose.yml  
├── requirements.txt  
└── templates/  
    └── index.html
```




## 🔧 Setup Instructions

### Prerequisites

- Docker
- Docker Compose

### Run Locally

```bash
# Clone the repo
git clone https://github.com/Nidhi-kumarii/flask-mysql-app.git
cd flask-mysql-app

# Build and start the containers
docker-compose up -d
```



## 🐳 Docker Hub Image

This project is also available as a Docker image on Docker Hub:

🔗 **[nidhikumari1/two-tier-flask-app:latest](https://hub.docker.com/r/nidhikumari1/two-tier-flask-app)**

You can pull and run the image using the following command:

```bash
docker pull nidhikumari1/two-tier-flask-app:latest



# Visit the app
http://localhost:5000




🛡️ Security Notes
Only port 5000 is exposed for Flask app

Port 3306 (MySQL) is kept internal

For production, consider setting up NGINX + HTTPS + Basic Auth



👩‍💻 Author

Nidhi Kumari


💡 This project is part of my DevOps hands-on learning and portfolio.
