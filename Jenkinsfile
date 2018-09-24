node {
    echo 'RUN pipeline job'
    stage ('Clone source'){
        def scmVars = checkout scm
        echo "${scmVars}"
        sh "git fetch"
    }
    stage('SonarQube analysis') {
      withSonarQubeEnv('My SonarQube Server') {
        sh 'mvn clean package sonar:sonar'
      }  // SonarQube taskId is automatically attached to the pipeline context
    }
   
    stage ('build'){
        sh "javac Hello.java"
    }
}
