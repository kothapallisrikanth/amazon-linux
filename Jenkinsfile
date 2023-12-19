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
			}
		}
	}
}
