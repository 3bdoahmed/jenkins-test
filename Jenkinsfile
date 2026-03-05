pipeline{
    agent {
        label "agent-01"
    }
    tools {
        maven "mvn-3-5-4"
        idk "JDK-11"
    }
    stages{
        stage("build app"){
            steps{
                sh "maven package installed"
            }
        }
        stage("test app"){
            steps{
                sh "mvn had tested"
            }
        }
        stage("build docker file"){
            steps{
                sh "docker build -t java-app:v1 ."
            }
        }


    }



}