pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        echo 'first jenkins pipeline'
        sh './mvnw clean compile'
      }
    }

    stage('Static Analysis') {
      steps {
        sh '''mvn clean verify sonar:sonar \\
  -Dsonar.projectKey=JPetStore \\
  -Dsonar.projectName=\'JPetStore\' \\
  -Dsonar.host.url=http://3.237.103.68:9000 \\
  -Dsonar.token=sqp_b1030a61227c8fed5e8407995a43db917e785767'''
      }
    }

  }
}