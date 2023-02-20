//All for God
pipeline{
    agent any
        tools{
            mvn 'mvn'
        }
        stages{
            stage(clone-the-code){
                steps{
                    git 'https://github.com/Acecmd/maven-web-application.git'
                }
            }
            stage(build-the-code){
                steps{
                   sh 'mvn clean package'
                }
            }
            stage(analyze-the-code){
                steps{
                   sh 'mvn sonar:sonar'
                }
            }
            stage(deploy-to-nexus){
                steps{
                    sh 'mvn deploy'
                }
            }
            stage(deploy-the-application){
                steps{
                    deploy adapters: [tomcat8(credentialsId: 'tomcat-cred', path: '', url: 'http://34.239.249.107:8080/')], contextPath: null, war: 'target/*war'
                }
            }
       }
}
