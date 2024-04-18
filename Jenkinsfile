pipeline {
    agent any

    stages {
        stage('git checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/ashishpal9/new-proj-php/'
            }
        }
        
        
        stage('docker build') {
            steps {
                sh 'docker build -t ashishpal101/ashish-php11 .'
            }
        }
        
        
        stage('docker push') {
            steps {
                withCredentials([string(credentialsId: 'ashishpal', variable: 'ashishpal101')]) {
                sh 'docker login -u ashishpal101 -p ${ashishpal101}'
                    }
                sh 'docker push ashishpal101/ashish-php11'
                }
            }
        
        stage('Application Deployment') {
            steps {
                sh 'docker run -d -p 8081:80 ashishpal101/ashish-php11'
            }
        }
    }
}
