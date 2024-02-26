pipeline {
    agent {
        label 'slave'
    }
    stages {
        stage('Checkout') {
            steps {
                // Checkout code from Git repository
                git url: 'https://github.com/rajluv/website.git'
            }
        }
        stage('Build Only') {
            when {
                branch 'develop'
            }
            steps {
                // Build the product if commit is made to develop branch
                script {
                    sh 'docker build -t website-builder -f Dockerfile .'
                }
            }
        }
    }
}
