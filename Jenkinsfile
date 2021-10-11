pipeline {
    agent none
  	stages {
    	stage('SCM Checkout'){
		steps{
        	git branch: 'main', credentialsId: 'Git', url: 'https://github.com/naveen4152/DemoApp1.git'
   	 	}
		}
    	stage('Docker Build'){
		steps{
        	sh 'docker build -t naveen4152/scripted_demo:1.1 .'
    			}
		}
    	stage('Docker Push'){
		steps{
        	withCredentials([string(credentialsId: 'Docker_pwd', variable: 'Docker_pwd')]) {
        	sh "docker login -u naveen4152 -p ${Docker_pwd}"
        	}
        	sh 'docker push naveen4152/scripted_demo:1.1'
    			}
		}
    	stage('Run Dockerimage'){
		steps{
        	sh 'docker run -d -p 80:80 --name myapp22 naveen4152/scrited_demo:1.1'
    			}
		}
	}
}
