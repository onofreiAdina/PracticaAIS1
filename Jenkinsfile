node{
	def mvnHome
	agent any
	stages {
		stage("Preparation") {
				git 'https://github.com/onofreiAdina/PracticaAIS1.git'
				mvnHome = tool "M3"
		}
		stage("Test") {
			steps {				
				script {
					if(isUnix()) {
						sh "mvn test"
					} else {
						bat(/"${mvnHome}\bin\mvn" test/)
					}
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
