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
            deploy adapters: [tomcat8(credentialsId: 'tomcat-cred', path: '', url: 'http://100.26.233.77:8080/')], contextPath: null, war: 'target/*war'
            }
        }
        
    }
}
