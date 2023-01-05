pipeline {
    agent any

    stages {
        stage('Building') {
            steps {
                sh 'pip3 install -r requirements.txt'
            }
        }
        stage('Testing') {
            steps {
                sh 'python3 -m unittest'
            }
        }
        stage('Deploying') {
            steps {
                // Build the Docker image
                sh 'docker build -t github-jenkins .'
                // Run a docker container from the image
                sh 'docker run -d -p 6003:5000 github-jenkins'
            }
        }
    }

    // Listen for Github webhooks
    triggers {
        githubPush()
    }
}
