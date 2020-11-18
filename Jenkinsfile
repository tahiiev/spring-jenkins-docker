pipeline {
    agent any
     stages {
          stage ('Build docker') {
              steps {
                  sh "chmod +x ./gradlew"
                  sh "gradle build"
              }
          }
          stage("Unit test") {
                  steps {
                    sh "./gradlew test"
                  }
          }
          dockerStop
          stage('Docker stop, build, run,push') {
                steps{
                sh './gradlew dockerStop'
                }
                steps{
                sh './gradlew docker'
                }
                steps{
                sh './gradlew dockerRun'
                }
          }
     }
}