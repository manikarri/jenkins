pipeline {
    agent any
    tools { 
        maven 'MAVEN1' 
        
    }
    stages {
        stage ('Initialize') {
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
        stage ('deploy') {
        //     when {
         //       branch 'main'
        //    }
             input {
                message "Can we Proceed?"
                ok "Yes"
                submitter "padmaraju"
                parameters {
                    string(name: 'PERSON', defaultValue: 'padmaraju', description: 'Member')
                }
            }
            steps {
              deploy adapters: [tomcat9(credentialsId: 'tomcatDeployCred', path: '', url: 'http://15.206.125.129:8080/')], contextPath: 'sampletomcatwebapp', war: '**/*.war'  
           }
            
        }
        
    }
}
