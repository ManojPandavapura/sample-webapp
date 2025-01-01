pipeline {
    agent any

    environment {
        // Set SonarQube details
        SONARQUBE_URL = "httpi//65.0.101.161:9000"
        SONARQUBE_CREDENTIALS = "sqa_3ef9ba47fd8e1c2041cd7124919269d3ff7bd7b6"
    }

    stages {
        stage('Checkout') {
            steps {
                // Checkout your code from SCM (e.g., GitHub)
                git 'https://github.com/ManojPandavapura/sample-webapp.git'
            }
        }

        stage('Build') {
            steps {
                script {
                    // Run Maven build
                    sh "mvn clean install"
                }
            }
        }

        stage('SonarQube Analysis') {
            steps {
                script {
                    // Run SonarQube scan
                    sh "mvn sonar:sonar -Dsonar.projectKey=my_project_key -Dsonar.host.url=${SONARQUBE_URL} -Dsonar.login=${SONARQUBE_CREDENTIALS}"
                }
            }
        }
    }
}
