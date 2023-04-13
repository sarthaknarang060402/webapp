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
        withSonarQubeEnv('SonarQube') {
        bat 'mvn clean install sonar:sonar \
        -Dsonar.host.url=http://localhost:9000 \
        -Dsonar.analysis.mode=publish org.codehaus.sonar-plugins.pdf-report:mavenpdfreport-plugin:1.3:generate \
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
