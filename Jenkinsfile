pipeline {
	agent any
	
	stages {
		stage("copy") {
			steps {
				sh "echo 'code copied'"
				git url: "https://github.com/kothapallisrikanth/amazon-linux.git",branch:"master"
			}
		}
		
		stage("build") {
			steps {
				sh "echo 'code build'"
				sh "docker build . -t srikanth370/amazonimage:latest"
				
			}
		}
		
		stage("test") {
			steps {
				sh "echo 'code test'"
			}
		}
		
		stage("deploy") {
			steps {
				sh "echo 'code deploy'"
				sh 'docker run -itd  srikanth370/amazonimage:latest'
			}
		}
	}
	post{
		always{
			sh 'docker images'
			sh 'docker ps'
		}
	}
	
	
}
