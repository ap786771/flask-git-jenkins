def COLOR_MAP = [
    "FAILURE" : 'danger',
    "SUCCESS" : 'good'
]

pipeline {
    agent any

    stages {
        stage('Clone') {
            steps {
                git branch: 'main', url: 'https://github.com/ap786771/flask-git-jenkins.git'
            }
        }

        stage('Install Dependencies') {
            steps {
                sh 'python3 -m pip install -r requirements.txt'
            }
        }

        stage('Run Flask App') {
            steps {
                sh 'nohup python3 app.py &'
            }
        }
    }

    post {
        always {
            echo "Slack Notifications"
            slackSend(
                channel: "#jenkins",
                color: COLOR_MAP[currentBuild.currentResult] ?: 'warning',
                message: "*${currentBuild.currentResult}:* Job `${env.JOB_NAME}`\nBuild #${env.BUILD_NUMBER}\n<${env.BUILD_URL}|View Details>"
            )
        }
    }
}
