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
            //sh "aws configure set aws_access_key_id "
            //sh  "aws configure set aws_secret_access_key "
            sh  "terraform init"
            sh "terraform apply --auto-approve"
            sh "sleep 30"
            sh "chmod 400 mykey"
            sh "ansible-playbook httpdconfigure.yml"
            sh "curl -LO https://storage.googleapis.com/minikube/releases/latest/minikube-latest.x86_64.rpm"
            sh "rpm -Uvh minikube-latest.x86_64.rpm"
            sh "minikube start --force"
            sh "curl -O https://s3.us-west-2.amazonaws.com/amazon-eks/1.28.3/2023-11-14/bin/linux/amd64/kubectl"
            sh "chmod +x ./kubectl"
            sh "cp ./kubectl /usr/bin/"
            sh "kubect get pods"

            
        }
        }
    }
}
