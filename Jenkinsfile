pipeline {
  agent any
  stages {
    stage('Checkout Code') {
      steps {
        git(url: 'https://github.com/derekchancts/curriculum-app', branch: 'dev')
      }
    }

    stage('Log') {
      parallel {
        stage('Log') {
          steps {
            sh 'ls -la'
          }
        }

        stage('test') {
          steps {
            sh 'la -al'
          }
        }

      }
    }

    stage('Build') {
      steps {
        sh 'docker build -f curriculum-front/Dockerfile -t derekchancts100/curriculum-front:latest .'
      }
    }

    stage('Log into Dockerhub') {
      environment {
        Creds = credentials('dockerhub')
      }
      steps {
        sh 'docker login -u $Creds_USR -p $Creds_PSW'
      }
    }

    stage('Push') {
      steps {
        sh 'docker push derekchancts100/curriculum-front:latest'
      }
    }

  }
}