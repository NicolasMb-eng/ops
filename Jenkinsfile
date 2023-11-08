pipeline {
    agent any
    environment {
        version = '1.0'
    }
    stages {
        stage('Git Checkout') {
            steps {
                script {
                    git branch: 'master', url: 'https://github.com/NicolasMb-eng/ops.git'
                }
            }
        }

        stage('Build') {
            steps {
                sh 'ls -ltr'
                sh 'mvn clean package'
            }
        }

        stage('SonarQube') {
            steps {
             
            }
        }

                stage('Mockito Tests') {
            steps {
                   
                }
        }

   stage('Unit Tests') {
            steps {
                    // Assurez-vous que vous êtes dans le répertoire du projet Maven
                    // Exécutez les tests unitaires avec Maven
                    sh 'mvn test'
                }
           }


        stage ('NEXUS DEPLOY') {

       steps {
       
            }
        stage('Build docker image'){
            steps{
                
            }
        }
        stage('Push image to Hub'){
            steps{
               
            }
        }
    }
}