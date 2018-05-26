node{
	def mvnHome
		stage("Preparation") {
				git 'https://github.com/onofreiAdina/PracticaAIS1.git'
				mvnHome = tool "M3"
		}
		stage("Test") {		
			env.JAVA_HOME= "${tool 'JDK8'}"
			env.PATH="{env.JAVA_HOME}/bin:${env.PATH}"
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
