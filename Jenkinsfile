//All for God, whose name is 'YAWEH'
//AMENNNNN!!!!

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
                    deploy adapters: [tomcat8(credentialsId: 'tomcat-cred', path: '', url: 'http://34.239.249.107:8080/')], contextPath: null, war: 'target/*war'
                }
            }
       }
}
