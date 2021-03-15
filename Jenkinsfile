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
			dir('/tmp'){
			    sh "rm -rf test2"
			    sh "git clone https://github.com/sc-vivkau/test2.git"
			    sh "mv /tmp/test2/clouddb.dev.properties  /home/opc/IoT-Sense/neomsense/com.neos.node.in-cse/configurations/services/clouddb.dev.properties"
			    sh "mv /tmp/test2/cloudnotification.dev.properties  /home/opc/IoT-Sense/neomsense/com.neos.node.in-cse/configurations/services/cloudnotification.dev.properties"
			    sh "mv /tmp/test2/neos.product  /home/opc/IoT-Sense/neomsense/com.neos.node.in-cse/neos.product"
			    sh "ls -lhrt"
			}
			
		}
	   }
		stage('maven build compilation and app launch'){
			
			steps{
				
				dir('/home/opc/IoT-Sense/neomsense'){
					sh  "pwd"
					sh "mvn clean install -DskipTests=true"
				}
				dir('/home/opc/IoT-Sense/neomsense/com.neos.node.in-cse/target/products/in-cse/linux/gtk/x86_64/'){
					sh "sh start.sh"
				}
				sh "pwd"
			}   
		}
		
	}

}
