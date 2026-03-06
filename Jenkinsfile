pipeline {
 agent any

 stages {

  stage('Clone Repo') {
   steps {
    git 'https://github.com/Vennilavanguvi/Trend.git'
   }
  }

  stage('Build Docker Image') {
   steps {
    sh 'docker build -t trend-app .'
   }
  }

  stage('Push Docker Image') {
   steps {
    sh 'docker tag trend-app dockerhubuser/trend-app'
    sh 'docker push dockerhubuser/trend-app'
   }
  }

  stage('Deploy to Kubernetes') {
   steps {
    sh 'kubectl apply -f deployment.yaml'
    sh 'kubectl apply -f service.yaml'
   }
  }

 }
}
