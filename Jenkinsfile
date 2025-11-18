pipeline {
    agent any

    parameters {
        booleanParam(
            name: 'EXECUTE_TESTS',
            defaultValue: true,
            description: 'Run Test stage?'
        )
    }

    environment {
        MY_TOOL_VERSION = '1.0.3'
    }

    stages {
        stage('Build') {
            steps {
                echo "Building with tool version: ${env.MY_TOOL_VERSION}"
            }
        }

        stage('Test') {
            when {
                expression { return params.EXECUTE_TESTS == true }
            }
            steps {
                echo "Tests running because EXECUTE_TESTS=${params.EXECUTE_TESTS}"
            }
        }

        stage('Deploy') {
            steps {
                echo 'Deploying...'
            }
        }
    }

    post {
        success {
            echo 'Pipeline finished successfully.'
        }
        failure {
            echo 'Pipeline failed. Check console logs.'
        }
        always {
            echo "Post-build actions completed. Using tool version: ${env.MY_TOOL_VERSION}"
        }
    }
}
