pipeline {
	agent any
	stages {
		stage ('build') {
			steps { 
				bat 'mvn clean package'
		}
		
		post{
			success {
				echo 'Now Archiving ...' 
				archiveArtifacts artifacts: '**/target/*.war'
			}
		}
	  }	
	  stage ('Deploy to staging'){
		steps {
			build job: 'deploy-staging'
	  
	  
	  
	  
		}
	  }
	}
	
}
				
		