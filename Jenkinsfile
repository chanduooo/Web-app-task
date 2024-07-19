pipeline {
    agent any

    stages {
        stage("npm test") {
            steps {
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
                cp -r build /usr/share/nginx/html
                sudo systemctl restart nginx                
                ''' 
                }
        }
   }
}
