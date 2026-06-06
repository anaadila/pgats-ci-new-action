pipeline {
    agent {
        label 'linux'
    }

     tools {
        nodejs "node 24.16.0"
     }

     stages {

        stage('Checkout') {
            steps {
                git branch: 'master',
                    url: 'https://github.com/anaadila/pgats-ci.git'
            }
        }

        stage('Instalando Yarn') {
            steps {
                sh 'npm install -g yarn'
            }
        }

        stage('Instalando Dependências') {
            steps {
                sh 'yarn install'
            }

        }

        stage('Instalando Browsers do Playwright') {
            steps {
                sh 'yarn playwright install --with-deps'
            }
        }

        stage('Executando testes E2E') {
            steps {
                sh 'yarn run e2e'
            }
        }
     }
}