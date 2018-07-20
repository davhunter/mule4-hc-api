pipeline {
	agent any
	stages {
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
		success {
		}
		unstable {
		}
		failure {
			mail to: 'davhunter@deloitte.ca',
			     subject: "Failed pipeline: ${currentBuild.fullDisplayName}",
			     body: "Something is wrong with ${env.BUILD_URL}"
		}
		changed {
		}
	}
}