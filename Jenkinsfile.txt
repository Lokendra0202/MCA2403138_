pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo 'Building the project...'
                sh 'mvn clean package'
            }
        }

        stage('Test') {
            steps {
                echo 'Running tests...'
                sh 'mvn test'
            }
        }

        stage('Deploy Test') {
            when {
                branch 'main'
            }
            steps {
                echo 'Deploying on main branch only...'
                // Add your deploy commands here, for example:
                sh './deploy-test.sh'
            }
        }
    }
}
