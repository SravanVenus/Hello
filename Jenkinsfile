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
        stage('Upload_to_Nexus')
            steps {
                nexusArtifactUploader artifacts: [[artifactId: 'helloworld', classifier: '', file: 'C:\\ProgramData\\Jenkins\\.jenkins\\workspace\\hello\\target\\helloworld-0.0.1-SNAPSHOT.jar', type: 'jar']], credentialsId: 'f34ad025-9e4d-488c-b741-b49e41cc950c', groupId: 'helloworld_sravan', nexusUrl: 'localhost:8081', nexusVersion: 'nexus3', protocol: 'http', repository: 'http://localhost:8081/repository/helloworld/', version: '0.0.1'
            }
        } 
    }
}
