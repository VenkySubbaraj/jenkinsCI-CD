pipeline {
    agent any
    
    stages {
        stage('Clean-docker-image') {
            steps {
                script {
                    // removes all docker images
                    sh 'docker image prune -a --force'
                    sh 'docker image ls'
                }
            }
        }
        
        stage('Build and Push') {
            steps {
                script {
                    // Set the Docker image name and version
                    def imageName = 'venkysubbaraj/sample-node-app'
                    def imageVersion = '1.0.0'

                    withCredentials([usernamePassword(credentialsId: 'dockercredentials', passwordVariable: 'PASSWORD', usernameVariable: 'USERNAME')]) {
                        sh '''
                        echo ${PASSWORD} | docker login --username ${USERNAME} --password-stdin
                        '''
                        sh "docker build -t ${imageName}:${imageVersion} ."
                        sh 'docker push ${imageName}:${imageVersion}'
                        
                    }
                }
            }
        }
    }
}
