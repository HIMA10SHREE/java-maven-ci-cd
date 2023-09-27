pipeline {
    agent any

    stages {
        stage('git checkout') {
            steps {
               checkout scmGit(branches: [[name: '*/main']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/HIMA10SHREE/java-maven-ci-cd.git']])
                  }
        }
        

         stage('maven build'){
             steps{
                sh 'mvn -B -DskipTests clean package'
                }
         }
         
          stage('generate artifacts'){
             steps{
                archiveArtifacts artifacts: 'target/*.war', followSymlinks: false
                }
         }
         stage('deploy to tomcat'){
             steps{
               deploy adapters: [tomcat9(credentialsId: 'tomcat-server', path: '', url: 'http://44.203.37.114:8080/')], contextPath: 'HIMA-TEST', onFailure: false, war: 'target/*.war'
             }
         }
           
        
    }
}