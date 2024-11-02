pipeline {
    agent {
        docker {
            image 'maven:3.9.9-jdk-9.0.4' // Utilise une image Docker avec Maven et Java
            args '-v /var/jenkins_home/.m2:/root/.m2' // Cache le répertoire Maven local
        }
    }

    stages {
        stage('Build') {
            steps {
                sh 'mvn clean install'
            }
        }
        stage('Test') {
            steps {
                sh 'mvn test'
            }
        }
        stage('Package') {
            steps {
                sh 'mvn package'
                archiveArtifacts artifacts: 'target/*.jar', allowEmptyArchive: true
            }
        }
    }
}
