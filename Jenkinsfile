pipeline {
    agent any
    stages {
        stage('git') {
            steps {
            git branch: 'main',
                   url: 'https://github.com/maheshryali/saleor-dashboard.git'
           }
        }
        stage('docker') {
            steps {
            sh """
            docker image build -t saleor:1.0 .
            docker container run -d saleor:1.0 
            docker tag saleor:1.0 maheshryali/newimage:1.0
            cat ~/file.txt | docker login --username maheshryali --password-stdin
            docker push maheshryali/newimage:1.0
            """
            }
        }
    }
}
