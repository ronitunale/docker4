pipeline {
		agent {
		node {
			label ('built-in')
		}
		}

		stages {
		stage ('install-git-docker') {
		steps {
	
			sh "yum install docker -y"
			sh "systemctl start docker"
			sh "chmod -R 777 /mnt"
		
	}
	}
			
			
		stage ('gitrepo-copy') {
		steps {
		dir ('/mnt/repo') {
			sh "rm -rf *"
			sh "git clone https://github.com/ronitunale/docker3.git"
			sh "chmod -R 777 /mnt"
			sh "cp /mnt/repo/docker3/docker-compose.yaml /mnt"
			
			
	}
	}
	}
			stage ('war-copy') {
		steps {
		dir ('/mnt') {
			sh "mkdir wars"
			sh "chmod -R 777 /mnt"
			sh "cp /mnt/repo/docker3/gameoflife.war /mnt/wars"
			
		}
		}	
		}
	
		stage ('Deploy-tomcat-on-docker') {
		steps {
		dir ('/mnt') {
			sh "docker-compose up -d"
				
	}
	}
	}
		
			

	}
	}
