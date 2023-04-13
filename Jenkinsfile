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
        withSonarQubeEnv('mysonar') {
        bat 'mvn clean install sonar:sonar \
          -Dsonar.host.url=http://localhost:9000 \
          -Dsonar.analysis.mode=publish org.sonarsource.scanner.maven:sonar-maven-plugin:jar:3.9.1.2184 \
          -Dsonar.projectKey=jenkins_project \
          -Dsonar.login=squ_986172bfd1ef8ecab3b0ca4e51116b14bdd69eec'
        }
      }
    }

  }
  tools {
    maven 'mymaven'
    //sonar 'mysonar'
  }
  
}
