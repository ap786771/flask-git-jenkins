pipeline {
    agent {
        docker {
            image 'python:3.10'
            args '-u root' // optional, lets you install packages if needed
        }
    }

    stages {
        stage('Clone') {
            steps {
                git branch: 'main', url: 'https://github.com/ap786771/flask-git-jenkins.git'
            }
        }

        stage('Install Dependencies') {
            steps {
                sh 'pip install -r requirements.txt'
            }
        }

        stage('Run Flask App') {
            steps {
                sh 'python app.py &'
            }
        }
    }
}
