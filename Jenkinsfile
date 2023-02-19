pipeline {
  agent any 
    tools {
        maven 'Maven 3.3.9'
        jdk 'jdk8'
    }
    stages {
      stage('Build') {
        steps {
          sh 'mvn clean install'
          echo 'Build Stage Successful'
        }
      }
      stage('Test') {
        steps {
          sh 'mvn test'
          echo 'Test stage succesful'
          post {
            always {
              junit 'target/surefire-reports/*.xml'
            }
          }
        }
      }
      stage('Deploy') {
        steps {
          sh 'mvn deploy'
          echo 'Development Successful'
        }
      }
    }
    post {
      failure {
        echo 'Pipeline failed'
      }
    }
  }

