pipeline{
 agent any
 stages{
   stage("checkout git"){
      steps{
        echo "git checkout started"
        git url: "https://github.com/akshu20791/addressbook-cicd-project"
      }
   }
  stage("compiling the code"){
    steps{
      echo "we are compiling the code"
      sh "mvn compile"
     }
   }
   stage("qa for the code"){
        steps{
            sh "mvn checkstyle:checkstyle" 
            recordIssues sourceCodeRetention: 'LAST_BUILD', tools: [checkStyle()]
      }
   }
   stage("Converting the code to package"){
        steps{
            sh "mvn package" 
      }
   }
   stage("Deploy the project in tomcat"){
        steps{
            sh "sudo cp /var/lib/jenkins/workspace/addressbook-pipeline/target/addressbook.war /opt/apache-tomcat-8.5.100/webapps"
      }
   }
   
 }
}
