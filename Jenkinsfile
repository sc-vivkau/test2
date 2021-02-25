pipeline{
	agent{
	    node {
		   label 'SC-IN01'
		}
	}
	stages {
		stage('Testing'){
		    steps {
			sh """
			    echo "Testing the connection"
			    echo "Connected successfully"
			"""
		    }
		}
		stage('Creating directory'){
			sh """
			    mkdir test
			    ls -lhrt 
			    echo "Directory created successfully"
			"""
		}
	}

}
