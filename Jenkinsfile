pipeline {
  agent  any
  tools {
    maven "Maven"
  }

  stages {

    stage('check java') {
        steps {
            sh "java -version"
        }
    }

	stage('clean') {
      steps {
        sh 'mvn clean'
      }
    }

    stage('backend tests') {
      steps {
        sh 'mvn test'
      }
    }
    
    stage('packaging') {
        steps {
            sh "./mvnw verify -Pprod -DskipTests"
            archiveArtifacts artifacts: '**/target/*.war', fingerprint: true
        }
    }

  }
}
