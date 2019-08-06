pipeline {
    agent any   	  
    	stages {
        	stage("clone code") {
            	steps {
                script {
                    // Let's clone the source
                    git 'https://github.com/rashmi7321/buildtest.git';
                }
            }
        }
            stage('SonarQube analysis') {
               withSonarQubeEnv(credentialsId: 'f225455e-ea59-40fa-8af7-08176e86507a', installationName: 'My SonarQube Server') { // You can override the credential to be used
      sh 'mvn org.sonarsource.scanner.maven:sonar-maven-plugin:3.6.0.1398:sonar'
    }
  }
} 
                
            
            
        	stage("mvn build") {
            	steps {
                script {
                    // If you are using Windows then you should use "bat" step
                    // Since unit testing is out of the scope we skip them
                    sh "mvn clean install"
                }
            }
        }
        
    }
}
