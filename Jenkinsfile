pipeline {
    agent any 
    // ou
    // agent {
    //     node {
    //        label 'build'
    //    }
    // }

    tools {
        maven 'M2_HOME'
    }

    options {
        // Timeout counter starts after agent is allocated
        timeout(time: 15, unit: 'SECONDS')
    }

    environment {
        APP_ENV = "DEV"
    }

    stages {
        stage('Code Checkout') {
            steps {
                git branch: 'main',
                    url: 'https://github.com/fersihela/Devops.git',
                    credentialsId: 'github-pat-helaf'
            }
        }

        stage('Code Build') {
            steps {
                sh 'mvn install -Dmaven.test.skip=true'
            }
        }
    }

    post {
        always {
            echo "======always======"
        }
        success {
            echo "=====pipeline executed successfully====="
        }
        failure {
            echo "======pipeline execution failed======"
        }
    }
}
