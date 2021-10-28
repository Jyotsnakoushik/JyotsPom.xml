@Library('app-libs') _
pipeline{
    agent any
    stages{
        stage("SCM Checkout"){
            steps {
                git branch: 'dev', url: 'https://github.com/Jyotsnakoushik/JyotsPom.xml'
            }
        }
        stage ("Maven build"){
            steps{
                sh 'mvn clean package'
                sh 'mv target/myweb*.war target/myweb.war'
            }
        }
        stage ("Deploy to tomcat development"){
            steps{
                tomcatdeploy("172.31.33.3","Tomcat","myweb")      
           }
        }
        
    }
    post {
  always {
    cleanWs()
  }
}
}
