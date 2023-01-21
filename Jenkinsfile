pipeline {
   agent any
   stages {
       stage('Test Code') {
           steps {
               sh '''
               echo "----TEST CODE-----"
               echo "-----------------------"
               resoult=`grep -o -i "MAIN" index.html | wc -l`
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
               sudo mv index.html /usr/share/nginx/html
               '''
          }
      }
   }
}
