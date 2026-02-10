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

        stage('SonarQube Analysis') {
            steps {
                withSonarQubeEnv('sonarqube') {
                    script {
                        def scannerHome = tool 'SonarQubeScanner'
                        bat """
                        "${scannerHome}\\bin\\sonar-scanner.bat" ^
                        -Dsonar.projectKey=angular-app ^
                        -Dsonar.projectName="Angular App" ^
                        -Dsonar.sources=. ^
                        -Dsonar.host.url=http://localhost:9000
                        """
                    }
                }
            }
        }

    }
}
