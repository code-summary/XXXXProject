pipeline {
    agent any
    parameters {
        extendedChoice description: 'Which branch to deploy?',
        multiSelectDelimiter: ',', name: 'BRANCH', quoteValue: false,
        saveJSONParameterToFile: false, type: 'PT_SINGLE_SELECT', value: 'master\nfeature-1\nfeature-2'
    }
    stages {
        stage('Select Path and Port') {
            steps {
                script {
                    env.DEPLOY_PATH = "${params.BRANCH}".equals("master") ? "/opt/myapp" : "/opt/myapp-${params.BRANCH}"
                    env.PORT = "${params.BRANCH}".equals("master") ? "8080" : "8081"
                }
            }
        }
        stage('Build') {
            steps {
                sh 'echo "Building..."'
            }
        }
        stage('Test') {
            steps {
                sh 'echo "Testing..."'
            }
        }
        stage('Deploy') {
            steps {
                sh "cp target/myapp.jar ${env.DEPLOY_PATH}"
                sh "java -jar ${env.DEPLOY_PATH}/myapp.jar --server.port=${env.PORT}"
            }
        }
    }
}
