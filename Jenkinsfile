pipeline {
   agent any
   stages {
       stage('Test Code') {
           steps {
               echo "This test is running ${env.BUILD_ID} on ${env.JENKINS_URL}"
               sh '''
               echo "----TEST CODE-----"
               echo "-----------------------"
               resoult=`grep -o -i "DEVELOP" index.html | wc -l`
               if [ "$resoult" = "1" ]
               then
                 echo "Test PASSED"
               else
                 echo "Test FAILED"
                 exit 1
               fi
               '''
           }
       }
      stage('Deploy Code') {
          steps {
               sh '''
               echo "Deploying Code"
               echo "-------------"
               mv index.html /usr/share/nginx/html
               '''
          }
      }
      stage ('Notification on Telegram') {
         steps {
            telegramSend 'Deploy on branch DEV was SUCCESS'
            
         }
      }
   }
}
