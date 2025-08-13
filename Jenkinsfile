pipeline {
    agent any 
    
    tools{
        jdk 'jdk17'
        maven 'maven3'
    }
    
    stages{
        
        stage("Git Checkout"){
            steps{
                git branch: 'test', changelog: false, poll: false, url: 'https://github.com/kajlekarn/Petclinic.git'
            }
        }
        
        stage("Compile"){
            steps{
                sh "mvn clean compile"
            }
        }
        
         stage("Test Cases"){
            steps{
                sh "mvn test"
            }
        }
        
         stage("Build"){
            steps{
                sh " mvn clean install"
            }
        }
        
        stage("Deploy To Tomcat"){
            steps{
                sh "cp target/*.war /opt/apache-tomcat-9.0.65/webapps/ "
            }
        }
    }
}
