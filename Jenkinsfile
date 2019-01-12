pipeline {
    agent any
    tools{
	maven 'mymaven'
	jdk 'myjava'
}
parameters {
	string(name: 'tomcat-dev', defaultValue: '3.17.142.240', description: 'Staging server')
	
}
stages{  	
stage('build'){
	steps{
		sh 'mvn clean package'


	     }
		post {
			success { 
			echo 'Now archiving...'
			archiveArtifacts artifacts: '**/target/*.war'
			}
		}
	}
	stage('deployment'){
		steps{
			sh "scp -i /home/jenkins/sanjay.pem **/target/*.war ec2-user@3.17.142.240 /var/lib/tomcat/webapps"	
		}
		
	}	
}
}
