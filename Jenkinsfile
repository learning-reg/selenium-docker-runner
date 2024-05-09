pipeline {
    
    agent any

    stages {
        stage('Start grid') {
            steps {
                sh "docker-compose -f grid.yaml up -d"
            }
        }

        stage('Run test') {
            steps {
                sh "docker-compose -f test-suites.yaml up"
            }
        }

        stage('Bring Grid Down') {
            steps {
                sh "docker-compose down"
            }
        }
    }

    post {
        always {
            sh "docker-compose -f grid.yaml down"
            sh "docker-compose -f test-suites.yaml down"
        }
    }
}