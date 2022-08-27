node{
    stage('git check out')
    {
     git 'https://github.com/javahometech/my-app.git'
    }
    
   stage('maven buid')
   sh 'mvn clean package'
   }
}
