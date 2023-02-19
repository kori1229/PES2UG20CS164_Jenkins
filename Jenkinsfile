pipeline {
  agent any 
    tools {
        maven 'maven 3.3.9'
        jdk 'jdk8'
    }
    stages {
      stage('Build') {
        def mvn_version = 'maven'
        withEnv( ["PATH+MAVEN=${tool mvn_version}/bin"] ) {
  //sh "mvn clean package"
        }
        steps {
          bat 'mvn clean install'
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

