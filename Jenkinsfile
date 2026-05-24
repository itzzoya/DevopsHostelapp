pipeline {
    agent any

    environment {
        IMAGE = "your-dockerhub-username/hostel-app:latest"
    }

    stages {

        stage('Checkout') {
            steps {
                git 'https://github.com/itzzoya/DevopsHostelapp.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t $IMAGE .'
            }
        }

        stage('Docker Login') {
            steps {
                sh 'echo YOUR_DOCKERHUB_PASSWORD | docker login -u YOUR_DOCKERHUB_USERNAME --password-stdin'
            }
        }

        stage('Push Image') {
            steps {
                sh 'docker push $IMAGE'
            }
        }

        stage('Deploy to Kubernetes') {
            steps {
                sh 'kubectl apply -f k8s/deployment.yaml'
                sh 'kubectl apply -f k8s/service.yaml'
            }
        }
    }
}
