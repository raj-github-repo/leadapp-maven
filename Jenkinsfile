pipeline {
    agent {
        node {
              label 'linux-node'
              customWorkspace '/home/ec2-user/cust_ws'
        }
    }
   stages{
       stage( 'cleaning cust ws')
            {
                steps{
                    sh 'pwd'
                    sh 'rm -rf *'
                    echo 'cust ws cleaned successfully'
                }
            
            }
         stage('....test...')
         { 
            steps{
                sh "mvn test"
                 echo 'tested successfully'
            }
         }
       stage('....package...')
       {
           steps{
               sh "mvn package"
               echo 'packaged successfully'
           }
       }
            
        stage('copying war file from cust ws to tomcat webapps')
            {
                steps{
                    sh 'cp /home/ec2-user/cust_ws/target/leadapp.war /home/ec2-user/apache-tomcat-9.0.79/webapps'
                    echo 'war file successfully deployed to tomcat'
                }
            }
       }
       
    }
