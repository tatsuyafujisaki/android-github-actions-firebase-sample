# GitHub Actions YAML
[.github/workflows/android.yml](.github/workflows/android.yml)

# Preparation
## for Firebase Test Lab
1. Create a service account with an Editor role at https://console.developers.google.com/iam-admin/serviceaccounts (as written in https://firebase.google.com/docs/test-lab/android/continuous)
2. Download a private key for the service account as JSON.
3. Encode it in Base64.
```shell
cat <private-key>.json | base64 | pbcopy
```
4. Add the encoded string to GitHub Secrets as `GOOGLE_SERVICES_JSON_BASE64`.

## for Firebase App Distribution
1. Copy your Firebase app ID from Firebase Console, and add it to GitHub Secrets as `FIREBASE_APP_ID`.
2. Install Firebase CLI on your computer.
3. Run `firebase login:ci` on console of your computer, and a token will be printed.
4. Add the token to GitHub Secrets `FIREBASE_TOKEN`.

## for Slack
1. Go to https://slack.com/apps/A0F7XDUAZ-incoming-webhooks
2. Add Incoming Webhooks
3. `Integration Settings` > `Post to Channel` > (select a channel)
4. Copy `Webhook URL`
5. Paste it in GitHub Secrets. I name it `SLACK_WEBHOOK_URL`.

# Appendix (optional)
## How to use `google-services.json` in a public repository.
1. Download `google-services.json` from Firebase Console.
2. Copy the content to GitHub Secrets without encoding it in Base64. I name it `GOOGLE_SERVICES_JSON`.
3. Add the following to your workflow.
```yaml
- run: echo $GOOGLE_SERVICES_JSON > app/google-services.json
  env:
    GOOGLE_SERVICES_JSON: ${{ secrets.GOOGLE_SERVICES_JSON }}
```
