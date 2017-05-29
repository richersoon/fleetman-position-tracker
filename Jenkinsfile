node {
   stage('Preparation') { 
      git 'https://github.com/richersoon/fleetman-position-tracker'
   }
   stage('Build') {
      sh "mvn clean package"
   }
   stage('Results') {
      junit '**/target/surefire-reports/TEST-*.xml'
      archive 'target/*.jar'
   }
   stage('Deploy') {
      ansiblePlaybook credentialsId: 'ssh-credentials', installation: 'ansible-installation', playbook: 'deploy.yaml', sudo: true, sudoUser: null
   }
}
