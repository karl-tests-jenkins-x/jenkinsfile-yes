pipeline {
    environment {
        ONE_VARIABLE = "1"
        TWO_VARIABLES = "2"
    }
    parameters {
        booleanParam defaultValue: false, description: 'There is no spoon.', name: 'THERE_IS_A_SPOON'
    }
    agent {
        label "master"
    }
    stages {
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
                stage ("in-parallel-3") {
                    steps{
                        echo "in-parallel-3"
                        sh "lsof"
                    }
                }
                stage ("in-parallel-4") {
                    steps{
                        echo "in-parallel-4"
                        sh "lsof"
                    }
                }
            } // end parallel block
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
