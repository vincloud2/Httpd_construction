pipeline {
    agent { label "slave1"}
    
    triggers { 
        pollSCM('* * * * *')
    }    

    stages {
        stage('Clone the project ') {
            steps {
                echo 'clone the project'
                git branch: 'main', url: 'https://github.com/vincloud2/Httpd_construction.git'
            }
        }
        stage('Coping the project') {
            steps {
                echo 'verify the file where it is cloned'
                sh '''pwd'''
                sh '''ls'''
            }
        }
        stage('Deploy to httpd server') {
            steps {
                echo 'coping the file '
                sh '''scp -i /home/ec2-user/key.pem -r /var/jenkins/workspace/html_project_Contruction/* ec2-user@54.169.230.197:/var/www/html'''
            }
        }
        stage('Stage4_dummy') {
            steps {
                echo 'check the deploy'
            }
        }    
    }
}
