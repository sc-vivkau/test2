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
		stage('Creating directory'){
		
		steps{	
			 
			    
			    sh "echo 'polling test success'"
			    sh "echo 'Directory created successfully'"
			    sh "ls -lhrt"
			
		}
		}
		stage('maven build compilation'){
			sh "cd /home/opc/IoT-Sense/neomsense"
			sh "mvn clean install -DskipTests=true"
		}
		
	}

}
