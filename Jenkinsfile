pipeline {
    agent any

    tools {
        maven "M3"
    }
    stages {
        stage ('Build') {
            steps {
                // Get code from Git
                git branch: 'main', url: 'https://github.com/spring-projects/spring-petclinic.git'

                // Run maven
                sh "mvn clean package"
            }
            post {
                success {
                    junit '**/target/surefire-reports/TEST-*.xml'
                    archiveArtifacts 'target/*.jar'
                }
            }

        }
    }
}
