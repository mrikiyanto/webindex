pipeline {
    agent any 
    stages {
        stage('Clone the repo') {
            steps {
				echo 'clone the repo'
				sh 'rm -rf webindex'
				sh 'git clone https://github.com/mrikiyanto/webindex.git'
            }
        }
        stage('Push repo to remote host') {
            steps {
				echo 'connect to host and pull down latest version' 
				sh 'rsync -avzyhe "ssh -i ~/riki.pem" ~/workspace/web-test/webindex/ root@172.16.0.17:/var/www/mry.com'
            }
        }
        stage('Check website is up') {
            steps {
				echo 'check website is up' 
				sh 'curl -is 172.16.0.20 | head -n 1'
	        }
        }
    }
}
