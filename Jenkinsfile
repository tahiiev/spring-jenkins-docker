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
           stage('Building our image') {
                      steps {
                          script {
                              dockerImage = docker.build registry + ":$BUILD_NUMBER"
                          }
                      }
                  }
          stage('Deploy our image') {
                       steps {
                           script {
                               docker.withRegistry( '', registryCredential ) {
                                   dockerImage.push()
                           }
                       }
                   }
                   stage('Cleaning up') {
                       steps {
                           sh "docker rmi $registry:$BUILD_NUMBER"
                       }
                   }

     }
}