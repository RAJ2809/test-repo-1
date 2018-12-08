#!groovy​

pipeline {
    agent any 
    stages {
        stage('Build') {
            steps {
                echo 'Hello, Maven'
                bat 'dir'
                bat 'mvn --version'
            }
        }
        stage('Test') {
            steps {
                echo 'Hello, JDK'
                bat 'java -version'
            }
        }
        stage('Deploy') {
            options {
        timeout(time: 30, unit: 'SECONDS') 
            }
        input {
        message "Which Version?"
        ok "Deploy"
        parameters {
            choice(name: 'APP_VERSION', choices: "v1.1\nv1.2\nv1.3", description: 'What to deploy?')
        }
      }
      
      steps {
                echo "Continuing with deployment"
                echo 'Hello, GIT'
                bat 'git version'
            }
        }
    }
}
