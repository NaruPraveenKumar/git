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
    
       stage("sonar-qubeQuality Gate"){
          timeout(time: 1, unit: 'HOURS') {
              def qg = waitForQualityGate()
              if (qg.status != 'OK') {
                  error "Pipeline aborted due to quality gate failure: ${qg.status}"
              }
          }
      }  
}
