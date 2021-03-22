pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
               checkout changelog: false, poll: false, scm: [$class: 'GitSCM', branches: [[name: '*/master']], doGenerateSubmoduleConfigurations: false, extensions: [], submoduleCfg: [], userRemoteConfigs: [[credentialsId: '343b9756-1de0-4596-b05b-519784e70a4a', url: 'https://github.com/Ajayvarma8142/angular-app-kubernetes.git']]]
            }
        }
        stage('NPM Build') {
            steps {
               bat label: '', script: 'npm install && npm install -g grunt-cli && npm run build'
            }
        }
        stage('Code quality') {
            steps {
               bat label: '', script: 'npm install sonar-scanner && npm run sonar'
            }
        }
    }
}

