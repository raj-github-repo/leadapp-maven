pipeline {
    agent {
        node {
              label 'linux-node'
              customWorkspace '/home/ec2-user/cust_ws'
        }
    }
   stages{
       stage( '....clean....')
            {
              tools {
		maven 'maven_3.9.4'
	      }

              steps{
                    sh 'pwd'
                    sh "mvn clean"
                    
                }
             }
         stage('....test...')
         { 
            tools {
				maven 'maven_3.9.4'
			}

             steps{
                sh "mvn test"
                 echo 'tested successfully'
            }
         }
       stage('....package...')
       {
          tools {
				maven 'maven_3.9.4'
			}

           steps{
               sh "mvn package"
               echo 'packaged successfully'
           }
       }
            
        stage('copying war file from cust ws to tomcat webapps')
            {
                steps{
                    sh 'scp /home/ec2-user/cust_ws/target/leadapp.war ec2-user@15.206.124.160:/home/ec2-user/apache-tomcat-9.0.79/webapps'
                    echo 'war file successfully deployed to tomcat'
                }
            }
       }
       
    }
