def app

pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                script {
                    git branch: 'main',
                        credentialsId: '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',
                        url: 'https://github.com/arendelle123/jenkins.git'
                }
            }
        }

        stage('Ready') {
            steps {
                sh "echo 'Ready to build'"
            }
        }

        stage('Build') {
            steps {
                sh "echo 'Build Spring Boot Jar'"
            }
        }

        stage('Build image') {
            steps {
                app = docker.build("211.183.3.100/test/nginx")
            }
        }

        stage('Push image') {
            steps {
                script {
                    docker.withRegistry("http://211.183.3.100", "admin") {
                        app.push("22")
                        app.push("latest-01") // Assign tag. latest-01, 22
                    }
                }
            }
        }

        stage('Complete') {
            steps {
                sh "echo 'The end'"
            }
        }
    }
}
