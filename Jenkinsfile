pipeline {
    agent any

    stages {
        stage('clone git repo') {
            steps {
                git branch: 'main', url: 'https://github.com/Ivanmanueli/jk-public-gh.git'
            }
        }
        
        stage('build image') {
            steps {
                sh 'docker build -t webapp:${BUILD_NUMBER} .'
            }
        }
        
        stage('deploy') {
            steps {
               // sh 'docker stop webapp_ctr'
                sh 'docker run --rm -d -p 3000:3000 --name webapp_ctr webapp:${BUILD_NUMBER}'
            }
        }
    }
}
