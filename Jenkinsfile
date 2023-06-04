pipeline {
    agent any

    environment {
       myjava = "/usr/lib/jvm/java-1.8.0-openjdk-amd64"
    }
    
    stages {
        stage('VCS Chekout') {
            steps {
                checkout changelog: false, poll: false, scm: scmGit(branches: [[name: '*/master']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/adevopstech/maven-java-sample.git']])
            }
        }
        
        stage('Compile Code') {
            steps {
                    sh 'mvn compile'
            }
        }
        
        stage('Test Code') {
            steps {
                    sh 'mvn test'
            }
        }
        
        stage('Deploy Code') {
            steps {
                    sh 'mvn clean verify package'
            }
        }
    }
}
