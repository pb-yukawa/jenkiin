#!/usr/bin/env groovy
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
                    try {
                        echo "Hello Hello ${dev1}"
                    } catch(e) {
                        sendChatwork('failure')
                    } finally {
                        // cleaning
                    }
                }
            }
        }
        stage('php') {
            steps {
                sh "composer install"
                sh "echo '<?php echo 123;' | php"
            }
        }
        stage('notification') {
            steps {
                sendChatwork('success')
            }
        }
    }
}

def sendChatwork(message) {
    sh "curl -X POST -H \"X-ChatWorkToken: ${BOT_APIKEY}\" -d \"body=test${KEY1} ${env.JOB_NAME} ${env.BUILD_NUMBER} (${env.BUILD_URL}): ${message}\" \"https://api.chatwork.com/v2/rooms/${TEST_ROOM_ID}/messages\""
}