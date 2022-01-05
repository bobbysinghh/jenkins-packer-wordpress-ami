pipeline{
    agent { 
        label "master"
    }
    stages{
        stage("packer-build"){
            steps{
                echo "Build Started"
                git branch: 'main', url: 'https://github.com/Bobby8249/jenkins-wordpress-ami.git'
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