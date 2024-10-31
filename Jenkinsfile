pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                script {
                    sh 'mvn clean package' // Construire l'application
                }
            }
        }
        stage('Test') {
            steps {
                script {
                    sh 'mvn test' // Exécuter les tests
                }
            }
        }
        stage('Deploy') {
            steps {
                script {
                    sh 'java -jar target/demo-0.0.1-SNAPSHOT.jar' // Déployer l'application
                }
            }
        }
    }
    post {
        success {
            echo 'Pipeline exécuté avec succès!'
        }
        failure {
            echo 'Échec du pipeline!'
        }
    }
}
