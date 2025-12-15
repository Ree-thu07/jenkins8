pipeline {
    agent any

    tools {
        maven 'Maven3'
        jdk 'JDK17'
    }

    triggers {
        githubPush()      // Build on GitHub push
        cron('0 2 * * *') // Nightly build at 2 AM
    }

    stages {
        stage('Checkout Code') {
            steps {
                git branch: 'main',
                    url: 'https://github.com/Ree-thu07/jenkins8.git'
            }
        }

        stage('Build with Maven') {
            steps {
                bat 'mvn clean package'
            }
        }
    }

    post {
        success {
            echo 'Build Successful!'
        }
        failure {
            echo 'Build Failed!'
        }
    }
}
