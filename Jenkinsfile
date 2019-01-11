pipeline {
    agent any
    tools{
	maven 'mymaven'
	jdk 'java 8'
}
    stages{
        stage('Build'){
            steps {
                sh 'mvn clean package'
            }
            post {
                success {
                    echo 'Now Archiving...'
                    archiveArtifacts artifacts: '**/target/*.war'
                
            }
         }
      }
}
}
