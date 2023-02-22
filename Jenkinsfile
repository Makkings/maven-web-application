pipeline{
    agent any
        tools{
            maven 'mvn'
        }
        stages{
            stage(clone){
                steps{
                    git 'https://github.com/Acecmd/maven-web-application.git'
                }
            }
            stage(build){
                steps{
                   sh 'mvn clean package'
                }
            }
            stage(analyze){
                steps{
                   sh 'mvn sonar:sonar'
                }
            }
            stage(backup){
                steps{
                    sh 'mvn deploy'
                }
            }
            stage(deploy){
                steps{
                    deploy adapters: [tomcat8(credentialsId: 'tomcred', path: '', url: 'http://54.80.146.202:8080/')], contextPath: null, war: 'target/*war'
                }
            }
       }
}
