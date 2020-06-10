pipeline {
	agent { docker { image 'python:3.5.1' } }

	stages {
		stage('Build') {
			steps {
				sh 'echo "Hello World"'
				sh '''
				    echo "bla bla bla multiline"
				    ls -lah
				'''
			}
		}
		stage('Test') {
			steps {
				echo 'Testing...'
			}
		}
		stage('Deploy') {
			steps {
				timeout(time: 1, unit: 'MINUTES') {
				    sh './health-check.sh'
				}
			}
		}
	}
}
