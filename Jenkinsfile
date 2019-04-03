pipeline {
    environment {
        ONE_VARIABLE = "1"
        TWO_VARIABLES = "2"
    }
    parameters {
        booleanParam defaultValue: true, description: 'Defaults to something else entirely.', name: 'DEFAULTS_TO_TRUE'
    }
    agent {
        label "master"
    }
    stages {
        stage ("Parallel Wrapper"){
            parallel {
                stage ("in-parallel-1") {
                    steps{
                        echo "in-parallel-1"
                        sh "lsof"
                    }
                }
                stage ("in-parallel-2") {
                    steps{
                        echo "in-parallel-2"
                        sh "lsof"
                    }
                }
            } // end parallel block
        }
        stage("S1") {
            when {
                expression {
                    echo "Expression returns true so netstat will run"
                    return true
                }
            }
            steps {
                sh "netstat -a"
            }
        }
        stage("S2") {
            steps {
                echo "Basic Jenkinsfile"
            }
        }
        stage ("S3") {
            steps {
                echo "Harder to create an intentional conflict than I thought"
                sh "ps -ef"
            }
        }
        stage("S4") {
            steps {
                echo "Sleep 10 seconds"
                sleep 10
            }
        }
    }
}
