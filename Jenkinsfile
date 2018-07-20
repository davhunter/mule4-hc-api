pipeline {
	agent any
	stages {
		stage('Build') {
			steps {
				sh 'mvn clean package deploy -Dhttp.port=8084'
			}
		}
	}
	post {
		always {
			echo 'finished build'
			deleteDir()
		}
		success {
			mail to: 'davhunter@deloitte.ca',
			     subject: "Build completed: ${currentBuild.fullDisplayName}",
			     body: "Build successfully completed. ${env.BUILD_URL}"
		}
		failure {
			mail to: 'davhunter@deloitte.ca',
			     subject: "Failed pipeline: ${currentBuild.fullDisplayName}",
			     body: "Something is wrong with ${env.BUILD_URL}"
		}
	}
}