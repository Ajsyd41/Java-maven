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
	  GRP_ID='value'
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
			env.GRP_ID=sh(script: 'mvn org.apache.maven.plugins:maven-help-plugin:3.2.0:evaluate -Dexpression=project.artifactId -q',returnStdout: true).trim()
			
			echo '============================================================================'
			
			echo "${env.GRP_ID}"
        }
     }



            

      }
}

 



