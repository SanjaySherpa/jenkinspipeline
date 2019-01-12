pipeline {
    agent any
    tools{
	maven 'mymaven'
	jdk 'myjava'
}
parameters {
	string(name: 'tomct-dev', defaultValue: '3.17.142.240', description: 'Staging server')
	
}
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
			sh "scp **/target/*.war ec2-user@${params.tomcat_dev}:/var/lib/tomcat7/webapps"	
		}
		
	}	
}

