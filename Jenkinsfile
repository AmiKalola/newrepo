pipeline {
    agent any
    stages{
        stage("try"){
            steps{
            echo "hello"
            }
        }
    }
    stages {
        stage('deploy') {
            steps {
              sh "aws configure set region $AWS_REGION" 
              sh "aws configure set aws_access_key_id $AWS_ACCESS_KEY_ID"  
              sh "aws configure set aws_secret_access_key $AWS_SECRET_ACCESS_KEY"
              sh "aws s3 cp index.html s3://$AWS_BUCKET"
              sh "aws cloudfront create-invalidation --distribution-id $CLOUDFRONT_ID --paths '/*'"

            }
        }
    }
}
