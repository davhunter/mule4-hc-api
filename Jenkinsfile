pipeline {
	agent any
	stages {
		stage('Build') {
			environment {
				ANYPOINT_CREDENTIALS = credentials("${ENV}.cloudhub.credentials")
			}
			steps {
				sh 'mvn clean package deploy -DmuleDeploy -Dusername=${ANYPOINT_CREDENTIALS_USR} -Dpassword=${ANYPOINT_CREDENTIALS_PSW} -Dhttp.port=8085'
			}
		}
	}
}