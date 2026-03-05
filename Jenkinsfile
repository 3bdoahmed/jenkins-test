pipeline{
    agent {
        label "agent-01"
    }
    tools {
        maven "mvn-3-5-4"
        jdk "JDK-11"
    }
    stages{
        stage("build app"){
            steps{
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
                sh "docker build -t java-app:v1 ."
            }
        }


    }



}