pipeline {
    agent any
    tools {
	nodejs 'node'
	}

    stages {
        stage("npm build") {
            steps {
                sh '''
		npm install	
		npm run build
		'''
                }
        }
        stage("npm test") {
            steps {
                sh 'npm test'
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
