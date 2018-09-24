node {
    echo 'RUN pipeline job'
    stage ('Clone source'){
        def scmVars = checkout scm
        echo "${scmVars}"
        sh "git fetch"
    }
    stage ('build'){
        sh "javac Hello.java"
        }
}