pipeline {
    agent any
    
    triggers {
        cron('H * * * *')
    }
    
    stages {
        stage('Git Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/Git-Ishan/backup.git'
            }
        }
        
        
        stage('Check Disk Usage') {
            steps {
                script {
                    sh '''
                        chmod +x script1.sh
                        ./script1.sh
                    '''
                }
            }
        }
        
        stage('Process Management') {
            steps {
                script {
                    sh '''
                        chmod +x bullet.sh
                        ./bullet.sh
                    '''
                }
            }
        }
    }
    
    post {
        failure {
            emailext (
                subject: "CRITICAL: Job '${env.JOB_NAME} [${env.BUILD_NUMBER}]'",
                body: """
                    FAILED: Job '${env.JOB_NAME} [${env.BUILD_NUMBER}]':
                    Check console output at '${env.BUILD_URL}'
                    """,
                to: '12veer34raj@gmail.com',
                from: 'jenkins@mail'
            )
        }
    }
}
