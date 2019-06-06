node
{
    def mavenhome = tool name : 'maven3.6.1',type :'maven'
    stage('git')
    {
        git credentialsId: 'Git-Jenkins', url: 'https://github.com/git-fundamentals/maven-web-application.git'
    }
    stage('maven')
    {
        sh "${mavenhome}/bin/mvn clean package"
    }
    stage('nexus')
    {
        sh "${mavenhome}/bin/mvn clean deploy"
    }
    stage('tomcat')
    {
        sh "cp ${WORKSPACE}/target/*.war /opt/tomcat/apache-tomcat-9.0.20/webapps"
    }
}
