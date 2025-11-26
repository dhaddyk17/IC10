pipeline {
    agent any

    stages {

        stage('Checkout') {
            steps {
                git url: 'https://github.com/dhaddyk17/IC10',
                    branch: 'master',
                    credentialsId: 'github-token'
            }
        }

        stage('Install Dependencies') {
            steps {
                sh '''
                    sudo apt update
                    sudo apt install -y python3-flask python3-flask-cors
                '''
            }
        }

        stage('Run Flask App') {
            steps {
                sh '''
                    cd $WORKSPACE
                    sudo pkill -f app.py || echo "No running Flask app"
                    sudo nohup python3 app.py > flask.log 2>&1 &
                '''
            }
        }
    }
}
