#!groovy​

properties([[$class: 'BuildDiscarderProperty', strategy: [$class: 'LogRotator', numToKeepStr: '10']]])

stage('build') {
    node {
        checkout scm
        def v = version()
        currentBuild.displayName = "${env.BRANCH_NAME}-${v}-${env.BUILD_NUMBER}"
        mvn "clean verify"
    }
}

def mvn(String goals) {
    def mvnHome = tool "Maven-3.6.0"
    def javaHome = tool "JDK11.0.1"

    withEnv(["JAVA_HOME=${javaHome}", "PATH+MAVEN=${mvnHome}/bin"]) {
        sh "mvn -B ${goals}"
    }
}

def version() {
    def matcher = readFile('pom.xml') =~ '<version>(.+)</version>'
    return matcher ? matcher[0][1] : null
}
