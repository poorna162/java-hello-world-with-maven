pipeline{
    agent any
    environment {
        PATH = "/opt/apache-maven-3.6.3/bin:$PATH"
    }
    stages{
        stage('git clone'){
            steps{
                checkout([$class: 'GitSCM', branches: [[name: '*/master']], extensions: [], userRemoteConfigs: [[credentialsId: 'github siva', url: 'https://github.com/sivanjaneyareddy/java-hello-world-with-maven.git']]])
            }
        }
        stage('build'){
            steps{
               sh 'mvn clean install'
            }
        }
    stage('Snyk Test') {
            steps {
                echo 'Snyk Testing...'
                snykSecurity (
                    projectName: 'poorna162', 
                    snykInstallation: 'snyk@latest', 
                    snykTokenId: 'snykapi',
                    failOnIssues: false
                )
            }
        } 
    }
}  
