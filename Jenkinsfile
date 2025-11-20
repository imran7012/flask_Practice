pipeline {
    agent any

    parameters {
    string(name: 'EC2_HOST', defaultValue: 'EC2 IP Address', description: 'Target EC2 host')
  }

    environment {
        VENV_DIR = "${WORKSPACE}/venv"
        SSH_KEY_ID = "syed-ID-ssh"
        EC2_USERNAME = "ec2-user"
        EC2_HOST = "${params.EC2_HOST}"
        DEPLOY_DIR = "/home/ec2-user/flask_app"
    }

    stages {

        stage('Checkout') {
            steps {
                echo "Cloning repository..."
                sh '''
                    rm -rf flask_Practice
                    git clone https://github.com/imran7012/flask_Practice.git
                '''
            }
        }

        stage('Build') {
            steps {
                echo "Setting up venv and installing dependencies..."
                sh '''
                    python3 -m venv "$VENV_DIR"
                    . "$VENV_DIR/bin/activate"
                    pip install --upgrade pip
                '''
            }
        }

        stage('Test') {
            steps {
                echo "Running pytest..."
                sh '''
                    . "$VENV_DIR/bin/activate"
                    pip install pytest
                    cd flask_Practice
                    pytest -v || exit 1
                '''
            }
        }

        stage('Deploy') {
            steps {
                sshagent(credentials: [env.SSH_KEY_ID]) {
                    sh """
                        echo "Creating tarball..."
                        rm -f app.tar.gz
                        tar --exclude='flask_Practice/.git' -czf app.tar.gz flask_Practice

                        echo "Copying tarball to EC2..."
                        scp -o StrictHostKeyChecking=no app.tar.gz ${EC2_USERNAME}@${EC2_HOST}:/home/ec2-user/

                        echo "Running remote deploy..."
                        ssh -o StrictHostKeyChecking=no ${EC2_USERNAME}@${EC2_HOST} << 'ENDSSH'
set -e

sudo yum install -y python3 python3-pip

mkdir -p ${DEPLOY_DIR}
rm -rf ${DEPLOY_DIR}/flask_Practice
tar xzf /home/ec2-user/app.tar.gz -C ${DEPLOY_DIR}

cd ${DEPLOY_DIR}/flask_Practice

sudo pip install -r ${DEPLOY_DIR}/flask_Practice/requirements.txt

# sudo pip install pymongo flask-pymongo

# sudo pip install python-dotenv

# Stop old Flask app if running
sudo pkill -f "flask run" || true

nohup flask run --host=0.0.0.0 --port=8000 > app.log 2>&1 &

echo "🚀 Deployment Completed"
ENDSSH

                        rm -f app.tar.gz
                    """
                }
            }
        }
    }

    post {
        success {
            emailext(
                subject: "Build SUCCESS: ${env.JOB_NAME} #${env.BUILD_NUMBER}",
                body: "Your Jenkins build was successful.",
                to: "imran7012@gmail.com"
            )
        }
        failure {
            emailext(
                subject: "Build FAILED: ${env.JOB_NAME} #${env.BUILD_NUMBER}",
                body: "Your Jenkins build failed. Please check the console output: ${env.BUILD_URL}",
                to: "imran7012@gmail.com"
            )
        }
    }
}
