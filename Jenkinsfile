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

     post {
        always {
            archiveArtifacts artifacts: 'reports/**, playwright-report/**', allowEmptyArchive: true        
            
            publishHTML(target: [
                allowMissing: true,
                alwaysLinkToLastBuild: true,
                keepAll: true,
                reportDir: 'reports/coverage/lcov-report',
                reportFiles: 'index.html',
                reportName: 'Unit Test Report'
            ])

            publishHTML(target: [
                allowMissing: true,
                alwaysLinkToLastBuild: true,
                keepAll: true,
                reportDir: 'reports/mutation',
                reportFiles: 'mutation.html',
                reportName: 'Mutation Test Report'
            ])

            publishHTML(target: [
                allowMissing: true,
                alwaysLinkToLastBuild: true,
                keepAll: true,
                reportDir: 'playwright-report',
                reportFiles: 'index.html',
                reportName: 'E2E Test Report'
            ])

            }
     }
}