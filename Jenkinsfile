pipeline{

	agent any

	environment {
		DOCKERHUB_CREDENTIALS=credentials('cicd')
	}

	stages {

		stage('Build') {

			steps {
				sh 'docker build -t eaglehaslanded/deneme123:latest .'
			}
		}

		stage('Login') {

			steps {
				sh 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'
			}
		}

		stage('Push') {

			steps {
				sh 'docker push eaglehaslanded/deneme123:latest'
			}
		}
	}

	post {
		always {
			sh 'docker logout'
		}
	}

}