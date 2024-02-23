@Library("shared-library") _

pipeline {
    agent {
        docker {
            image 'ajsyd141/java-python'
            args '-u 0:0 --privileged --net host -v /var/run/docker.sock:/var/run/docker.sock -v /root/.m2:/root/.m2'
        }
    }

 stages {

    stage('Pipeline Metadata') {
        steps {
         script {
            gitCheckOut.customCheckout()
         }
      }  
    }

   stage('Injecting Environment Variables') {
        steps {
            echo 'loading Variables'
             loadVariables()
             echo 'Done'
        }  
    }

    stage('calling') {
        steps {
            echo 'Calling configs'
             secretCall(key: "$KEY")
             secretCall(key: "$SECRET_ID")
             secretCall(key: "$SECRET_TOKEN")
             secretCall(key: "$SAST")
             secretCall(key: "$SCA")

        }  
    }

    // stage('Install Dependencies'){
    //     steps{
    //         script{
    //             sh 'apk add --update --no-cache maven'
    //         }
    //     }
    // }

    // stage('Maven Build') {
    //     steps {
    //         mvnCheck()
    //     }  
    // }

    // stage('Unit Test') {
    //     steps {
    //         mvnTest()
    //     }
    //  }  

    // stage('SAST') {
    //     steps {
    //         echo "${project_Name}"
    //         mvnSonar(project_Name: "${project_Name}")
    //     }
    //  }  

    // stage('Quality Gate') {
    //     steps {
    //         mvnSonarQualityGate()
    //     }
    //  }  

    // stage('DockerImage Build') {
    //     steps {
    //          dockerBuild()
    //         }
    //     }
         
    // stage('Docker Image Push') {
    //     steps {
    //         dockerImagePush(credentialsId: 'DockerID', url: 'https://registry.hub.docker.com')
    //     }
    //  }
 }

    post {
       
        always {

             echo "${project_Name}"
            cleanWs()
        }
   }
}


