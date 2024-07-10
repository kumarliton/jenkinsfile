pipeline {
    agent any
    tools {
  maven 'maven'
}

    stages {
        stage('Hello') {
            steps {
                echo 'Hello World'
            }
        } 
        stage ('git') {
            steps {
                
            git 'https://github.com/anitha8242/hello-world.git'
            }
        }
        stage('build') {
            steps {
                sh 'mvn package'
            }
        }
        stage ('deploy') {
            steps {
               deploy adapters: [tomcat9(credentialsId: '908', path: '', url: 'http://52.91.118.39:8080/')], contextPath: null, war: '**/*.war'
            }
        }
        stage ('test') {
          steps {
              withCredentials([string(credentialsId: '678', variable: 'sonarqube')]) {
                  sh 'mvn sonar:sonar'
                }
            }
        }
    }
}
