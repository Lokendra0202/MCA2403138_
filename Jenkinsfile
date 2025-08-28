pipeline {
    agent any

    parameters {
        string(name: 'BUILD_NUMBER_INPUT', defaultValue: '', description: 'Enter the current build number')
    }

    stages {
        stage('Build') {
            when {
                branch 'development'
            }
            steps {
                echo 'Building the project... (only on development branch)'
                // Add your build commands here, e.g.:
                // sh 'make build'
            }
        }

        stage('Test') {
            steps {
                echo 'Running tests... (on all branches)'
                // Add your test commands here, e.g.:
                // sh 'make test'
            }
        }

        stage('Deploy') {
            steps {
                script {
                    if (params.BUILD_NUMBER_INPUT?.trim()) {
                        echo "Deploying build number: ${params.BUILD_NUMBER_INPUT}"
                        // Add your deploy commands here, e.g.:
                        // sh "deploy.sh --build ${params.BUILD_NUMBER_INPUT}"
                    } else {
                        error("Build number not provided! Please provide BUILD_NUMBER_INPUT parameter.")
                    }
                }
            }
        }
    }
}
