pipeline {
 agent any
   stages {
     stage('Deploy to astronomer') {
       when { branch 'main' }
       steps {
         checkout scm  
         script {
           sh 'docker build -t registry.${BASE_DOMAIN}/${RELEASE_NAME}/airflow:ci-${BUILD_NUMBER} .'
           sh 'docker login registry.${BASE_DOMAIN} -u _ -p ${SERVICE_ACCOUNT_KEY}'
           sh 'docker push registry.${BASE_DOMAIN}/${RELEASE_NAME}/airflow:ci-${BUILD_NUMBER}'
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
