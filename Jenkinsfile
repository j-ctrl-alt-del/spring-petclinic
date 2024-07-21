pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        echo 'first jenkins pipeline'
        sh './mvnw clean compile'
      }
    }

    stage('Unit Test') {
      steps {
        sh './mvnw test'
        junit '**/target/surefire-reports/TEST-*.xml'
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

    stage('Package') {
      steps {
        sh './mvnw package -DskipTests=true'
      }
    }

    stage('Shell Script') {
      steps {
        sh './mvnw verify -P tomcat90'
      }
    }

  }
}