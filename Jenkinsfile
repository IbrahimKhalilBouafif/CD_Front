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

    stage('Docker Build') {
      steps {
        script {
           sh 'ansible-playbook ansible/docker.yml -i ansible/inventory/hosts.yml'
          }
       }
    }
    stage('Pushing DockerHub') {
      steps {
        script {
           sh 'ansible-playbook ansible/docker-registry.yml -i ansible/inventory/hosts.yml'
          }
       }
    }
     stage('Monitoring') {
      steps {
        script {
           sh 'cd /var/lib/jenkins/workspace/cd-project'
           sh 'docker compose up -d'
          }
       }
    }
   }
}