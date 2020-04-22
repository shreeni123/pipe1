pipeline {
  agent {
    docker {
      image 'maven:3-alpine' 
      args '-v /root/.m2:/root/.m2' 
      }
  }
  options {
    skipStagesAfterUnstable()
    }
  
  stages {
    
    stage('Checkout') {
        steps {
            git 'https://github.com/shreeni123/pipe1.git'
        }
    }
    
    stage('Compile') { 
      steps {
        sh 'mvn -B -DskipTests compile' 
      }
    }
    
    stage('Unit Testing') { 
      steps {
        sh 'mvn test' 
      }
    }
    
    stage('Publish result') { 
      steps {
        junit 'target/surefire-reports/*.xml'
      }
    }
    
    stage('Package Artifact') { 
      steps {
        sh 'mvn package' 
      }
    }
    
    stage('Print Hello') {
        steps {
            sh 'echo Hello to Jenkins'
        }
    }
  }
}