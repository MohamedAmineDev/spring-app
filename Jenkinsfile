pipeline{
    agent any
    tools{
        maven 'maven'
    }
    stages{
        stage ("Clean up"){
            steps{
                deleteDir()
            }
        }
        stage ("Clone repo"){
            steps{
                 sh "git clone https://github.com/MohamedAmineDev/spring-app.git"
            }
        }
        stage ("Generate backend image"){
            steps{
                dir('spring-app'){
                    sh "mvn clean install "
                    sh " sudo -S docker build  -t spring-app  ."
                }
            }
        }
        stage ("Run docker compose"){
            steps{
                dir("spring-app"){
                    sh " sudo -S docker  compose up"
                }
            }
        }
    }
}