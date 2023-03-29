pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        bat 'mvn -B -DskipTests clean package'
      }
    }

    stage('Test') {
      post {
        always {
          junit 'target/surefire-reports/*.xml'
        }

      }
      steps {
        bat 'mvn test'
      }
    }

    stage('Nexus-deploy') {
      steps {
        bat 'mvn clean deploy'
      }
    }

  }
  tools {
    maven 'mymaven'
  }
}
