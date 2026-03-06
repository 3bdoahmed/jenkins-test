pipeline{
    agent {
        label "agent-01"
    }
    tools {
        maven "mvn-3-5-4"
        jdk "JDK-11"
    }
    environment {
        DOCKER_USERNAME = credentials("docker_username")
        DOCKER_PASSWORD = credentials("docker_password")
        DEPI_ROUND = "R4"
    }
    stages{
        stage("build app"){
            steps{
                sh "echo ${DEPI_ROUND}"
                sh "mvn package install -Dskiptests"
            }
        }
        stage("test app"){
            steps{
                sh "mvn test"
            }
        }
        stage("build docker file"){
            steps{
                sh "docker build -t abdelrahman678/java-app:v${BUILD_NUMBER} ."
            }
        }
        //stage("push image to dockerhub"){
        //    steps{withCredentials([string(credentialsId: 'docker_username', variable: 'DOCKER_USERNAME'), string(credentialsId: 'docker_password', variable: 'DOCKER_PASSWORD')]) {
        //    sh "docker login -u ${DOCKER_USERNAME} -p ${DOCKER_PASSWORD}"
        //     }
        //     sh "docker push java-app:${BUILD_NUMBER}"
        //    }
        //}
        stage("push image to dockerhub"){
            steps{
                sh "docker login -u ${DOCKER_USERNAME} -p ${DOCKER_PASSWORD}"
                sh "docker push abdelrahman678/java-app:v${BUILD_NUMBER}"
            }
        }



    }



}