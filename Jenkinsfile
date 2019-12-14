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
                  sshagent(['9a2b1964-97c6-4c30-8241-af818fa62c0a']) {
                  sh 'scp -o StrictHostKeyCking=no */target/*.war ec2-user@3.136.19.4:/var/lib/tomcat/webapps'
} } }       
}
}
