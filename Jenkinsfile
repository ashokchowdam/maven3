node('built-in') 
{
   stage('continuousdownload') 
   {
      git 'https://github.com/intelliqittrainings/maven.git'
   }
    stage('continuousbuild') 
   {
     sh 'mvn package'
   }
    stage('continuousdeployment') 
   {
     deploy adapters: [tomcat9(credentialsId: '9c4540f7-d30b-4640-8c30-b8f6fcd13cb3', path: '', url: 'http://172.31.13.44:8080')], contextPath: 'testapp1', war: '**/*.war'
   }
    stage('continuoustesting') 
   {
     git 'https://github.com/intelliqittrainings/FunctionalTesting.git'
     sh 'java -jar /home/ubuntu/.jenkins/workspace/deploy/testing.jar'
   }
    stage('continuousbuild') 
   {
     deploy adapters: [tomcat9(credentialsId: '9c4540f7-d30b-4640-8c30-b8f6fcd13cb3', path: '', url: 'http://172.31.3.218:8080')], contextPath: 'proadapp', war: '**/*.war'
   }
   
   

}
