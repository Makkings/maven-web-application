// This is my first jenkins file.
// I will write so many in this life in the name of Jesus, Amen.
// God has made me the head.
//Note to self:
// I AM THE SME - subject matter expert...
// My job is done here

pipeline{
    agent any
    tools{
        maven 'mvn'
    }
    stages{
        stage('clone'){
            steps{
                git 'https://github.com/Acecmd/maven-web-application.git'
            }
        }
        stage('test and build'){
            steps{
                sh 'mvn clean package'
            }
        }
        stage('code quality analysis'){
            steps{
                sh 'mvn sonar:sonar'
            }
        }
        stage('upload to nexus'){
            steps{
                sh 'mvn deploy'
            }
        }
        stage('deploy to tomcat'){
            steps{
            deploy adapters: [tomcat8(credentialsId: 'tomcat-cred', path: '', url: 'http://54.227.127.193:8080/')], contextPath: null, war: 'target/*war'
            }
        }
        
    }
}
