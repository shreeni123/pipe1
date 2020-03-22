node {
    stage('Checkout'){
        git branch: 'master', url: 'https://github.com/atinsingh/pipe1.git'
    }

    stage('Compile') {
        withMaven(jdk: 'jdk8', maven: 'm3') {
           sh "mvn compile"
        }
    }

     stage('Unit Testing') {
        withMaven(jdk: 'jdk8', maven: 'm3') {
           sh "mvn test"
        }
    }

    stage('Publish Result '){
        junit '  target/surefire-reports/*.xml'
    }

    stage('Package Artifact') {
            withMaven(jdk: 'jdk8', maven: 'm3') {
               sh "mvn package"
            }
    }
    stage ("Print Hello"){
        sh 'echo Hello to Jenkins'
    }
}