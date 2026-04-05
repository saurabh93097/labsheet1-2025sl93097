pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                echo 'Checking out code...'
            }
        }

        stage('Build') {
            steps {
                sh 'echo Building the application...'
                sh 'ls'
            }
        }

        stage('Test') {
            steps {
                sh 'python3 -c "import calculator; assert calculator.add(2,3) == 5"'
                sh 'python3 -c "import calculator; assert calculator.multiply(2,3) == 6"'
            }
        }

        stage('Deploy') {
            steps {
                sshagent(['ec2-key']){
			sh 'scp -o StrictHostKeyChecking=no calculator.py ubuntu@13.62.56.248/home/ubuntu/'
		}
            }
        }

    }
}
