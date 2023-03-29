pipeline {
    agent any

    parameters {
        gitParameter branchFilter: ".*", defaultValue: 'master', name: 'BRANCH', type: 'PT_BRANCH'
    }

    stages {
        stage('Git Checkout') {
          steps {
              checkout([$class: 'GitSCM', branches: [[name: '$BRANCH']], extensions: [], submoduleCfg: [],userRemoteConfigs: [[url: '<your git repository url>']]])
            }
        }

        stage('Build and Deploy') {
            steps {
                sh '''
                sh build.sh
                sh deploy.sh <your deployment directory> <server port>
                '''
            }
        }
    }
}
