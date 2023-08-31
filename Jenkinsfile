// ---
// ref repo -https://github.com/spring-projects/spring-petclinic.git
// ---

pipeline
{

    agent {
       docker { 
           image 'maven:3.9.0'
            args '-v /root/.m2:/root/.m2'
      }
	}
	  environment {
    indev='-dev'
    def version = sh (script: 'mvn help:evaluate -Dexpression=parent.version -q -DforceStdout', returnStdout: true)

    fin="${version}${indev}"
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

			echo "${env.version}"
		    echo '============================================================================'
			echo "${env.version}"
			echo '============================================================================'
            echo "${env.indev}"

			
        }
     }



            

      }
}

 



