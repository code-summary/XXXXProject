pipeline {
    agent any
    stages {
        stage('Select Branch') {
            steps {
                script {
                    env.BRANCH_NAME = input(
                        id: 'branch',
                        message: 'Which branch to deploy?',
                        parameters: [string(defaultValue: 'master', description: 'Branch name', name: 'BRANCH')]
                    )
                    env.DEPLOY_PATH = input(
                        id: 'path',
                        message: 'Where to deploy?',
                        parameters: [string(defaultValue: '/opt/myapp', description: 'Deploy path', name: 'DEPLOY_PATH')]
                    )
                    env.PORT = input(
                        id: 'port',
                        message: 'Which port to use?',
                        parameters: [string(defaultValue: '8080', description: 'Port number', name: 'PORT')]
                    )
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
