def app

node {
    stage('Checkout'){
        steps {
            git branch: 'main',
        } 
    }

    stage('Ready'){
        sh "echo 'Ready to build'"
    }

    stage('Build'){
        sh "echo 'Build Spring Boot Jar'"
    }
    stage('Build image'){
        app = docker.build("211.183.3.100/test/nginx")
    }

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
