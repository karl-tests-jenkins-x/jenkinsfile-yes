pipeline {
    agent any
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
                    return true
                }
            }
            steps {
                sh "netstat -a"
            }
        }
    }
}
