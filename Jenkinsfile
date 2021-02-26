pipeline{
	agent{
	    node {
		   label 'SC-IN01'
		}
	}
	stages {
		stage('Testing'){
		    steps {
			step{
			sh echo "Testing the connection"
			sh echo "Connected successfully"
			}
		    }
		}
		stage('Creating directory'){
		
		steps{	
			
		   step{
			    sh mkdir test
			    sh ls -lhrt 
			    sh echo "Directory created successfully"
			
			}
		}	
		}
	}

}
