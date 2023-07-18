pipeline {
	agent any
	tools {
		maven 'MAVEN3'
		jdk 'JavaJDK11'
	}

	stages {
		stage('Code fetch') {
			steps {
				git branch: 'main', url: 'https://github.com/BalajiVenkatesan123/vprofile-project.git'
			}
		}

		stage('Build') {
			steps {
				sh 'mvn install -DskipTests'
			}

			post {
				success {
					echo "Archiving Artifact now ..."
					archiveArtifacts artifacts: 'target/*.war'
				}
			}
		}

		stage('Unit test') {
			steps {
				sh 'mvn test'
			}
		}
	}
}
