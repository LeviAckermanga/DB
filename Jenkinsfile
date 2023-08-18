pipeline {
    agent any
    
    stages {

        stage('Construir y Testear') {
            steps {
                sh 'mvn clean package'  
            }
        }
        stage('Instalar dependencias') {
            steps {
                  script {
                      sh 'apt-get update'
                      sh 'apt-get install -y mysql-client'
                  }
            }
        }

        stage('Desplegar a la Base de Datos') {
            steps {
                script {
                    def dbHost = '172.17.0.3:3307'
                    def dbUser = 'root'
                    def dbPassword = 'diego3010'
                    def dbName = 'mysqlite'

                    // Ejecutar un script para insertar registros en la base de datos
                    sh "mysql -h ${dbHost} -u ${dbUser} -p ${dbPassword} ${dbName} < scripts/insert_registros.sql"
                }
            }
        }
    }
}
