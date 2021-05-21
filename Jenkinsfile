pipeline{
    agent any
    parameters {
        booleanParam defaultValue: true, description: 'value_for_this', name: 'CodeAnalysis'
    }
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
            when {environment name: 'BUILDME', value: 'yes'}
            steps {
                withSonarQubeENV('sonarqube_mine') {
                    bat 'mvn sonar:sonar'
                }
            }
        }
    }    
}