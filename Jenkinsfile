pipeline {
    agent any
    
    stages {
        stage('Build') {
            steps {
                sh 'docker build -t my-app .'
            }
        }
        
        stage('Test') {
            steps {
                sh 'docker run my-app npm test'
            }
        }
        
        stage('Deploy') {
            steps {
                script {
                    def kubectl = tool name: 'kubectl', type: 'ToolType'
                    sh "${kubectl} apply -f kubernetes/deployment.yaml"
                }
            }
        }
    }
}
