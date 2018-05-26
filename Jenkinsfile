pipeline {
	tools {
		maven "M3"
	}
	agent any
	stages {
		stage("Preparation") {
			steps {
				git 'https://github.com/onofreiAdina/PracticaAIS1.git'
			}
		}
		stage("Test") {
			steps {				
				if(isUnix()) {
					sh "mvn test"
				} else {
					bat(/"${mvnHome}\bin\mvn" test/)
				}
			}
		}
	}
	post {
		always {
			junit '**/target/surefire-reports/TEST-*.xml'
		}
	}
}
