pipeline {
    agent any
    tools {
        maven 'Apache Maven 3.8.4'
    }
    stages {
        stage('checkout'){
            steps {
                git 'https://github.com/markyates7748/jenkins_demo.git'
            }
        }
        stage('build'){
            steps {
                sh 'mvn clean package'
            }
        }
        stage('run'){
            steps {
                sh 'java -jar demo-0.0.1-SNAPSHOT.jar'
            }
        }
        stage('archive'){
            steps {
                s3Upload consoleLogLevel: 'INFO', dontSetBuildResultOnFailure: false, dontWaitForConcurrentBuildCompletion: false, entries: [[bucket: 'myates7748-aws-class', excludedFile: '', flatten: false, gzipFiles: false, keepForever: false, managedArtifacts: false, noUploadOnFailure: true, selectedRegion: 'us-west-1', showDirectlyInBrowser: false, sourceFile: 'target/*.jar', storageClass: 'STANDARD', uploadFromSlave: false, useServerSideEncryption: false]], pluginFailureResultConstraint: 'FAILURE', profileName: 'myatesJenkins', userMetadata: []
            }
        }
    }
}
