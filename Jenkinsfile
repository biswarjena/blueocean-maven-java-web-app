pipeline {
  agent any
  stages {
    stage('error') {
      steps {
        withMaven(jdk: 'JAVA_HOME', maven: 'MAVEN_HOME') {
          sh 'mvn clean'
          sh 'mvn test '
          sh 'mvn jacoco:report'
        }

        withSonarQubeEnv(installationName: 'SonarQube Server', credentialsId: 'Sonarqube running in VM devops') {
          sh '/Users/bisu/ProgramFiles/sonar-scanner/bin/sonar-scanner -Dproject.setttings=sonar-project.properties', label: ‘SonarQube Analysis’
        }
        
        waitForQualityGate(abortPipeline: true, credentialsId: ‘Sonarqube running in VM devops’, webhookSecretId: ‘Webhook for sonarqube’)
        }

      }
    }

  }
}
