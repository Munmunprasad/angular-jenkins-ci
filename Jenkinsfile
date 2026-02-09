pipeline {
    agent any

    tools {
        nodejs 'nodejs'
    }

    stages {

        stage('Check Node & NPM') {
            steps {
                bat 'node -v'
                bat 'npm -v'
            }
        }

        stage('Install Dependencies') {
            steps {
                bat 'npm install'
            }
        }

        stage('Build Angular Application') {
            steps {
                bat 'npm run build'
            }
        }
    }
}
