pipeline {
	agent any
	tools {
		maven 'Maven 3.3.9'
		jdk 'jdk8'
	}
	stages {
		stage('Initialize') {
			steps {
				sh '''
					echo "PATH = ${PATH}"
					echo "M2_HOME = ${M2_HOME}"
			}
		}
		stage('Build') {
			steps {
				echo 'this is a minimal pipeline.'
			}
		}
	}
	post {
		always {
			echo 'finished build'
			deleteDir()
		}
		failure {
			mail to: 'davhunter@deloitte.ca',
			     subject: "Failed pipeline: ${currentBuild.fullDisplayName}",
			     body: "Something is wrong with ${env.BUILD_URL}"
		}
	}
}