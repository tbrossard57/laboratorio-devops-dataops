node {

    stage('Checkout') {
        checkout scm
    }

    stage('Validar Python') {
        bat 'python --version'
    }

    stage('Instalar dependencias') {
        bat 'pip install pandas'
        bat 'pip install psycopg2-binary'
    }

    stage('Ejecutar procesamiento') {
        bat 'python scripts/procesamiento.py'
    }

    stage('Validacion final') {
        echo 'Pipeline ejecutado correctamente'
    }
}
