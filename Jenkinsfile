#!/usr/bin/env groovy

import groovy.json.JsonOutput

//def slackNotificationChannel = '[CHANNEL_NAME]'     // ex: = "builds"
def slackNotificationChannel = '[builds]'

def notifySlack(text, channel, attachments) {
    //def slackURL = '[SLACK_WEBHOOK_URL]'
    def slackURL = '[https://hooks.slack.com/services/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]'

    def jenkinsIcon = 'https://wiki.jenkins-ci.org/download/attachments/2916393/logo.png'

    def payload = JsonOutput.toJson([text: text,
        channel: channel,
        username: "Jenkins",
        icon_url: jenkinsIcon,
        attachments: attachments
    ])

    sh "curl -X POST --data-urlencode \'payload=${payload}\' ${slackURL}"
}

node {
    stage("Post to Slack") {
        notifySlack("Success!", slackNotificationChannel, [])
    }
}