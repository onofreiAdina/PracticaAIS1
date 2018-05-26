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
				sh "tic-tac-toe-enunciado/target; java -jar cd tictactoe-enunciado-0.0.1-SNAPSHOT.jar > out.log & echo  \$! > pid"
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
			sh "kill cd \$(cat tic-tac-toe-enunciado/target/pid)"
			archive "cd tic-tac-toe-enunciado/target/out.log"
		}
		success{
			archive "cd tic-tac-toe-enunciado/target/*.jar"
		}
	}
}
