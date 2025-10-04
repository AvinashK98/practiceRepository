pipeline{
        agent{
            label{
                label "built-in"
                customWorkspace "/myWsp"
            }

        } 
        stages{
            stage("Updating"){
                steps{
                      sh "yum update -y"      
                }
            }
            stage("Worskspace cleanup"){
                steps{
                      sh "rm -rf /myWsp/*"    
                }
            }

            stage("removing existing httpd"){
                steps{
                      sh "yum remove httpd -y"    
                        
                }
            }

            stage("Installing"){
                steps{
                      sh "yum install httpd -y"      
                }
            }
            
            stage("Starting httpd"){
                steps{
                      sh "systemctl start httpd"      
                }
            }

            stage("Enabling httpd"){
                steps{
                      sh "systemctl enable httpd"      
                }
            }

            stage("Checking status"){
                steps{
                      sh "systemctl status httpd"      
                }
            }

            stage("Creating a sample webpage"){
                steps{
                      sh 'echo "<h1>Deployed via Jenkins</h1>" > index.html'      
                }
            }

            stage("moving index.html to workspace"){
                steps{
                      sh "mv /myWsp/index.html /var/www/html"      
                }
            }
            
            stage("Privide permission"){
                steps{
                    sh "chmod -R 777  /var/www/html"
                }
            }
            }
        }
