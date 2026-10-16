
stage('Check JMeter') {
    steps {
        bat '"C:\\Users\\UTIS LAPTOP 624\\Downloads\\apache-jmeter-5.6.3\\apache-jmeter-5.6.3\\bin\\jmeter.bat" -v'
    }
}

stage('Run Performance Test') {
    steps {
        bat '"C:\\Users\\UTIS LAPTOP 624\\Downloads\\apache-jmeter-5.6.3\\apache-jmeter-5.6.3\\bin\\jmeter.bat" -n -t "Ecommerce_API_TestPlan.jmx" -l results.jtl -e -o html-report'
    }
}
