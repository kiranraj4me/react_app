node {
stage('Checkout from Github') {
    checkout scm
}
try{

            stage('Unit Tests') {
                sh 'gradle test'
                junit 'build/test-results/test/*.xml'
            }
            stage('Integration Tests') {
                sh 'gradle integrationTest'
                junit 'build/test-results/integrationTest/*.xml'
            }
            stage('Coverage') {
                // generate test report
                sh 'gradle jacocoTestReport'
                // verify minimum coverage
                sh 'gradle jacocoTestCoverageVerification'
            }
            stage('SonarQube') {
                withSonarQubeEnv('SonarQubeServer') {
                    // submit results to SonarQube
                    sh 'gradle sonarqube'
                }
            }
            stage('Quality Gate') {
                timeout(time: 1, unit: 'HOURS') {
                    // TODO: make this a failure criteria once coverage is ready
                    waitForQualityGate abortPipeline: false
                }
            }
            stage('Publish War') {
                sh 'gradle publish'
            }
        }
    }

    stage('Publish Helm Chart') {
        something
    }
} finally {
    something
}
}
