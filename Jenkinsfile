pipeline {
    agent any

    stages {
        stage ('SCM') {
            steps {
                git branch: 'master', url: 'https://c2-80295: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@github.com/C2-80295/question2.git'
            }
        }
        stage ('docker login') {
            steps {
                sh 'echo dckr_pat_FxQD9x_Fec84SBAiHZuCeAkz8Rs | /usr/bin/docker login -u jakejake23 --password-stdin'
            }
        }
        stage ('docker build image') {
            steps {
                sh '/usr/bin/docker build -t jakejake23/q2 .'
            }
        }
        stage ('docker push image') {
            steps {
                sh '/usr/bin/docker push jakejake23/q2'
            }
        }
        #start minikube
        stage ('start minikube') {
            steps {
                sh 'minikube start'
            }
        }
        stage ('kubernetes replica set t0 create 5 pods') {
            steps {
                sh 'kubectl create -f rs1.yaml'
            }
        }
        
        
    }
}