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
        stage("Basic master") {
            steps {
                echo "--> This is base master"
                echo "--> We will not change this stage""
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
        stage("S2 runs ps -ef PR will echo after lsof") {
            steps {
                echo "--> Run lsof"
                sh "lsof | grep -v \"Permission denied\""
            }
        }
        stage("S3 sleep 10 seconds new master will change this to 5 seconds") {
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
