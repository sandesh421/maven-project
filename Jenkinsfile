pipeline {
    agent any
    stages {
        stage('scm Checkout'){
          git  'https://github.com/sandesh421/maven-project'
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
                  sshagent(['d09638bd-2199-4dd9-a51e-3bfc4a5a47df']) {
                  sh 'scp -o StrictHostKeyChecking=no */target/*.war ec2-user@172.31.12.220:/var/lib/tomcat/webapps'
} } }       
}
}
