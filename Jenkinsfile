pipeline {
    agent any

    stages {
        stage('Building') {
            steps {
                sh 'pip --version'
            }
        }
        stage('Testing') {
            steps {
                
                sh 'python -m unitest'
            }
        }
        stage('Deploying') {
            steps {
                sh 'docker build -t jenkins .'
                sh 'docker run -d -p 5000:5000 jenkins'
            }
        }
    }

    triggers {
        githubPush()
    }
}
