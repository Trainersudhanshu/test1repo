//This pipeline will pull the code from github and then test it, and everytime it will test in a daynamic docker container slave
pipeline {
    agent {label "ec2"}
    stages {
        stage('Build') {
            steps {
                echo 'Build.......,,,,,,,.'
                git 'https://github.com/Trainersudhanshu/test1repo.git'
                sh "date"
            }
        }
        stage("Install"){
            steps{
            echo "Testing.."
            echo "Testing was succesfull!"
            sh "yum install ansible -y"
            sh "wget https://releases.hashicorp.com/terraform/1.6.0/terraform_1.6.0_linux_amd64.zip"
            sh "unzip terraform_1.6.0_linux_amd64.zip"
            sh "mv terraform /usr/local/bin/"
            sh "terraform --version"
            sh "aws configure set aws_access_key_id AKIA2UC27P3FDVF5CKUU"
            sh  "aws configure set aws_secret_access_key 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"
            sh  "terraform init"
            sh "terraform apply --auto-approve"
            
        }
        }
    }
}
