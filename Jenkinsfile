pipeline {
    environment {
        ONE_VARIABLE = "1"
        TWO_VARIABLES = "2"
    }
    parameters {
        booleanParam defaultValue: true, description: 'Should we run netstat', name: 'SHOULD_I_NETSTAT'
    }
    agent {
        label "master"
    }
    stages {
        stage("Base Jenkinsfile from master") {
            steps {
                echo "Base Jenkinsfile from master"
            }
        }
        stage("S1 netstat if param is true") {
            when {
                expression {
                    echo "Depends on the DEFAULTS_TO_TRUE param"
                    return params.DEFAULTS_TO_TRUE
                }
            }
            steps {
                sh "netstat -a"
            }
        }
        stage("S2 runs lsof") {
            steps {
                echo "--> Run lsof"
                sh "lsof"
            }
        }
        stage ("S3 runs ps -ef") {
            steps {
                echo "--> Run ps -ef"
                sh "ps -ef"
            }
        }
        stage("S4 sleep 10 seconds") {
            steps {
                echo "Sleep 10 seconds"
                sleep 10
            }
        }
    }
    post{
        always {
            echo "--> post --> always"
        }
        success {
            echo "--> post --> success"
        }
        failure {
            echo "--> post --> failure"
        }
    }
}
