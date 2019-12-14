pipeline {
    agent any
    stages {
        stage('scm checkout'){
          git 'https://github.com/sandesh421/maven-project'
        }
  }
    {
        stage ('Compile Stage') {
            steps {
                withMaven(maven : 'localmaven') {
                    sh 'mvn clean compile'
                }
            }
        }
        stage ('Testing Stage') {
            steps {
                withMaven(maven : 'localmaven') {
                    sh 'mvn test'
                }
            }
        }
        stage ('install Stage') {
            steps {
                withMaven(maven : 'localmaven') {
                    sh 'mvn install'
                }
            }
        }
        stage ('deploy to dev') {
             steps {
                  sshagent(['tomcat']) {
                  sh 'scp -o StrictHostKeyCking=no */target/*.war ec2-user@172.31.12.220:/var/lib/tomcat/webapps'
} } }       
}
}
