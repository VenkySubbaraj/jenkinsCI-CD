pipeline {
    agent any
    
    stages {
        stage('Build') {
            steps {
                script {
                    // Set the Docker image name and version
                    def imageName = 'venkysubbaraj/sample'
                    def imageVersion = '1.0.0'
                    
                    // Build the Docker image
                    sh "docker build -t ${imageName}:${imageVersion} ."
                }
            }
        }
        
        stage('Push') {
            steps {
                script {
                    // Set the Docker image name and version
                    def imageName = 'venkysubbaraj/sample'
                    def imageVersion = '1.0.0'

                    withCredentials([usernamePassword(credentialsId: 'dockercredentials', passwordVariable: 'PASSWORD', usernameVariable: 'USERNAME')]) {
                        sh '''
                        echo ${PASSWORD} | docker login --username ${USERNAME} --password-stdin
                        '''
                        sh "docker push ${imageName}:${imageVersion}"
                    // Login to Docker Hub
                    // withDockerRegistry([credentialsId: 'dockercredentials', url: '']) {
                        // Push the Docker image
                        
                    // }
                }
            }
        }
    }
}
