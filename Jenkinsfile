pipeline {
    agent {
        docker { 
            image 'postman/newman'
            args '-it --entrypoint=/bin/bash'
        }
    }

    stages {
        stage('Test') {
            steps {
                sh 'newman run jenkins-api.postman_collection.json -e jenkins.postman_environment.json -r cli'
            }
        }
    }
}