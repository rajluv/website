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
        stage('Build and Publish') {
            when {
                branch 'master'
            }
            steps {
                // Build and publish website on port 82 if commit is made to master branch
                script {
                    sh 'docker build -t website-builder -f Dockerfile .'
                    sh 'docker run -d -p 82:80 --name website-container website-builder'
                }
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
