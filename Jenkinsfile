pipeline {
    agent any

    stages {
        stage('Clone') {
            steps {
                git 'https://github.com/ap786771/flask-git-jenkins.git'
            }
        }

        stage('Install Dependencies') {
            steps {
                sh 'pip install -r requirements.txt'
            }
        }

        stage('Run Flask App') {
            steps {
                sh 'nohup python app.py &'
            }
        }
    }
}

