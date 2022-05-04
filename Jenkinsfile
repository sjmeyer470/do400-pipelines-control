pipeline {


    agent {
        node {
            label 'nodejs'
        }
    }

    parameters {
        booleanParam(name: "RUNE_FRONTEND_TESTS", defaultsValue: true)
    }
   
    
    stages{
        stage('Run Tests'){
            parallel {
                stage('Backend Tests'){
                    steps {
                        sh 'node ./backend/test.js'
                    }
                }
            

                stage('Frontend Tests'){
                    when { expression { params.RUNE_FRONTEND_TESTS}}
                    steps {
                        sh 'node ./frontend/test.js'
                    }
            
                } 
            }
        }
        
    }
}
