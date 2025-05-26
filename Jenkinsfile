pipeline{
    agent any
     tools {
        maven 'maven-399' 
    }
    environment{
        env_url = "www.google.com"
    }
    parameters {
        string(name: 'PERSON', defaultValue: 'Mr Jenkins', description: 'Who should I say hello to?')
        text(name: 'BIOGRAPHY', defaultValue: '', description: 'Enter some information about the person')
        booleanParam(name: 'TOGGLE', defaultValue: true, description: 'Toggle this value')
        choice(name: 'CHOICE', choices: ['One', 'Two', 'Three'], description: 'Pick something')
        password(name: 'PASSWORD', defaultValue: 'SECRET', description: 'Enter a password')
    }
    options { buildDiscarder(logRotator(numToKeepStr: '10')) 
              timeout(time: 1, unit: 'MINUTES')
            }
    triggers { pollSCM('*/1 * * * *') }
    stages {
        stage ("Print Hello"){
            steps{
                sh "echo Hello world"
                sh "echo name of the site is ${env_url}"
                sh "mvn --version"

            }
        }
        stage('parallel staging'){
            parallel {
                stage('Branch A'){
                    steps{
                    sh "echo branch A on parallel task"    
                }
            }
                stage('Branch B'){
                    steps{
                        sh "echo branch B on parallel task"
                }
            }

        }
        }
        
        stage ("Welcome All"){
            environment{
                env_url = "www.yahoo.com"
            }
            steps{
                sh "echo Welcome to India"
                sh "echo Name of the site is ${env_url}"
            }
        }
    }

}