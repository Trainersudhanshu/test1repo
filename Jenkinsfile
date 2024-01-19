//This pipeline will pull the code from github and then test it, and everytime it will test in a daynamic docker container slave
pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                echo 'Build.......,,,,,,,.'
                git 'https://github.com/Trainersudhanshu/JenkinsProj.git'
                sh "date"
            }
        }
        stage("Test"){
            steps{
            echo "Testing.."
            echo "Testing was succesfull!"
        }
        }
    }
}
