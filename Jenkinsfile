pipeline
{

    agent any

    tools
    {
        maven 'Maven'
    }
    options
    {
        timestamps()
    }
 stages
    {
     stage('SCM Checkout')
     {
        steps
        {
            git branch: 'main', credentialsId: 'GithubID', url: 'https://github.com/Ajsyd41/jenkinsRepo.git'
        }
     }
    stage('Unit Test')
     {
        steps
        {
            bat 'mvn test'
            junit '**/target/surefire-reports/TEST-*.xml'
        }
     }
     stage('Maven Build')
     {
        steps
        {
             bat 'mvn clean install'   
        }
     }
         stage('SonarQube analysis') {
      steps {
         script {
          scannerHome = tool 'sonarqube_scanner'
         }
        withSonarQubeEnv('sonar-api') {
          bat "${scannerHome}/sonar-scanner"
        }
      }
    }
 }
}
 



