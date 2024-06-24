pipeline {
    agent {
        docker { 
            image 'postman/newman'
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