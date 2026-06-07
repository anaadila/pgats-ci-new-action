pipeline {
    agent {
        label 'mestre'
    }

     tools {
        nodejs "node 24.16.0"
     }

     stages {

        stage('Instalando Yarn') {
            steps {
                bat 'npm install -g yarn'
            }
        }

        stage('Instalando Dependências') {
            steps {
                bat 'yarn install'
            }

        }

        stage('Instalando Browsers do Playwright') {
            steps {
                bat 'yarn playwright install --with-deps'
            }
        }

        stage('Executando testes unitários') {
            steps {
                bat 'yarn run test'
            }
        }

        stage('Executando testes E2E') {
            steps {
                bat 'yarn run e2e'
            }
        }
     }
}