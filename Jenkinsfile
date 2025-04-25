pipeline {
    agent any

    environment {
        WORKDIR = "${env.WORKSPACE}"
    }
    stages {
        stage('Validate') {
            steps {
                sh '''
                    mvn --version
                    ansible --version
                '''
            }
        }
        
        stage('Build') {
            steps {
                sh 'mvn clean package'
            }
        }

        stage('Deploy a container'){
            steps {
                sh 'ansible-playbook jpetstoreplaybook.yml'
            }
        }
    }
    post {
        always{
            cleanWs()
        }
    }
}
