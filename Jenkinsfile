pipeline {
    agent any
    tools {
        maven 'maven_3.8.5'
        jdk 'jdknew'
    }
    stages {
        stage ('Initialize') {
            steps {
                bat '''
                    echo "PATH = ${PATH}"
                    echo "MAVEN_HOME = ${MAVEN_HOME}"
                '''
           }
       }
    stages {
        stage('Checkout') { 
            steps {
                checkout scm
            }
        }
    }
}
