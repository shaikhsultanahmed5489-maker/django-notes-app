@Library("Shared") _

pipeline {

    agent { label "tiger" }

    stages {

        stage("Hello") {
            steps {
                script {
                    hello()
                }
            }
        }

        stage("Code") {
            steps {
                script {
                    clone("https://github.com/shaikhsultanahmed5489-maker/django-notes-app.git", "main")
                }
            }
        }

        stage("Build") {
            steps {
                script {
                    docker_build("notes-app", "latest", "sultanahmeddev")
                }
            }
        }

        stage("Push to DockerHub") {
            steps {
                script {
                    docker_push("notes-app", "latest", "sultanahmeddev")
                }
            }
        }

        stage("Deploy") {
            steps {
                echo "This is deploying the code"
                sh "docker compose down && docker compose up -d"
            }
        }

    }
}
