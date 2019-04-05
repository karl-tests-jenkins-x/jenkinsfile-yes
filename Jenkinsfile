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
                    echo "Depends on the SHOULD_I_NETSTAT param"
                    return params.SHOULD_I_NETSTAT
                }
            }
            steps {
                sh "netstat -a"
            }
        }
        stage("S2 runs ps -ef") {
            steps {
                echo "--> Run lsof"
                sh "lsof"
            }
        }
        stage("S3 sleep 10 seconds") {
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
