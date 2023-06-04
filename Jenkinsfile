pipeline {
  agent any

  stages {
      stage('Build Artifact') {
            steps {
              sh "mvn clean package -DskipTests=true"
              archive 'target/*.jar' //so that those can be downloaded later
            }
      }
      
      stage('Unit Test - Junit and Jacoco') {
            steps {
              sh "mvn test"
            }
            post {
              always {
                Junit 'target/surefire-reports/*.xml'
                Jacoco execPattern: 'target/jacoco.exec'
              }
            }
        }   
    }
}

