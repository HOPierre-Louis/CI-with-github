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
                sh 'python -m unittest'
            }
        }
        stage('Deploying') {
            steps {
                // Build the Docker image
                sh 'docker build -t github-jenkins-leolb .'
                // Run a docker container from the image
                sh 'docker run -d -p 5000:5000 github-jenkins-leolb'
            }
        }
    }

    // Listen for Github webhooks
    triggers {
        githubPush()
    }
}
