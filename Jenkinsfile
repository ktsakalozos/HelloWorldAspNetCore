pipeline {
  agent any
  stages {
    stage('Install kubectl') {
      steps {
        sh '''echo "Installing kubectl"
sudo snap install kubectl --classic'''
      }
    }
    stage('Install dotnet') {
      steps {
        sh '''echo "Installing dotnet"
curl https://packages.microsoft.com/keys/microsoft.asc | gpg --dearmor > microsoft.gpg 
sudo mv microsoft.gpg /etc/apt/trusted.gpg.d/microsoft.gpg
sudo sh -c \'echo "deb [arch=amd64] https://packages.microsoft.com/repos/microsoft-ubuntu-xenial-prod xenial main" > /etc/apt/sources.list.d/dotnetdev.list\'
sudo apt-get install apt-transport-https -y 
sudo apt-get update
sudo apt-get install dotnet-sdk-2.1.4 -y'''
      }
    }
    stage('Install docker') {
      steps {
        sh '''echo "Installing docker"
sudo apt-get install \\
    apt-transport-https \\
    ca-certificates \\
    curl \\
    software-properties-common -y
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
sudo add-apt-repository \\
   "deb [arch=amd64] https://download.docker.com/linux/ubuntu \\
   $(lsb_release -cs) \\
   stable"
sudo apt-get update
sudo apt-get install docker-ce -y'''
      }
    }
  }
}