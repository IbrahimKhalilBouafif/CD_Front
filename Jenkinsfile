pipeline {
   agent any
   stages {
    stage('Checkout') {
      steps {
        script {
           git branch: 'ibrahim', 
           url: 'https://github.com/IbrahimKhalilBouafif/CD_Front.git'
          }
       }
    }
    stage('Build') {
      steps {
        script {
           sh 'ansible-playbook ansible/build.yml -i ansible/inventory/hosts.yml'
          }
       }
    }
   }
}