pipeline {
    agent any

    stages {

        stage('Construir y Testear') {
            steps {
                sh 'mvn clean package'  
            }
        }

        stage('Desplegar a la Base de Datos') {
            steps {
                script {
                    def dbHost = 'tu_host_de_bd'
                    def dbUser = 'tu_usuario'
                    def dbPassword = 'tu_contraseña'
                    def dbName = 'tu_base_de_datos'

                    // Ejecutar un script para insertar registros en la base de datos
                    sh "mysql -h ${dbHost} -u ${dbUser} -p${dbPassword} ${dbName} < scripts/insert_registros.sql"
                }
            }
        }
    }
}
