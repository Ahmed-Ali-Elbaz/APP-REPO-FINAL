pipeline {
    agent {label "slave"}

    stages {

        // CI Stage
        stage('Build an image from helloworld app') {
            steps {

 
                    withCredentials([usernamePassword(credentialsId: 'dockerhub', usernameVariable: 'USERNAME', passwordVariable: 'PASSWORD')]) { 
                    
                    sh """
                        
                        docker build .  -t ahmedhedihed/helloworld:$BUILD_NUMBER
                        docker login -u ${USERNAME} -p ${PASSWORD}
                        docker push ahmedhedihed/helloworld:$BUILD_NUMBER
                        
                    """
                    
                    }

            }



        }


        // CD Stage
        stage('Deploy app on GKE cluster') {
            steps {

        //           
                withCredentials([file(credentialsId: 'cluster', variable: 'serviceAcc')]){

                    sh """

                            gcloud auth activate-service-account --key-file="$serviceAcc"
                            gcloud container clusters get-credentials private-cluster --zone us-central1-a --project wired-sol-367809
                            sed -i 's/tagversion/${env.BUILD_NUMBER}/g' Deployment/app.yaml
                            kubectl apply  -f Deployment

                       """

                        
                    
                }
                    
            }     

            
        }     

    }

    // Slack Notifications
        post {

            failure {

                slackSend (channel:"helloworldapp", color:"#FF0000", message:"FAILD: Job '${env.JOB_NAME} [${env.BUILD_NUMBER}]' (${env.BUILD_URL})")
            }

            success {

                slackSend (channel:"helloworldapp", color:"#00FF00", message:"SUCCEEDED: Job '${env.JOB_NAME} [${env.BUILD_NUMBER}]' (${env.BUILD_URL})")

            }

        }  



}
