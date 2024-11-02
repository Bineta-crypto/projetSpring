pipeline {
    agent {
        docker {
            image 'maven:3.8.5-jdk-11' // Utilise une image Docker avec Maven et Java
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
