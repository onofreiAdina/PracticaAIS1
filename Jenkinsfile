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
		stage("Create jar"){
			steps{
				sh "mvn package -DskipTests"
			}
		}
		stage("Start app"){
			steps{
				sh "src/target; java -jar cd tictactoe-enunciado-0.0.1-SNAPSHOT.jar > out.log & echo  \$! > pid"
			}
		}
		stage("Test") {
			steps {
				sh "mvn test"
			}
		}
	}
	post {
		always {
			junit '**/target/surefire-reports/TEST-*.xml'
			sh "kill cd \$(cat src/target/pid)"
			archive "cd src/target/out.log"
		}
		success{
			archive "cd src/target/*.jar"
		}
	}
}
