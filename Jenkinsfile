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
        stage('upload to nexus')
            steps {
                nexusArtifactUploader credentialsId: 'f34ad025-9e4d-488c-b741-b49e41cc950c', groupId: 'helloworld_sravan', nexusUrl: '192.168.0.103:8081', nexusVersion: 'nexus3', protocol: 'http', repository: '192.168.0.103:8081/repository/helloworld', version: '0.0.1'
            }
        }
    }
}
