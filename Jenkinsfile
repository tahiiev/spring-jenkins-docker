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
          stage ('Build docker') {
              steps {
                  sh "./gradlew build"
              }
          }
          steps {
              withDockerRegistry(credentialsId: 'dockerhub', url: 'https://index.docker.io/v1/') {
                  sh 'docker push avsimvadim/app'
              }
          }
          stage ('Deploy') {
              steps {
                  sh 'docker run -d -p 8080:8080 avsimvadim/app'
              }
          }

     }
}