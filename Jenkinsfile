pipeline{
  agent any
  stages{
   stage('fetch from repo'){
    steps{
      git branch: 'master', url: 'https://github.com/c2-80511/SunProject.git'
     }
   }

   stage('build image'){
     steps{
      sh 'whoami'
      sh '/usr/bin/docker image build -t prasadthombare/hackathon2 .'
     }
   } 
   
   stage('docker login'){
     steps{
       
       sh 'echo dckr_pat_CHPu1ilNJ-p1MFZJucnCfF_nOEA | /usr/bin/docker login -u prasadthombare --password-stdin'
       }
     }

    stage('push image'){
          steps{
          sh '/usr/bin/docker  image push prasadthombare/hackathon2'
            }   

          } 

    stage('remove container'){
      steps{
      sh ' /usr/bin/docker container rm --force hackathon'
         }
      }
    stage('start container'){
        steps{ 
       
         sh '/usr/bin/docker container run -itd --name hackathon -p 9876:80 prasadthombare/hackathon2'
           }


       }
  
 }
}
