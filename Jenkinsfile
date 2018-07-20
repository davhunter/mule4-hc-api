pipeline {
	agent any
	stages {
		stage('Build') {
			environment {
				ANYPOINT_CREDENTIALS = credentials('CloudHub')
				CH_CLIENT_ID = credentials('CloudHub-Client-ID')
				CH_CLIENT_SECRET = credentials('CloudHub-Client-Secret')
				AUTODISC_APIID = credentials('dataaggregator_autodiscid_sandbox')
			}
			steps {
				sh 'mvn clean package deploy -DmuleDeploy -Dusername=${ANYPOINT_CREDENTIALS_USR} -Dpassword=${ANYPOINT_CREDENTIALS_PSW} -Dhttp.port=8084 -Dch-client-id=$CH_CLIENT_ID -Dch-client-secret=$CH_CLIENT_SECRET -Dapi.id=$AUTODISC_APIID'
			}
		}
	}
	/* post {
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
	} */
}