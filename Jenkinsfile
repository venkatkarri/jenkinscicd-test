
pipeline { 
  agent any 
environment { 
  Version='$BUILD_NUMBER' 
}
  stages { 
    stage('aws configure') { 
     steps{ 
     withCredentials([aws( 
// $class: 'AmazonWebServicesCredentialsBinding', 
accessKeyVariable: 'AWS_ACCESS_KEY_ID', 
credentialsId: 'aws_siddu', 
secretKeyVariable: 'AWS_SECRET_ACCESS_KEY')]) {
    // some block
       sh '''aws ecr get-login-password --region eu-north-1 | docker login --username AWS --password-stdin 590183680362.dkr.ecr.eu-north-1.amazonaws.com'''
}
     
}  
      
}
    
    stage('1st') { 
     steps{ 
       sh '''docker tag kvsvenkat/tfapps-portal-febe:1.1.1 590183680362.dkr.ecr.eu-north-1.amazonaws.com/dockertestrepo:$Version''' 
       sh '''docker push 590183680362.dkr.ecr.eu-north-1.amazonaws.com/dockertestrepo:$Version'''

}

}

}

}
