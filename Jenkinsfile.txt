
pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                echo 'Repository checked out by Jenkins'
            }
        }

        stage('Check JMeter') {
            steps {
                bat 'jmeter -v'
            }
        }

        stage('Run Performance Test') {
            steps {
                bat 'jmeter -n -t "Ecommerce_API_TestPlan.jmx" -l results.jtl -e -o html-report'
            }
        }
    }

    post {
        always {
            archiveArtifacts artifacts: 'results.jtl,html-report/**',
                allowEmptyArchive: true
        }
    }
}
