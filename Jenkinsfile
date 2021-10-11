pipeline{
agent any
  stages {
    stage('SCM Checkout'){
        git branch: 'main', credentialsId: 'Git', url: 'https://github.com/naveen4152/DemoApp1.git'
    }
    stage('Docker Build'){
        sh 'docker build -t naveen4152/scripted_demo:1.1 .'
    }
    stage('Docker Push'){
        withCredentials([string(credentialsId: 'Docker_pwd', variable: 'Docker_pwd')]) {
        sh "docker login -u naveen4152 -p ${Docker_pwd}"
        }
        sh 'docker push naveen4152/scripted_demo:1.1'
    }
    stage('Run Dockerimage'){
        sh 'docker run -d -p 80:80 --name myapp22 naveen4152/scrited_demo:1.1'
    }
}
}