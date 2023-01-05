pipeline {
    agent any

    stages {
        stage('Building') {
            steps {
                // Pull the code from Github
                git url: 'https://github.com/HOPierre-Louis/CI-with-github.git/'
            }
        }
        stage('Testing') {
            steps {
                // Install the python flask application and run the tests
                sh 'pip install -r requirements.txt'
                sh 'python -m unitest'
            }
        }
        stage('Deploying') {
            steps {
                // Build the Docker image
                sh 'docker build -t <your_image_name> .'
                // Run a docker container from the image
                sh 'docker run -d -p 5000:5000 <your_image_name>'
            }
        }
    }

    // Listen for Github webhooks
    triggers {
        githubPush()
    }
}
