// ---
// ref repo -https://github.com/spring-projects/spring-petclinic.git
// ---

pipeline
{

    agent any

    tools{
        
        maven 'Maven'
    }
    options{

        timestamps()
        timeout(time: 20,unit: 'MINUTES')
    }
 stages
    {
     stage('SCM Checkout'){
        steps{

            checkout scm
        }
     }
    stage('Unit Test'){
        steps{

            bat 'mvn clean package'
            junit '**/target/surefire-reports/TEST-*.xml'
        }
     }
      stage('SonarQube analysis') {
        steps {
           withSonarQubeEnv('sonar-api') {
               bat 'mvn clean package'
               bat  'mvn sonar:sonar'
             }
        }
     }
       stage('Integration Test'){
        steps{

            bat 'mvn clean package -Dsurefire.skip=true failsafe:integration-test'
            junit '**/target/failsafe-reports/*.xml'
        }
     }
        
            
      //    script {
      //     scannerHome = tool 'sonarqube_scanner'
      //    }
      //   withSonarQubeEnv('sonar-api') {
      //     bat "${scannerHome}/sonar-scanner"
      //   }
      }
}

 



