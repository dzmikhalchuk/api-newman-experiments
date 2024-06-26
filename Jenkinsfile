pipeline {
    agent {
        docker { 
            image 'node'
            args '-u root:root'
        }
    }

    options {
        skipDefaultCheckout(true)
    }

    environment {
        NPM_CONFIG_CACHE = "${WORKSPACE}/.npm"
    }

    stages {
        stage('Checkout. Install newman and newman-reporter-htmlextra') {
            steps {
                checkout scm
                sh 'npm install -g newman'
                sh 'npm install -g newman-reporter-htmlextra'
            }
        }
        stage('Test') {
            steps {
                sh 'newman run jenkins-api.postman_collection.json -e jenkins.postman_environment.json -r htmlextra,cli,junit --reporter-htmlextra-export newman/report.html --reporter-htmlextra-title "External API Report" --reporter-junit-export newman/report.xml'
            }
        }
    }

    post {
    success {
      publishHTML([allowMissing: false, alwaysLinkToLastBuild: false, keepAll: false, reportDir: 'newman', reportFiles: 'report.html', reportName: 'External API Report', reportTitles: '', useWrapperFileDirectly: true])
    }
  }
}