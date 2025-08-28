pipeline {
    agent {
        docker {
            image 'maven:3.9.4-openjdk-17'
            args '-v $HOME/.m2:/root/.m2'
        }
    }
    stages {
        stage('Build') {
            steps {
                sh 'mvn clean package'
            }
        }
        stage('Test') {
            steps {
                sh 'mvn test'
            }
        }
        stage('Deploy Test') {
            when {
                branch 'main'
            }
            steps {
                echo 'Deploy commands here'
            }
        }
    }
}
