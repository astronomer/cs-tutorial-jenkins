pipeline {
 agent any
   stages {
     stage('Deploy to astronomer') {
       steps {
         checkout scm  
         script {
           sh 'docker build -t registry.gcp0001.us-east4.astronomer.io/frigid-umbra-3525/airflow:ci-${BUILD_NUMBER} .'
           sh 'docker login registry.gcp0001.us-east4.astronomer.io -u _ -p ${params.SERVICE_ACCOUNT_KEY}'
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
