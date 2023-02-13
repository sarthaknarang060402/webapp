pipeline {
    agent {
        label 'master'
    }
    stages {
        stage('Build') {
            steps {
                 echo 'This is a minimal pipeline.'
            }
        }
//         stage('Sonar-Report') {
//             steps {
//             sh 'mvn sonar:sonar \
//   -Dsonar.projectKey=jenkins_project \
//   -Dsonar.host.url=http://localhost:9000 \
//   -Dsonar.login=5f09ded7e5db4d0ea0dcfd937c181af706e60475'
//             }
//         }
        stage('Test') { 
            steps {
                 echo 'This is a minimal pipeline.'
            }
        }
        stage('Sonar-Report') {
            steps {
                 echo 'This is a minimal pipeline.'
            }
        }
    }
}
