pipeline{
	tools {
   		  maven "M3"
  	 }
	agent any
	def mvnHome
	stages{
		stage("Preparation") {
				git 'https://github.com/onofreiAdina/PracticaAIS1.git'
				mvnHome = tool "M3"
		}
		stage("Test") {	
			steps{
				script {
					env.JAVA_HOME= "${tool 'JDK8'}"
					env.PATH="{env.JAVA_HOME}/bin:${env.PATH}"
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
