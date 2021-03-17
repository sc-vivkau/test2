pipeline{
	agent{
	    node {
		   label 'SC-IN01'
		}
	}
	environment{
		IN_CSE_PATH = '/home/opc/IoT-Sense/neomsense/com.neos.node.in-cse'
		MAVEN_BUILD_PATH = '/home/opc/IoT-Sense/neomsense'
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
			
			    sh "echo 'Entered in /home/opc directory'"
			    sh "rm -rf test2"
			    sh "echo 'old git has been removed'"
			    sh "git clone https://github.com/sc-vivkau/test2.git"
			    sh "mv test2/clouddb.dev.properties  $IN_CSE_PATH/configurations/services/clouddb.dev.properties"
			    sh "mv test2/cloudnotification.dev.properties  $IN_CSE_PATH/configurations/services/cloudnotification.dev.properties"
			    sh "mv test2/neos.product  $IN_CSE_PATH/neos.product"
			    sh "ls -lhrt"
			
			
		}
	   }
		stage('maven build compilation and app launch'){
			
			steps{
				
				dir("$MAVEN_BUILD_PATH"){
					sh  "pwd"
					sh "mvn clean install -DskipTests=true"
				}
				dir("$IN_CSE_PATH/target/products/in-cse/linux/gtk/x86_64"){
					//sh "ps -elf | grep start.sh | awk -F' ' '{system('kill -9 '$4)}'"
					sh "ID = ps -elf | grep start.sh | awk -F' ' '{print \\$4}'| head -n 1d"
					sh "kill -9 $ID"
					sh "JENKINS_NODE_COOKIE=dontKillMe nohup sh start.sh &"
				}
				sh "pwd"
			}   
		}
		
	}

}
