pipeline{
     agent any
     
     tools{
     	maven 'Maven'
     }

     stages{
          stage('Checkout'){
               steps{
                    git branch:'master', url: 'https://github.com/t-a-nmay/myAnsibleWebApp.git'
               }
          }
          stage('Build'){
               steps{
                    sh 'mvn clean package'
               }
          }
          stage('Archive'){
               steps{
                    archiveArtifacts artifacts: 'target/*.war', fingerprint:true
               }
          }
          stage('Deploy'){
               steps{
                    sh 'mvn clean install'
                    sh 'ansible-playbook ansible/playbook.yml -i ansible/hosts.ini'
               }
          }
          
     }
     
}
