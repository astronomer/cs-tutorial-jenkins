pipeline {
 agent any
   stages {
     stage('Deploy to astronomer') {
       steps {
         checkout scm  
         script {
           sh 'docker build -t registry.gcp0001.us-east4.astronomer.io/frigid-umbra-3525/airflow:ci-${BUILD_NUMBER} .'
           sh 'docker login registry.gcp0001.us-east4.astronomer.io -u _ -p 79f4ef49ec65c2941acb5a51f48fd236'
           sh 'docker push registry.gcp0001.us-east4.astronomer.io/frigid-umbra-3525/airflow:ci-${BUILD_NUMBER}'
         }
       }
     }
   }
 post {
   always {
     cleanWs()
   }
 }
}
