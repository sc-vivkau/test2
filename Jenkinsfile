pipeline{
	agent{
	    node {
		   label 'SC-IN01'
		}
	}
	stages {
		stage('Testing'){
		    steps {
			    
			sh "echo 'Testing the connection'"
			sh "echo 'Connected successfully'"
			    
		    }
		}
		stage('git repo and config update'){
		
		steps{	
			dir('/tmp/'){
			    
			    sh "git clone https://github.com/sc-vivkau/test2.git"
			    sh "git pull"
			    sh "ls -lhrt"
			}
			
		}
	   }
		stage('maven build compilation'){
			
			steps{
				
				dir('/home/opc/IoT-Sense/neomsense'){
					sh  "pwd"
					sh "mvn clean install -DskipTests=true"
				}
				sh "pwd"
			}   
		}
		
	}

}
