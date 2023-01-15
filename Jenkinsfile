pipeline {
  agent any 
  tools {
    maven 'maven'
  }
  stages {
    stage ('Initialize') {
      steps {
        sh '''
                    echo "PATH = ${PATH}"
                    echo "M2_HOME = ${M2_HOME}"
            ''' 
      }
    }

    stage ('Build') {
      steps {
      sh 'mvn clean package'
       }
    }
stage ('Deploy-To-Tomcat') {
            steps {
           sshagent(['tomcat']) {
                sh 'sshpass -p "P@ssw0rd" scp -o StrictHostKeyChecking=no /var/lib/jenkins/workspace/CDCDV1/target/WebApp.war root@192.168.11.12:/root/PROD/apache-tomcat-9.0.71/webapps/webapp.war'  
                 }
           }
  }

  }
}
