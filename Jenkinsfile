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

        stage('Build back') {
            steps {
                sh 'ls -ltr'
                sh 'mvn clean package'
            }
        }

    

   stage('Unit Tests') {
            steps {
                    // Assurez-vous que vous êtes dans le répertoire du projet Maven
                    // Exécutez les tests unitaires avec Maven
                    sh 'mvn test'
                }
           }

       stage('Mockito Tests') {
            steps {
                    // Assurez-vous que vous êtes dans le répertoire du projet Maven
                    // Exécutez les tests Mockito avec Maven (assurez-vous d'avoir configuré les tests Mockito correctement)
                    sh 'mvn clean test -Pmockito-tests'
                }
       }

        stage('Generate JaCoCo Coverage Reports') {
    steps {
        sh 'mvn jacoco:report'
    }
}

 stage ('NEXUS DEPLOY') {

       steps {
       sh 'mvn deploy -DskipTests'
             }
            }
        stage('SonarQube') {
            steps {
                script {
                    try {
                        sh 'mvn sonar:sonar'
                    } catch (Exception e) {
                        currentBuild.result = 'FAILURE'
                        error "Error running SonarQube analysis: ${e.message}"
                    }
                }
            }
        }
      
    }
}
