pipeline {
		agent {
		node {
			label ('172.31.4.90')
		}
		}

		stages {
		stage ('install-git-docker') {
		steps {
	
			sh "sudo yum install docker -y"
			sh "sudo systemctl start docker"
			sh "sudo yum install git -y"
			sh "sudo chmod -R 777 /mnt"
		
	}
	}
			stage ('install-docker-compose') {
		steps {
	
			sh "sudo curl -SL https://github.com/docker/compose/releases/download/v2.11.0/docker-compose-linux-x86_64 -o /usr/local/bin/docker-compose"
			sh "sudo chmod +x /usr/local/bin/docker-compose"
			sh "sudo ln -s /usr/local/bin/docker-compose /usr/bin/docker-compose"
			sh "sudo chmod +x /usr/bin/docker-compose"
		
	}
	}
			
		stage ('gitrepo-copy') {
		steps {
		dir ('/mnt/repo') {
			sh "sudo rm -rf *"
			sh "sudo git clone https://github.com/ronitunale/docker4.git"
			sh "sudo chmod -R 777 /mnt"
			
			
			
	}
	}
	}
			
			
			stage ('war-copy') {
		steps {
		dir ('/mnt/wars') {
		
			sh "sudo chmod -R 777 /mnt"
			sh "sudo cp /mnt/repo/docker4/gameoflife.war /mnt/wars"
			
		}
		}	
		}
	
		stage ('Deploy-tomcat-on-docker') {
		steps {
		dir ('/mnt/yaml') {
			sh "sudo cp /mnt/repo/docker4/docker-compose.yaml /mnt/yaml"
			sh "sudo docker-compose up -d"
				
	}
	}
	}
		
			

	}
	}
