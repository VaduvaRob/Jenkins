pipeline{
    agent any
    stages{
        stage('Build'){
        steps {
            echo "hi"
            sh 'sudo yum update'
            sh 'sudo yum install -y httpd' 
            }
        }
        stage('Site creation'){
        parallel { 
            stage('Start httpd'){
            steps{
                sh 'sudo systemctl start httpd'
                sh 'sudo systemctl enable httpd'
            }    
            }
            stage('Create html'){
            steps { 
                sh 'sudo chmod 333 /var/www/html'
                sh 'sudo echo "<html><head><title>Web App</title></head><body><h1>" This is your newly created webserver using jenkins "</h1></body></html>" > /var/www/html/index.html'
            }
            }
        }
        }
         stage('Check'){
        steps {
            sh 'curl localhost:8080' 
        }
        }
    }
}
