pipeline {
    agent { label 'centos_slave' } 

    stages {
        stage('Clone repo and clean it') {
	timeout(time: 3, unit: 'SECONDS') { // start of timeout
            steps {
			script {
				sh "sudo yum install -y maven"
				}

                echo 'Hello from Git HUB'
                cleanWs()
		   sh "git clone https://github.com/Kapil987/maven_Prac.git"
		   sh "pwd"
		   sh "cd maven_Prac"
		   sh "pwd"
		   sh "mvn -f maven_Prac/pom.xml clean "
                  }//end of steps
					} //end of timeout block 
                       }// stage build end
            
	stage('Test') {
            steps {
                echo 'Hello Test'
		   sh "mvn -f maven_Prac/pom.xml test "
                  }
                       }// stage Test end

	stage('Deploy') {
            steps {
                echo 'Hello Deploy'
		   sh "mvn -f maven_Prac/pom.xml package "
		   sh "pwd"
		   // start of dir 
		   dir("maven_prac") 
		        {
		        sh "pwd"
		        }// end of dir, start dir(folder) and a block after it needs to be written else error
		       
		   }
                       }// stage Deploy end

	}// stages end
}
