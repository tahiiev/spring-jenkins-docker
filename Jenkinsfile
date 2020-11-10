pipeline {
     agent any
     stages {
          stage("Compile") {
               steps {
                    sh "chmod +x ./gradlew"
                    sh "./gradlew compileJava"
               }
          }
          stage("Unit test") {
               steps {
                    sh "./gradlew test"
               }
          }
          stage('Build Docker image') {
                steps {
                    sh './gradlew docker'
                }
          }
          stage('Push Docker image') {
                      environment {
                          DOCKER_HUB_LOGIN = credentials('docker-hub')
                      }
                      steps {
                          sh 'docker login --username=avsimvadim --password=Vadym1595'
                          sh './gradlew dockerPush'
                      }
          }
     }
}