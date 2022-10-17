pipeline {
    agent none
    
    tools { 
        maven 'MAVEN1' 
        
    }
    stages {
         parallel {
        stage ('Initialize') {
             agent {
              node 'slave1'
              }
            steps {
                sh '''
                    echo "PATH = ${PATH}"
                    echo "M2_HOME = ${M2_HOME}"
                ''' 
            }
        }

        stage ('Build') {
            steps {
                sh 'mvn clean install'
            }
        }
         }
         }

}
