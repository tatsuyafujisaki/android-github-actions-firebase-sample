# GitHub Actions workflow for Android
[.github/workflows/android.yml](.github/workflows/android.yml)

# What this workflow demonstrates
1. Build
2. Unit testing
3. Instrumented testing
4. Slack notification

# Prerequisites
## Add Incoming Webhooks on slack.com
1. Go to https://slack.com/apps/A0F7XDUAZ-incoming-webhooks
2. Add Incoming Webhooks
3. `Integration Settings` > `Post to Channel` > (select a channel)
4. Copy `Webhook URL`

## Add a secret for Slack Incoming Webhooks on github.com
1. Go to the Secrets page of your GitHub repository (i.e. https://github.com/{your-username}/{your-repository-name}/settings/secrets)
2. Add a secret whose name is `SLACK_WEBHOOK_URL` and value is the Webhook URL copied from slack.com
