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
3/jenkins.git'
        } 
    }

    // mvn 툴 선언하는 stage, 필자의 경우 maven 3.6.0을 사용중
    stage('Ready'){
        sh "echo 'Ready to build'"
    }

    // mvn 빌드로 jar파일을 생성하는 stage
    stage('Build'){
        sh "echo 'Build Spring Boot Jar'"
    }

    //dockerfile기반 빌드하는 stage ,git소스 root에 dockerfile이 있어야한다
    stage('Build image'){
        app = docker.build("211.183.3.100/test/nginx")
    }

    //docker image를 push하는 stage, harbor 
    //docker.withRegistry에 dockerhub는 앞서 설정한 harbor credentials의 ID이다.
    stage('Push image') {
        docker.withRegistry("http://211.183.3.100", "admin") {
            app.push("22")
            app.push("latest-01") // 태그를 부여한다. latest-01, 22
        }
    }

    stage('Complete') {
        sh "echo 'The end'"
    }
  }
