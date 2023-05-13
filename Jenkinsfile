pipeline{
    agent any
    environment{
        DOCKERHUB_CREDENTIALS=credentials('dockerhub')
    }
    stages {
        
        stage('gitclone'){
            steps{
                git 'https://github.com/yannhunter/nodeapp_test.git'
            }
        }
        
        stage('build'){
            steps{
                sh 'docker build -t gunhunter21/nodeapp_test:latest .'
            }
        }
        
        stage('login'){
            steps{
                sh 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'                		
            	echo 'Login Completed' 
            }
        }
        
        stage('push'){
            steps{
                sh 'docker push gunhunter21/nodeapp_test:latest'
            }
        }
    }
    
    post{
        always{
            sh 'docker logout'
        }
    }
}
