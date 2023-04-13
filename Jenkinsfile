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
    stage('Sonar-Demo') {
      steps {
        SonargraphReport sonargraphBuildJDK: 'jdk11', sonargraphBuildVersion: 'mysonar'
        bat 'mvn clean install sonar:sonar -Dsonar.host.url=http://localhost:9000 Dsonar.analysis.mode=publish'
      }
    }

  }
  tools {
    maven 'mymaven'
    //sonar 'mysonar'
  }
  
}
