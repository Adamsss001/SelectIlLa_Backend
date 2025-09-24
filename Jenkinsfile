pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                echo 'Building SelectIlLa Backend...'
                sh 'npm install'
            }
        }
        stage('Test') {
            steps {
                echo 'Running tests...'
                sh 'npm test'
            }
        }
        stage('SonarQube Analysis') {
            steps {
                withSonarQubeEnv('BillcomSonarQube') {
                    sh 'npx sonar-scanner'
                }
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying application...'
                sh 'docker build -t selectilla-backend .'
            }
        }
    }
}
