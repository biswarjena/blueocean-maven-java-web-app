pipeline {
  agent any
  stages {
    stage('') {
      steps {
        withMaven(jdk: 'JAVA_HOME', maven: 'MAVEN_HOME') {
          sh 'mvn clean'
          sh 'mvn test '
          sh 'mvn jacoco:report'
        }

      }
    }

  }
}