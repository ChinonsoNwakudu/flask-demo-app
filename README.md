# Flask DevOps Demo

A simple Flask application demonstrating a complete DevOps workflow with containerization and CI/CD integration.

## Project Overview

This project demonstrates a modern DevOps pipeline for a simple Python Flask application, including:

- Building a basic web application with Flask
- Containerizing the application with Docker
- Version control with Git and GitHub
- Continuous Integration and Continuous Deployment with GitHub Actions
- Automated container image publishing to Docker Hub

## Prerequisites

To work with this project, you'll need:

- Python 3.9 or higher
- Docker installed on your machine
- Git
- A GitHub account
- A Docker Hub account

## Application Structure

```
flask-devops-demo/
├── .github/
│   └── workflows/
│       └── docker-build-push.yml
├── venv/
├── .dockerignore
├── .gitignore
├── app.py
├── Dockerfile
└── requirements.txt
```

## Getting Started

### 1. Clone the Repository

```bash
git clone https://github.com/ChinonsoNwakudu/flask-demo-app.git
cd flask-devops-demo
```

### 2. Set Up Local Development Environment

```bash
# Create and activate virtual environment
python -m venv venv
source venv/bin/activate  # On Windows: venv\Scripts\activate

# Install dependencies
pip install -r requirements.txt

# Run the application locally
python app.py
```

The application will be available at http://localhost:5000

### 3. Working with Docker

Build and run the containerized application:

```bash
# Build the Docker image
docker build -t flask-devops-demo .

# Run the container
docker run -p 5000:5000 flask-devops-demo
```

Access the application at http://localhost:5000


## CI/CD Pipeline

This project uses GitHub Actions for CI/CD. The workflow is defined in `.github/workflows/docker-build-push.yml`.

### Workflow Steps

1. Triggered on push to main branch or pull requests
2. Checks out the code
3. Logs in to Docker Hub
4. Builds the Docker image
5. Pushes the image to Docker Hub

### Setting Up GitHub Secrets

To enable the CI/CD pipeline, add these secrets to your GitHub repository:

1. Go to your repository → Settings → Secrets and variables → Actions
2. Add the following secrets:
   - `DOCKER_HUB_USERNAME`: Your Docker Hub username
   - `DOCKER_HUB_ACCESS_TOKEN`: Your Docker Hub access token (not your password)

## Docker Commands Reference (Alternative)

### Build an Image

```bash
docker build -t yourusername/flask-demo-app:latest .
```

### Run a Container

```bash
docker run -d -p 5000:5000 yourusername/flask-demo-app:latest
```

### Push to Docker Hub

```bash
# Login to Docker Hub
docker login

# Push the image
docker push yourusername/flask-demo-app:latest
```

### Pull from Docker Hub

```bash
docker pull yourusername/flask-demo-app:latest
```

## Troubleshooting

### Docker Hub Authentication Issues

If you encounter a "401 Unauthorized" error when pushing to Docker Hub:

1. Verify that your Docker Hub repository exists
2. Check that your access token is valid and has push permissions
3. Ensure your GitHub secrets are configured correctly
4. Test authentication locally with `docker login`

### Repository Creation

Make sure your repository exists on Docker Hub before pushing. You can create it through the Docker Hub website.

## Additional Resources

- [Flask Documentation](https://flask.palletsprojects.com/)
- [Docker Documentation](https://docs.docker.com/)
- [GitHub Actions Documentation](https://docs.github.com/en/actions)
- [Docker Hub Documentation](https://docs.docker.com/docker-hub/)

