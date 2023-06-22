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
                    def imageName = 'your-dockerhub-username/your-image-name'
                    def imageVersion = '1.0.0'
                    
                    // Login to Docker Hub
                    withDockerRegistry([credentialsId: ${dockercredentials}, url: '']) {
                        // Push the Docker image
                        sh "docker push ${imageName}:${imageVersion}"
                    }
                }
            }
        }
    }
}
