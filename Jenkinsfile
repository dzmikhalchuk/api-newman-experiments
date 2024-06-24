pipeline {
    agent {
        docker { 
            image 'node'
            args '-u root:root'
        }
    }

    environment {
        NPM_CONFIG_CACHE = "${WORKSPACE}/.npm"
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