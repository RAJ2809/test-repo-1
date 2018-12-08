#!groovy​
   
pipeline {
    agent any 
    stages {
    
    stage('Deliver for development') {
            when {
                branch 'develop'
            }
            steps {
                echo 'Hello, Maven'
                bat 'dir'
                bat 'mvn --version'
                input message: 'Finished using the web site? (Click "Proceed" to continue)'
                echo 'Thanks for the option'
            }
        }
        stage('Deploy for production') {
            when {
                branch 'master'
            }
            options {
        	   timeout(time: 30, unit: 'SECONDS')
            input message: 'Finished using the web site? (Click "Proceed" to continue)'
            }
            steps {
               echo 'Hello, JDK'
                bat 'java -version'
                
        }
        
      }
      }
      }
