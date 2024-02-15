pipeline {
    agent any

    stages {
        stage('Cloning Git Repository') {
            steps {
                git branch: 'main', url: 'https://github.com/Loolo100/jk-public-gh.git'
            }
        }
        
        stage('Building Image') {
            steps {
                sh 'docker build -t webapp:${BUILD_NUMBER} .'
            }
        }
            
        stage('Deploying Application') {
            steps {
                script {
                    // Stop the container
                    // sh 'docker stop webapp_ctr || true'

                    // Run the container
                    sh "docker run --rm -d -p 3000:3000 --name webapp_ctr webapp:${BUILD_NUMBER}"
                }
            }
        }
    }
}
