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
        stage ('reload docker service') {
            steps {
                sh '/usr/bin/docker service update --image jakejake23/q2 --force myservice'
            }
        }
    }
}