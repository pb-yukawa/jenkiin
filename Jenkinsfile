pipeline {
    agent any

    environment {
        AWS_ACCESS_KEY_ID     = credentials('jenkins-aws-secret-key-id')
        AWS_SECRET_ACCESS_KEY = credentials('jenkins-aws-secret-access-key')
        BOT_APIKEY = credentials('chatwork.bot.apikey')
        TEST_ROOM_ID = credentials('chatwork.room.test')
        KEY1 = credentials("${env}.key1")
    }

    stages {
        stage('hello1') {
             steps {
                echo "Hello Hello ${dev1} ${Environment}"
            }
        }
        stage('notification') {
            steps {
                sh "curl -X POST -H \"X-ChatWorkToken: ${BOT_APIKEY}\" -d \"body=test${KEY1}\" \"https://api.chatwork.com/v2/rooms/${TEST_ROOM_ID}/messages\""
            }
        }
    }
}
