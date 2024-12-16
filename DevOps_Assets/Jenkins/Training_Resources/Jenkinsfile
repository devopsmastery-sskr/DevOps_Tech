pipeline{
    agent {
        label 'AGENT-1'
    }
    options{
        timeout(time: 1, unit: 'HOURS')
        disableConcurrentBuilds()
        //ansiColor('xterm')//to see colors in console, plugin
     }
    environment{
        NAME = 'PROD'
        TYPE = 'JAVABased'
    }
    parameters {
        string(name: 'PERSON', defaultValue: 'Mr Jenkins', description: 'Who should I say hello to?')
        text(name: 'BIOGRAPHY', defaultValue: '', description: 'Enter some information about the person')
        booleanParam(name: 'TOGGLE', defaultValue: true, description: 'Toggle this value')
        choice(name: 'CHOICE', choices: ['One', 'Two', 'Three'], description: 'Pick something')
        password(name: 'PASSWORD', defaultValue: 'SECRET', description: 'Enter a password')
    }

    stages{
        stage('test'){
            steps {
                sh 'env'
                echo "heloo jenkins pipeline job"
            }
        }
        stage('sleep stage'){
            steps{
                sh 'sleep 10'
                echo 'this for testing'
            }
        }
        stage('accesing parameters'){
            steps{
                echo "Hello ${params.PERSON}"
                echo "Biography: ${params.BIOGRAPHY}"
                echo "Toggle: ${params.TOGGLE}"
                echo "Choice: ${params.CHOICE}"
                echo "Password: ${params.PASSWORD}"
                echo "testing github web-hook"
                error "intentional failure"
            }
        }
    }
    post{
        always{
            echo "always  build"
            deleteDir() //always delete this project in bknd after job exec.
        }
        failure{
            sh 'echo "during failures"'
            }
        
        success{
            echo "during success"
        }


    }
}
