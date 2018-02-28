node {
    environment {
        AWS_ACCESS_KEY_ID     = credentials('jenkins-aws-secret-key-id')
        AWS_SECRET_ACCESS_KEY = credentials('jenkins-aws-secret-access-key')
    }

    stage 'hello1'
    echo "Hello ${AWS_ACCESS_KEY_ID}"
    
    stage 'hello2'
    echo 'Hello World2'
    
    stage 'hello3'
    echo 'Hello World3'
}
