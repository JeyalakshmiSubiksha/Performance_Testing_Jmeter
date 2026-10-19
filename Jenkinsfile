
pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                echo 'Repository checked out successfully'
            }
        }

        stage('Check JMeter') {
            steps {
                bat '"C:\\Users\\UTIS LAPTOP 624\\Downloads\\apache-jmeter-5.6.3\\apache-jmeter-5.6.3\\bin\\jmeter.bat" -v'
            }
        }

        
stage('Run Performance Test') {
    steps {
        bat '''
            if exist html-report rmdir /s /q html-report
            if exist results.jtl del /q results.jtl

            "C:\\Users\\UTIS LAPTOP 624\\Downloads\\apache-jmeter-5.6.3\\apache-jmeter-5.6.3\\bin\\jmeter.bat" -n -t "Ecommerce_API_TestPlan.jmx" -l results.jtl -e -o html-report
        '''
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
