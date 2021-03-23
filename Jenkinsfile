pipeline{
	agent{
	    node {
		   label 'SC-IN01'
		}
	}
	environment{
		IN_CSE_PATH = '/home/opc/IoT-Sense/neomsense/com.neos.node.in-cse'
		MAVEN_BUILD_PATH = '/home/opc/IoT-Sense/neomsense'
		REPO_DIR_NAME = 'test2'
		MN_CSE_PATH = '/home/opc/IoT-Sense/neomsense/com.neos.node.mn-cse'
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
			//sh """
			     //rm -rf $REPO_DIR_NAME
			     //echo 'old git has been removed'
			     git clone https://limited:23fc07744c094e10c605c6954d49668cb77a135f\@github.com/sc-vivkau/testing.git
			     //mv $REPO_DIR_NAME/clouddb.dev.properties  $IN_CSE_PATH/configurations/services/clouddb.dev.properties
			     //mv $REPO_DIR_NAME/cloudnotification.dev.properties  $IN_CSE_PATH/configurations/services/cloudnotification.dev.properties
			     //mv $REPO_DIR_NAME/neos.product  $IN_CSE_PATH/neos.product
			//"""
			
		}
	   }
		stage('maven build compilation and app launch'){
			
			steps{
				
				dir("$MAVEN_BUILD_PATH"){
					sh  "pwd"
					//sh "mvn clean install -DskipTests=true"
				}
				dir("$IN_CSE_PATH/target/products/in-cse/linux/gtk/x86_64"){
					
				    //sh """
					//    if ((`ps -elf | grep 'plugins/org.eclipse.equinox.launcher_1.3.0.v20140415-2008.jar'|wc -l` >= 2)); then
					 //   		echo "found a running java process going to kill it..."
					//		kill -9 \$(ps -elf | grep 'plugins/org.eclipse.equinox.launcher_1.3.0.v20140415-2008.jar'| head -n 1| awk -F' ' '{print \$4}')
					  //  else echo "No Running Java process found so skipping the kill process step..."
					    //fi
						 
					  //"""	
						
					//sh "JENKINS_NODE_COOKIE=dontKillMe nohup sh start.sh &"
				}
				sh "pwd"
			}   
		}
		
	}

}
