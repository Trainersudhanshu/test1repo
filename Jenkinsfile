//This pipeline will pull the code from github and then test it, and everytime it will test in a daynamic docker container slave
pipeline {
    agent {
            dockerContainer 'jinny1/jenkinsslave:v1'
        }

    stages {
        stage('Build') {
            steps {
                echo 'Build....'
                git 'https://github.com/Trainersudhanshu/JenkinsProj.git'
                sh "date"
            }
        }
        stage("Test"){
            steps{
            echo "Testing.."
            sh  "python3 -m pip install --upgrade pip"
            sh  "python3 -m pip install flake8 pytest"
            sh  "pip3 install -r requirements.txt"
            sh "pytest test_app.py"
            echo "Testing was succesfull!"
        }
        }
    }
}
