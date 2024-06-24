pipeline {
    agent {
        docker { 
            image 'node'
        }
    }

    stages {
        stage('Test') {
            steps {
                sh 'npm install -g newman'
                sh 'newman run jenkins-api.postman_collection.json -e jenkins.postman_environment.json -r cli'
            }
        }
    }
}