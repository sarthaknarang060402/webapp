pipeline {
  agent {
    node {
      label 'Salve-01'
    }

  }
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

    stage('Sonar-Report') {
      steps {
        echo 'done'
      }
    }

  }
  tools {
    maven 'mymaven'
  }
}