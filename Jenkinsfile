pipeline {
    agent {
        kubernetes {
            label 'pod'
            defaultContainer 'jnlp'
             yaml """
apiVersion: v1
kind: Pod
spec:
  containers:
  - name: maven
    image: maven:alpine
    command:
    - cat
    tty: true
"""
    }
  }
    stages {
        stage('Deploy') {
            steps {
                container('maven') {
                    sh 'mvn deploy'
                }
            }
        }
    }
}