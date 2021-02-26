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
			sh """
			    echo "Testing the connection"
			    echo "Connected successfully"
			"""
			}
		    }
		}
		stage('Creating directory'){
		
		steps{	
			
		   step{	sh """
			    mkdir test
			    ls -lhrt 
			    echo "Directory created successfully"
			"""
			}
		}	
		}
	}

}
