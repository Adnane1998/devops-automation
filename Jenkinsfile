pipeline {
    
    agent any
    tools{
       maven 'maven_3_9_2' 
    }
    stages{
        stage('Build Maven')
        {
        steps{
            checkout scmGit(branches: [[name: '*/main']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/Adnane1998/devops-automation']])
            bat 'mvn clean install'
        }
        }
    
    stage('Build docker image')
    {
        steps{
            script{
                bat 'docker build -t adnane1998/devops-integration .'
            }
        }
    }
    stage('Push image to Hub')
    {
        steps{
            script{
           withCredentials([string(credentialsId: 'dockerhub-pwd', variable: 'dockerhubpwd')]) {
            bat 'docker login -u adnane1998 -p Alahouakbar1998!!'
}
            bat 'docker push adnane1998/devops-integration'
            }
        }
        
    }
    }
}