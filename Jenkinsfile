pipeline{
    agent any
    environment{
        env_url = "www.google.com"
    }
    stages {
        stage ("Print Hello"){
            steps{
                sh "echo Hello world"
                sh "echo name of the site is ${env_url}"

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