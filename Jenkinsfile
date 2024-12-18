pipeline {
    agent any

    stages {
        stage('Clonar Repositório') {
            steps {
                git branch: 'main', url: 'https://github.com/wallafidevops/jk-public-gh.git'
            }
        }
        stage('Build') {
            steps {
                sh 'docker build -t webapp:${BUILD_NUMBER} .'
            }
        }
        stage('Deploy') {
            steps {
                sh '''
               #  docker stop webapp_ctr || true
               #  docker rm webapp_ctr || true
                docker run --rm -d -p 3000:3000 --name webapp_ctr webapp:${BUILD_NUMBER}
                '''
            }
        }        
    }
}
