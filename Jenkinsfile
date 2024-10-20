pipeline {
    // agent
    agent {
        node {
            label 'agent-1'
            
        }
    }
    environment{
        GREETING = 'Hello Jenkins'
    }
    options{
        disableConcurrentBuilds()
    }
    parameters {
        string(name: 'PERSON', defaultValue: 'Mr Jenkins', description: 'Who should I say hello to?')

        text(name: 'BIOGRAPHY', defaultValue: '', description: 'Enter some information about the person')

        booleanParam(name: 'TOGGLE', defaultValue: true, description: 'Toggle this value')

        choice(name: 'CHOICE', choices: ['One', 'Two', 'Three'], description: 'Pick something')

        password(name: 'PASSWORD', defaultValue: 'SECRET', description: 'Enter a password')
    }

    // Build
    stages {
        stage('Build') {
            steps {
                echo 'Hello World - building'
            }
        }
        stage('Test') {
            steps {
                sh """
                    echo "Here I wrote shell script"
                """
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying'
            }
        }
        stage('testing params'){
            steps{
                echo "Hello ${params.PERSON}"

                echo "Biography: ${params.BIOGRAPHY}"

                echo "Toggle: ${params.TOGGLE}"

                echo "Choice: ${params.CHOICE}"

                echo "Password: ${params.PASSWORD}"
            }
        }
    }
    // post build
    
    post 
    { 
        always 
        { 
            echo 'I will always say Hello again!'
        }
        failure 
        { 
            echo 'This will run after pipeline failure'
        }
        success
        {
            echo 'This will run after pipeline success'
        }
    }
}