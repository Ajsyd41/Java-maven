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

            bat 'mvn test -Dmaven.test.failure.ignore=true'
            junit '**/target/surefire-reports/TEST-*.xml'
        }
     }
      stage('Package') { 
      steps {

        echo 'Package Appplication...'
        bat 'mvn clean package -Dmaven.test.skip=true'

      }
    }
      stage('SonarQube analysis') {
        steps {
           withSonarQubeEnv('sonar-api') {
            //    bat 'mvn clean package'
               bat  'mvn sonar:sonar'
             }
        }
     }

    stage('Deploy to Nexus') { 
      steps {
        echo 'Deploy Appplication...'
        bat 'mvn deploy -Dmaven.test.skip=true -Dmaven.install.skip=true'
      }
    }
            

      }
}

 



