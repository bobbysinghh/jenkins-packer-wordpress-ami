pipeline{
    agent { 
        label "master"
    }
    parameters {
        string(name: 'ACCESS_KEY', description: 'aws access key of your aws account')
        string(name: 'SECRET_KEY', description: "aws secret key of aws account")
    }
    stages{
        stage("packer-build"){
            steps{
                echo "Build Started"
                git branch: 'main', url: 'https://github.com/Bobby8249/jenkins-packer-wordpress-ami.git'
                sh "export AWS_ACCESS_KEY_ID=${params.ACCESS_KEY}"
                sh "export AWS__SECRET_ACCESS_ID=${params.SECRET_KEY}"
                sh "sudo chmod 600 bobby_devops.pem"
                sh "sudo packer build -force ."
                echo "Build Ended"
            }
            post{
                success{
                    echo "executed successfully"
                }
                failure{
                    echo "execution failed"
                }
            }
        }
    }
}
