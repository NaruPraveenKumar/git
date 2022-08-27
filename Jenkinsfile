node{
    stage('git check out')
    {
     git 'https://github.com/javahometech/my-app.git'
    }
    
   stage{
   sh 'mvn clean package'
   }
}
