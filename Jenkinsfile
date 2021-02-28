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
			 
			    
			    
			    sh "echo 'Directory created successfully'"
			    sh "ls -lhrt"
			
		}	
		}
	}

}
