pipeline {
    agent any


    stages {
        stage('SCM Checkout'){
          git  'https://github.com/prakashk0301/maven-project'
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
                  sshagent(['d5763664-1a68-492e-a9c3-0f111fe3895f']) {
                  sh 'scp -o StrictHostKeyChecking=no */target/*.war ec2-user@172.31.24.198:/var/lib/tomcat/webapps'
} } }

         
}
}
