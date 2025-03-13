pipeline {
    agent any
    stages {
        stage('Clone repository') {
            steps {
                checkout([$class: 'GitSCM',
                          branches: [[name: '*/main']],
                          userRemoteConfigs: [[url: 'https://github.com/esha-rathod/PES1UG22CS202_jenkins.git']]])
            } // <- This was missing!  VERY IMPORTANT.
        } // <- and this one

        stage('Build') {
            steps {
                sh 'g++ -o PES1UG22CS202-1 main/hello.cpp' // Compiles C++ file
            }
        }

        stage('Test') {
            steps {
                sh './PES1UG22CS202-1' // Runs the compiled file
            }
        }

        stage('Deploy') {
            steps {
                echo "Deploying the application..."
            }
        }
    }

    post {
        failure {
            echo 'Pipeline failed' // Post action in case of failure
        }
    }
}
