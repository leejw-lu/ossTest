node {
    def app
    stage('Clone repository') {
        git 'https://github.com/leejw-lu/ossTest.git'
    }
    stage('Build image') {
        app = docker.build("jiwoo22/prbasedtest")
    }
    stage('Test image') {
        app.inside {
            sh 'make test'
        }
    }
    stage('Push image') {
        docker.withRegistry('https://registry.hub.docker.com', 'dockerhub') {
           app.push("${env.BUILD_NUMBER}")
           app.push("latest")
        }
    }
}
