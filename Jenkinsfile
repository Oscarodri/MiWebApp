pipeline{
    agent any
    stages{
        stage('Repositorio'){
            steps{
                echo 'Clonamos el repositorio'
                git url:'https://github.com/Oscarodri/MiWebApp'
            }
        }
        stage('Empaquetado'){
            steps{
                echo 'Empaqueto mediante maven'
                sh 'mvn package'
            }
        }
        stage('Enviar a Tomcat'){
            steps{
                echo 'Envio a Tomcat'
                deploy adapters: [tomcat9(credentialsId: '599f6d50-0d61-471f-85ad-2faff671f505', path: '', url: 'http://localhost:8082')], contextPath: 'prueba1', war: 'target/miweb.war'
            }
        }
    }
    post{
        always{
            echo 'Yo me ejecuto siempre'
        }
        success{
            echo 'Yo me ejecuto si todo ha ido bien'
        }
        failure{
            echo 'Yo me ejecuto si todo ha ido mal'
        }
        changed{
            echo 'Yo me ejecuto si esta ejecucion no acaba en el mismo estado que la anterior'
        }
    }
}