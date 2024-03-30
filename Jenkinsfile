pipeline {
    agent any
    stages {
        stage('Proxy') {
            steps {
                sh 'export http_proxy="http://192.168.101.49:7890"'
            }
        }
        stage('Build') {
            steps {
                sh 'mvn -B -DskipTests clean package'
            }
        }
        stage('Test') {
            steps {
                sh 'mvn test'
            }
            post {
                always {
                    junit 'target/surefire-reports/*.xml'
                }
            }
        }
    }
}