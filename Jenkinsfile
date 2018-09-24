node {
    def mvnHome = tool 'maven'
    tool name: 'maven', type: 'maven'
    echo 'RUN pipeline job'
    stage ('Clone source'){
        def scmVars = checkout scm
        echo "${scmVars}"
        sh "git fetch"
    }
    stage('SonarQube analysis') {
      withSonarQubeEnv('My SonarQube Server') {
//          withEnv( ["PATH+MAVEN=${maven}/bin"] ) {
            sh '${mvnHome}/bin/mvn clean package sonar:sonar'
//          }
      }  // SonarQube taskId is automatically attached to the pipeline context
    }
   
    stage ('build'){
        sh "javac Hello.java"
    }
}
