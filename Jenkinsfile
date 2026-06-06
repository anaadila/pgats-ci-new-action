pipeline {
    agent any
     tools {
        nodejs "node 24.16.0"
     }

     stages {
        stage('Checkout') {
            steps {
                checkout([$class: 'GitSCM', branches: [[name: '*/main']], userRemoteConfigs: [[url: 'https://github.com/anaadila/pgats-ci.git']]])
            }
        }

        stage('Instalando Yarn e dependências') {
            steps {
                sh 'npm install -g yarn'
                sh 'yarn'
            }
        }

        stage('Instalando Browsers do Playwright') {
            steps {
                sh 'yarn playwright install'
            }
        }

        stage('Executando testes E2E') {
            steps {
                sh 'yarn run e2e'
            }
        }
     }
}