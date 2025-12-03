pipeline {
    agent any

    stages {

        stage('Clone Project') {
            steps {
                git branch: 'master', url: 'https://github.com/PraveenKuberABC/Amazon-Ecom.git'
            }
        }

        stage('Clean') {
            steps {
                sh 'mvn clean'
            }
        }

        stage('Compile') {
            steps {
                sh 'mvn compile'
            }
        }

        stage('Test') {
            steps {
                sh 'mvn test'
            }
        }

        stage('Build') {
            steps {
                sh 'mvn clean install'
            }
        }

    }

    post {
        success {
            mail to: 'arpitha.abc.123@gmail.com',
                 subject: "BUILD SUCCESS: ${env.JOB_NAME} #${env.BUILD_NUMBER}",
                 body: "Hello Arpitha,\n\nThe Jenkins pipeline <${env.JOB_NAME}> build #${env.BUILD_NUMBER} has SUCCESSFULLY completed.\n\nCheck console output: ${env.BUILD_URL}\n\nBest regards,\nJenkins"
        }

        failure {
            mail to: 'arpitha.abc.123@gmail.com',
                 subject: "BUILD FAILURE: ${env.JOB_NAME} #${env.BUILD_NUMBER}",
                 body: "Hello Arpitha,\n\nThe Jenkins pipeline <${env.JOB_NAME}> build #${env.BUILD_NUMBER} has FAILED.\n\nCheck console output: ${env.BUILD_URL}\n\nPlease take necessary action.\n\nBest regards,\nJenkins"
        }
    }
}
