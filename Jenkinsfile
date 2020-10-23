pipeline {
	agent any
	stages {
		stage('Checkout SCM') {
			steps {
				git changelog: false, credentialsId: '393a4939-9ce6-4dec-a270-f19cabdb93e4', poll: false, url: 'https://github.com/SIT-ICT3x03/Team-009.git'
			}
		}

		stage('OWASP DependencyCheck') {
			steps {
				dependencyCheck additionalArguments: '--format HTML --format XML', odcInstallation: 'Default'
			}
		}
	}	
	post {
		success {
			dependencyCheckPublisher pattern: 'dependency-check-report.xml'
		}
	}
}
