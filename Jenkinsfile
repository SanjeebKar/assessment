pipeline {
    agent any
    tools {
        // Install the Maven version configured as "M3" and add it to the path.
        maven "M3"
    }
    stages {
        stage('Build') {
            steps {                
                git 'https://github.com/SanjeebKar/assessment.git'
                sh "docker build -t jaibw/website004:${env.BUILD_TAG} ."
            }
        }
        stage('Push') {
            steps {
                sh "docker push jaibw/website004:${env.BUILD_TAG}"
            }
        }
        stage('Deploy') {
            steps {
                sh "sed -i 's/username/${env.BUILD_TAG}/g' k8sfile.yaml"
                sh "kubectl apply -f k8sfile.yaml"
                sh "kubectl get svc | grep ${env.BUILD_TAG}"
            }
        }
    }
    }
