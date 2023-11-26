pipeline {
    agent any

    stages {
        stage ('SCM') {
            steps {
                git branch: 'master', url: 'https://c2-80295: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@github.com/C2-80295/Sample.git'
            }
        }

        
        stage ('docker login') {
            steps {
                sh 'echo dckr_pat_FxQD9x_Fec84SBAiHZuCeAkz8Rs | /usr/bin/docker login -u jakejake23 --password-stdin'
            }
        }
        stage ('docker build image') {
            steps {
                sh '/usr/bin/docker build -t jakejake23/sample .'
            }
        }
        stage ('docker push image') {
            steps {
                sh '/usr/bin/docker push jakejake23/sample'
            }
        }
        stage ('reload docker service') {
            steps {
                sh '/usr/bin/docker service update --image jakejake23/sample --force myservice'
            }
        }
    }
}