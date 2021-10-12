pipeline {
    agent any
    stages {
        stage('SCM Checkout'){
	        	steps{
                	git branch: 'prod', credentialsId: 'Git', url: 'https://github.com/naveen4152/DemoApp1.git'
   	 	               }
	        	}
	        	
    	stage('Docker Build'){
		        steps{
        	        sh 'docker build -t naveen4152/multibranch_demo:1.1 .'
    			    }
		        }
	stage('Docker Push'){
		steps{
        	withCredentials([string(credentialsId: 'Docker_pwd', variable: 'docker_wd')]) {
        	sh "docker login -u naveen4152 -p ${docker_wd}"
        	}
        	sh 'docker push naveen4152/multibranch_demo:1.1'
    			}
		}
		stage('Run Dockerimage'){
		steps{
        	sh 'docker run -d -p 80:80 --name myapp33 naveen4152/multibranch_demo:1.1'
    			}
		}
    	
	}
}
