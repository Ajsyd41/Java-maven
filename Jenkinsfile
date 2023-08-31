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
    POSTFIX='-dev'
    VERSION = sh (script: 'mvn help:evaluate -Dexpression=project.parent.artifactId -q -DforceStdout', returnStdout: true)
    ARTIFACT_VERSION="${VERSION}${POSTFIX}"
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

			echo "${env.POSTFIX}"
		    echo '============================================================================'
			echo "${env.VERSION}"
			echo '============================================================================'
            echo "${env.ARTIFACT_VERSION}"

			
        }
     }



            

      }
}

 



