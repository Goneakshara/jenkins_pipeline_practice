
pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                echo 'Source code checkout completed'
            }
        }

        stage('Build') {
            steps {
                echo 'Creating build output'

                sh '''
                    mkdir -p build-output
                    echo "Hello from Jenkins Pipeline" > build-output/message.txt
                    echo "Build completed successfully"
                '''
            }
        }

        stage('Test') {
            steps {
                echo 'Testing build output'

                sh '''
                    test -s build-output/message.txt
                    cat build-output/message.txt
                    echo "Test passed"
                '''
            }
        }

        stage('Archive') {
            steps {
                archiveArtifacts artifacts: 'build-output/message.txt',
                                 fingerprint: true
            }
        }
    }
    
     
post {
    always {
        echo 'Pipeline execution completed'
    }

    success {
        echo 'Congratulations! Pipeline succeeded'
    }

    failure {
        echo 'Pipeline failed. Please check the logs'
    }
}
stage('Test') {
    steps {
        echo 'Testing build output'
        error 'Intentional failure for Jenkins practice'
    }
}

}
