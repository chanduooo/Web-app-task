pipeline {
    agent any
    stages {
        
        stage('Build') {
            steps {
                sh 'npm install'
                sh 'npm run build'
            }
        }
        stage('install nginx in remote server') {
            steps {
                sh '''
                  ssh ec2-user@34.211.227.164
                  sudo yum install nginx -y
                  sudo systemctl start nginx
                  sudo systemctl enable nginx
                '''
            }
        }
        stage('Deploy') {
            steps {
                   
                    sh '''

                    scp -o StrictHostKeyChecking=no -r build/* ec2-user@34.211.227.164:/usr/share/nginx/html
                    ssh -o StrictHostKeyChecking=no ec2-user@34.211.227.164 'sudo systemctl restart nginx'
                    '''
                }
            }
        }
    }
