#!groovy
// Check Webdeco properties
properties([disableConcurrentBuilds()])

pipeline {
    agent { 
        label 'master'
        }
    options {
        buildDiscarder(logRotator(numToKeepStr: '10', artifactNumToKeepStr: '10'))
        timestamps()
    }
    stages {
        stage("Create Docker images") {
            steps {
			sh 'ssh rymar64@40.124.44.223 \'sudo rm -rf html5 && sudo git clone https://github.com/rymar24/html5.git\' '
            }
        }
		stage("Build Docker images") {
            steps {
			sh 'ssh rymar64@40.124.44.223 \'cd html5 && sudo docker build -t deco5 . \''
            }
        }
		stage("RUN Docker images") {
            steps {
			sh 'ssh rymar64@40.124.44.223 \'sudo docker run -d -p 90:80 deco5\''
            }
        }		
    }	
}
