pipeline {
    agent any
    stages {
        stage('Validar Python') {
            steps { bat 'python --version' }
        }
        stage('Instalar dependencias') {
            steps {
                bat 'pip install pandas'
                bat 'pip install psycopg2-binary'
            }
        }
        stage('Ejecutar procesamiento') {
            steps { bat 'python scripts/procesamiento.py' }
        }
        stage('Validacion final') {
            steps { echo 'Pipeline ejecutado correctamente' }
        }
    }
    post {
        success {
            mail to: 'tbrossard57@gmail.com',
                 subject: "Pipeline OK - pipeline-dataops build ${env.BUILD_NUMBER}",
                 body: "El pipeline se ejecuto correctamente. Build numero ${env.BUILD_NUMBER}."
        }
        failure {
            mail to: 'tbrossard57@gmail.com',
                 subject: "Pipeline FALLO - pipeline-dataops build ${env.BUILD_NUMBER}",
                 body: "El pipeline fallo. Revisar la consola. Build numero ${env.BUILD_NUMBER}."
        }
    }
}
