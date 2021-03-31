pipeline{
	agent{
	    node {
		   label "SC-IN01"
		}
	}
	environment{
		IN_CSE_PATH = '/home/opc/IoT-Sense/neomsense/com.neos.node.in-cse'
		MAVEN_BUILD_PATH = '/home/opc/IoT-Sense/neomsense'
		REPO_DIR_NAME = '/home/opc/IoT-Sense'
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
			sh """
			
			if ((`ls -lhrt /home/opc/ | grep -w IoT-Sense | wc -l` == 1)); then
				withCredentials([string(credentialsId: 'IOTSense', variable: 'PW1')]) {
   					 
					dir($REPO_DIR_NAME){
				
					//sh "git pull --branch env.GIT_BRANCH https://IOTSense:\${PW1}@github.com/Scry-Analytics/IoT-Sense"
				}
				else
				dir(/home/opc/){
					sh "git clone --branch env.GIT_BRANCH https://IOTSense:\${PW1}@github.com/Scry-Analytics/IoT-Sense"	
				}
				}
			"""
			     //sh "rm -rf /home/opc/IoT-Sense"
			     //sh "mv IoT-Sense /home/opc/"
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
					sh "mvn clean install -DskipTests=true"
				}
				dir("$MN_CSE_PATH/target/products/mn-cse/linux/gtk/x86_64"){
					
				    sh """
					    if ((`ps -elf | grep 'plugins/org.eclipse.equinox.launcher_1.3.0.v20140415-2008.jar'|wc -l` >= 2)); then
					    		echo "found a running java process going to kill it..."
							kill -9 \$(ps -elf | grep 'plugins/org.eclipse.equinox.launcher_1.3.0.v20140415-2008.jar'| head -n 1| awk -F' ' '{print \$4}')
					    else echo "No Running Java process found so skipping the kill process step..."
					    fi
						 
					  """	
						
					sh "JENKINS_NODE_COOKIE=dontKillMe nohup sh start.sh &"
				}
				sh "pwd"
			}   
		}
		
	}

}
