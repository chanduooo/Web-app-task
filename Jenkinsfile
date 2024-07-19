ipeline {
    agent any
    tools {
        nodejs 'node'
    }

    stages {
        stage("npm test") {
            steps {
                sh 'npm  install'
                sh 'npm run test'
                }
        }
        stage("npm build") {
            steps {
                sh 'npm run build'
                }
        }
        stage("nginx installation") {
            steps {
                sh '''
                    sudo yum install nginx -y
                    sudo systemctl start nginx
                    sudo systemctl enable nginx
                    '''
                }
        }
        stage("Copy build") {
            steps {
                sh '''
                sudo cp -r build /usr/share/nginx/html
                sudo systemctl restart nginx                
                ''' 
                }
        }
   }
}
