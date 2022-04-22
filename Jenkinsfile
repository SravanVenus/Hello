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
        stage('checkout') {
            steps {
                checkout scm
            }
        }
        stage('build') {
            steps {
                bat 'mvn  -B -DskipTests clean package'
            }
        }
        stage('upload to nexus'){
            steps{
                nexusArtifactUploader artifacts: [
                    [
                    artifactId: 'helloworld', 
                    classifier: '', 
                    file: 'target/helloworld-0.0.1.jar', 
                    type: 'jar'
                      ]
                    ], 
                    credentialsId: 'nexus3', 
                    groupId: 'helloworld_sravan', 
                    nexusUrl: 'localhost:8081', 
                    nexusVersion: 'nexus3', 
                    protocol: 'http', 
                    repository: 'Test', 
                    version: '0.0.1'
            }
        }
    }
}
