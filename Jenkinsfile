pipeline {
    agent any

    stages {
        stage('Git checkout') {
            steps{
                // Get source code from a GitHub repository
                git branch:'main', url:'https://github.com/nini1108/openhack-devops-team/'
            }
        }
        
        stage('Build') {
            steps{
                // Do your build task
                dir("./apis/trips/") {
                sh '/usr/local/go/bin/go build -o main .'
                }
            }
        }
        
        stage('Test') {
            steps{
                // Run unit tests, integration tests, and/or e2e tests
                dir("./apis/trips/") {
                sh '/usr/local/go/bin/go test ./tripsgo -run Unit'
                sh '/usr/local/go/bin/go test ./tripsgo'
                }
            }
        }
        
        stage('Get') {
            steps{
                // Publish your artifacts to somewhere.
                // However, in our hands-on, you just need to print the artifact list by Linux command 'ls -la'
                dir("./apis/trips/") {
                sh '/usr/local/go/bin/go get -d'
                }
            }
        }

        post {
            always { 
                echo 'I will always say Hello again!'
            }
        }
    }
}
