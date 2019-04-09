pipeline {
    environment {
        ONE_VARIABLE    = "1"
        TWO_VARIABLE    = "2"
        RED_VARIABLE    = "red"
        BLUE_VARIABLE   = "blue"
        BRANCH_VARIABLE = "test-my-jenkinsfile"
    }
    parameters {
        booleanParam defaultValue: true, description: 'Should we run netstat', name: 'SHOULD_I_NETSTAT'
    }
    agent {
        label "master"
    }
    stages {
        stage("Echo some env vars") {
            steps {
                echo "--> Our variables are ${env.ONE_VARIABLE}, ${env.TWO_VARIABLE}, ${env.RED_VARIABLE}, ${env.BLUE_VARIABLE}, "
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
        stage("S2 only if branch == master") {
            when {
                branch 'master'
            }
            steps {
                echo "--> HELLO FROM MASTER"
                sh "ls -alhR"
            }
        }
        stage("S3 only if branch != master") {
            when {
                not {
                    branch 'master'
                }
            }
            steps {
                echo "--> NOT MASTER"
                sh "ps -ef"
            }
        }
        stage("S4 only if PR branch") {
            when {
                branch 'PR*'
            }
            steps {
                echo "--> PR Branch"
                sh "du -h -d 1"
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
