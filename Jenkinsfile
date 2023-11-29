pipeline {
    agent any
    
    stages {
        stage ('SCM') {
            steps {
                git 'https://github.com/C1-80371/exec3.git'
            }
        }
        
        stage ('Docker login') {
            steps {
                sh 'echo dckr_pat_k7omGrJpkqaBaI_7Q5v4hwSF1zI | /usr/bin/docker login -u kuldeeproy --password-stdin'
            }
        }
        
        stage ('Docker build image') {
            steps {
                sh '/usr/bin/docker build -t kuldeeproy/ex3httpd .'
            }
        }
        
        stage ('Docker image push') {
            steps {
                sh '/usr/bin/docker image push kuldeeproy/ex3httpd'
            }
        }
        
        stage ('Create service') {
            steps {
                sh 'kubectl apply -f rs_svc.yaml'
            }
        }
    }
}
