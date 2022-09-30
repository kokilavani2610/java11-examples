pipeline {
  agent any
  stages {
    stage('Print') {
      steps {
        script {
          echo 'java-11'          
        }
      }
    }
    stage ('Scan') {
            steps {
               withSonarQubeEnv(installationName: 'ProductionSonarQube scanner', credentialsId: 'new-sonar') {
                bat '''                 
                mvn org.sonarsource.scanner.maven:sonar-maven-plugin:3.7.0.1746:sonar
                mvn clean package sonar:sonar
                '''
                }
            }
        }
  }
}
