node{
    stage('git check out')
    {
     git 'https://github.com/javahometech/my-app.git'
    }
    
   stage('maven buid')
    {
      def mvnHome=  tool name: 'maven', type: 'maven'
        sh "${mvnHome}/bin/mvn package"
   }
    
     stage('Sonar Analysis')
    {
          
         def mvnHome=  tool name: 'maven', type: 'maven'
        withSonarQubeEnv('sonar7') {
         sh "${mvnHome}/bin/mvn sonar:sonar"
        }
      }
stage("Quality Gate"){
        timeout(time: 1, unit: 'HOURS') { // Just in case something goes wrong, pipeline will be killed after a timeout
            def qg = waitForQualityGate() // Reuse taskId previously collected by withSonarQubeEnv
        if (qg.status != 'OK') {error "Pipeline aborted due to quality gate failure: ${qg.status}"

          } else {

                echo 'Quality Gate PASSED'

            }

        }

    }
}
