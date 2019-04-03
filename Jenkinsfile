pipeline {
    agent master
    stages {
        stage("S1") {
            steps {
                echo "Basic Jenkinsfile"
            }
        }
        stage("S2") {
            when {
                expression {
                    echo "Should I run?"
                    return false
                }
            }
            steps {
                sh "netstat -a"
            }
        }
        stage("S3") {
            steps {
                echo "Sleep 10 seconds"
                sleep 10
            }
        }
    }
}
