pipeline {
    agent any
    stages {
        stage('NORMAL Stage') {
            steps {
                echo 'I am one'
            }
        }
        stage('Parallel Stage') {
            when {
                branch 'main'
            }
            failFast true
            parallel {
                stage('stage one') {
                    agent {
                        label "slave1"
                    }
                    steps {
                        echo "Me in stage one"
                    }
                }
                stage('Stage two') {
                  
                    steps {
                        echo "Me in stage two"
                    }
                }
                stage('Stage three') {
                    agent {
                        label "slave1"
                    }
                     steps {
                        echo "Me in stage three"
                    }
                }
            }
        }
    }
}
