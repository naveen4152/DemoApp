pipeline {
    agent any
    stages {
        stage('SCM Checkout'){
	        	steps{
                	git branch: 'dev', credentialsId: 'Git', url: 'https://github.com/naveen4152/DemoApp1.git'
   	 	               }
	        	}
	        	
    	stage('Docker Build'){
		        steps{
        	        sh 'docker build -t naveen4152/declarative_demo:1.1 .'
    			    }
		        }
    	
	}
}
