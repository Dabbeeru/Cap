node 
{
    stage('Clone sources') {
        git url: 'https://github.com/Dabbeeru/Cap.git'
    }
}
{
   def M2_HOME="/usr/share/maven"
   stage('getscm') { // for display purposes
      // Get some code from a GitHub repository
      git ''
      // Get the Maven tool.
   }
   stage('SonarQube analysis') {
    def scannerHome = tool 'sonar';
    withSonarQubeEnv('sonar') { // If you have configured more than one global server connection, you can specify its name
      sh "${scannerHome}/bin/sonar-scanner"
    }
  }
   stage('Build') {
      // Run the maven build
      if (isUnix()) {
         sh "${M2_HOME}/bin/mvn -Dmaven.test.failure.ignore clean package"
      } else {
      echo 'this is build maven artifact'
         bat(/"${mvnHome}\bin\mvn" -Dmaven.test.failure.ignore clean package/)
      }
   }
    stage('artifact') {
      
      archive 'target/*.war'
   }
   stage("DeployAppTomcat") {
  sshagent(['give credentials id']) {
    sh "scp -o StrictHostKeyChecking=no target/war file name   centos@ip adress:/usr/share/tomcat/webapps/" 
   }
  }
 }
