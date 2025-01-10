pipeline {
    agent any

    stages {
        stage('Checkout Code') {
            steps {
                git branch: 'main', url: 'https://github.com/kazalbrur/Selenium_Web_Automation_with_Github_Action.git'
            }
        }

        stage('Setup Environment') {
            steps {
                sh 'python -m pip install --upgrade pip'
                sh 'pip install -r requirements.txt'
            }
        }

        stage('Run Selenium Tests') {
            steps {
                sh 'pytest --html=reports/report.html'
            }
        }

        stage('Publish Test Report') {
            steps {
                publishHTML(target: [
                    reportName: 'Selenium Test Report',
                    reportDir: 'reports',
                    reportFiles: 'report.html',
                    keepAll: true,
                    alwaysLinkToLastBuild: true
                ])
            }
        }
    }
}
