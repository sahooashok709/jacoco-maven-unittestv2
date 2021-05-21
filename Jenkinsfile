pipeline{
    agent any
    stages {
        stage("checkout") {
            steps {
                git branch: 'master', url: 'https://github.com/sahooashok709/jacoco-maven-unittestv2.git'
            }
        }
        stage('PreCheck') {
            steps {
                script {
                    env.BUILDME = "yes"
                }
            }
        }
        stage("unit_test") {
            steps {
                bat "mvn test"
            }
        }
        stage("build") {
            steps {
                bat "mvn clean package"
            }
        }
        stage('SonarAnalysis') {
            steps {
                 bat 'mvn sonar:sonar'
            }
        }
    }    
}