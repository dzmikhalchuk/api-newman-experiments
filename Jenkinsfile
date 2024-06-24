pipeline {
    agent {
        docker { image 'dannydainton/htmlextra' }
    }

    stages {
        stage('Test') {
            steps {
                sh 'newman run jenkins-api.postman_collection.json -e jenkins.postman_environment.json -r cli'
            }
        }
    }
}