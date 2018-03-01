pipeline {
    agent any

    environment {
        AWS_ACCESS_KEY_ID     = credentials('jenkins-aws-secret-key-id')
        AWS_SECRET_ACCESS_KEY = credentials('jenkins-aws-secret-access-key')
        BOT_APIKEY = credentials('chatwork.bot.apikey')
        TEST_ROOM_ID = credentials('chatwork.room.test')
    }

    stages {
        stage('hello1') {
            node {
                steps {
                    echo "Hello Hello"
                }
            }
        }
        stage('notification') {
            node {
                steps {
                    sh "curl -X POST -H 'X-ChatWorkToken: ${BOT_APIKEY}' -d 'body=test' 'https://api.chatwork.com/v2/rooms/${TEST_ROOM_ID}/messages'"
                }
            }
        }
    }
}
