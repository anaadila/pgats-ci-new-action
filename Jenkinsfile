pipeline {
    agent {
        label 'mestre'
    }

     tools {
        nodejs "node 24.16.0"
     }

     stages {

        stage('Setup Environment') {
            steps {
                // Install dependencies
                bat 'npm install -g yarn'

                // Install project dependencies
                bat 'yarn install'

                // Install Playwright browsers and dependencies
                bat 'yarn playwright install --with-deps'
            }
        }

        stage('Unity Tests') {
            steps {
                bat 'yarn run test'
            }
        }

        stage('Mutation Tests') {
            steps {
                bat 'yarn run test:mutation'
            }
        }

        stage('E2E Tests') {
            steps {
                bat 'yarn run e2e'
            }
        }
     }
}