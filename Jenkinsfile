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
				sh 'aws ecr get-login-password --region ap-south-1 | docker login --username AWS --password-stdin 720621264458.dkr.ecr.ap-south-1.amazonaws.com'
				sh 'docker build . -t srikanth-image:latest'
				sh 'docker tag srikanth-image:latest 720621264458.dkr.ecr.ap-south-1.amazonaws.com/srikanth-repo:latest'
				sh 'docker push 720621264458.dkr.ecr.ap-south-1.amazonaws.com/srikanth-repo:latest'
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
				sh 'docker kill $(docker ps -q)'
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
