node{
	def mvnHome
		stage("Preparation") {
				git 'https://github.com/onofreiAdina/PracticaAIS1.git'
				mvnHome = tool "M3"
		}
		stage("Test") {			
				script {
					if(isUnix()) {
						sh "mvn test"
					} else {
						bat(/"${mvnHome}\bin\mvn" test/)
					}
				}
			
		}
	
	stage("Results") {
		always {
			junit '**/target/surefire-reports/TEST-*.xml'
		}
	}
}
