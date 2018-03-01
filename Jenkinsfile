pipeline {
    agent any

    environment {
        AWS_ACCESS_KEY_ID     = credentials('jenkins-aws-secret-key-id')
        AWS_SECRET_ACCESS_KEY = credentials('jenkins-aws-secret-access-key')
        BOT_APIKEY = credentials('chatwork.bot.apikey')
        TEST_ROOM_ID = credentials('chatwork.room.test')
        KEY1 = credentials("${buildenv}.key1")
    }

    stages {
        stage('hello1') {
            steps {
                script {
                    echo "Hello Hello ${dev1} ${Environment}"
                } catch(e) {
                    sh "curl -X POST -H \"X-ChatWorkToken: ${BOT_APIKEY}\" -d \"body=FAILURE!!! test${KEY1} ${JOB_NAME} ${BUILD_NUMBER} (${BUILD_URL})\" \"https://api.chatwork.com/v2/rooms/${TEST_ROOM_ID}/messages\""
                } finally {
                    // cleaning
                }
            }
        }
        stage('docker run') {
            steps {
                docker.image('openjdk:8u131-jdk').inside() {
                    sh 'java -version'
                }
            }
        }
        stage('notification') {
            steps {
                sh "curl -X POST -H \"X-ChatWorkToken: ${BOT_APIKEY}\" -d \"body=test${KEY1} ${JOB_NAME} ${BUILD_NUMBER} (${BUILD_URL})\" \"https://api.chatwork.com/v2/rooms/${TEST_ROOM_ID}/messages\""
            }
        }
    }
}
