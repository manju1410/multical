node{
    stage('scmcheckout'){
        git url:'https://github.com/manju1410/multical.git'
    }
    stage('mvn package'){
        def Mvn_Home= tool name:'maven3', type:'maven'
        sh "${Mvn_Home}/bin/mvn package"
    }
    stage('SonarQube analysis') {
        def Mvn-Home = tool name:'maven3', type:'maven'
        withSonarQubeEnv('sonar') {
        sh "${Mvn_Home}/bin/mvn sonar:sonar"
        }
    }    
    stage('Deploy-to-Tomcat'){
       ws('/home/vijay/.jenkins/workspace/job1/target'){
       sh 'cp -r *.war /home/vijay/softwares/apache-tomcat-8.5.35/webapps'
    }
   }
 }
