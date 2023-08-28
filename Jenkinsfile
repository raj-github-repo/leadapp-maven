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
                    echo 'pwd'
                    sh 'rm -rf *'
                    echo 'cust ws cleaned successfully'
                }
                
            }
            stage('copying war file from cust ws to jenkins workspace')
            {
                steps{
                    sh 'cp /home/ec2-user/jenkins-remote-dir/workspace/leadapp-maven/target/leadapp.war /home/ec2-user/jenkins-remote-dir/workspace/third_pipeline'
                    echo 'war file copied successfully to preset ws of third_pipeline'
                }
            }
       }
       
    }
