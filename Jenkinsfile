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
	post {
		always {
			echo 'This will always run'
		}
		success {
			echo 'This will run only if successful'
		}
		failure {
            echo 'This will run only if failed'
        }
        unstable {
            echo 'This will run only if the run was marked as unstable'
        }
        changed {
            echo 'This will run only if the state of the Pipeline has changed'
            echo 'For example, if the Pipeline was previously failing but is now successful'
        }
	}
}
